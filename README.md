# Tablet UI

A tiny root-powered Quick Settings tile for Android that flips your phone between its normal layout and a tablet-style layout with one tap.

## What it does

Tablet UI adds a single tile to your Quick Settings panel. Tap it and the display density changes so apps and the system UI switch to their larger, tablet-style layouts. Tap it again and everything returns to normal. The tile shows as active while tablet mode is on.

| Mode | Density | Smallest width |
| --- | --- | --- |
| Normal | 432 dpi | about 400dp |
| Tablet | 265 dpi | about 652dp |

These values are tuned for a 1080 px wide screen. Smallest width in dp = screen width in px x 160 / dpi.

## Features

- One-tap toggle from Quick Settings
- Tile state always matches the real screen layout, even after a reboot
- Hide the launcher icon from inside the app, and reopen it any time by long-pressing the tile
- No background service, no network access, no ads, no analytics
- Tiny download, well under 10 KB

## How it works

The tile is an Android `TileService`. When tapped, it runs `wm density <value>` through `su`, which is the same command you would type in a root terminal. It decides whether tablet mode is on by reading the current smallest screen width, so it never gets out of sync.

## Requirements

- Android 8.0 or newer
- Root access (developed and tested with KernelSU)

## Permissions

The app asks for no Android permissions. It only needs a root grant from your root manager, and only uses it to run the density command.

## Downloads

Every build is published automatically on the [Releases](../../releases) page as `TabletUI.apk`. Builds are signed with a fixed key, so new releases update over old ones.

## Troubleshooting

If the screen ever looks wrong, restore the default density with:

```
su -c "wm density reset"
```

## Project info

- Package: `com.waguri.tablettile`
- Built with plain Java and Gradle, compiled by GitHub Actions
- Author: [waguri-paglu](https://github.com/waguri-paglu)
