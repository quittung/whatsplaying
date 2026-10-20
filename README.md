# whatsplaying

My Pixel Buds wouldn't switch from my Linux PC to my phone. Turns out a Firefox tab was keeping an audio stream open, even though I couldn't hear anything.

This is a small command to see which apps are using audio, where it's going, and the tab or media title when available. It also shows microphone use and whether streams are running or idle, so you can find the thing to pause or close.

Maybe it helps someone else with the same annoyance.

## Install

Needs Python 3 and PipeWire's `pw-dump`. No Python packages to install.

```sh
git clone https://github.com/quittung/whatsplaying.git
cd whatsplaying
mkdir -p ~/.local/bin
install -m 755 whatsplaying ~/.local/bin/whatsplaying
```

Make sure `~/.local/bin` is in your `PATH`, then run:

```sh
whatsplaying
```

Example output (shortened):

```text
Playback
  [running] Firefox (PID 12345)
    Some video / X
    to: Pixel Buds Pro 2
  [idle] speech-dispatcher-dummy (PID 12346)
    to: Pixel Buds Pro 2
```

For live updates: `watch -n 1 whatsplaying`. For JSON: `whatsplaying --json`.

It only reads audio status. A running stream can still be silent; this helps find what's holding it open, rather than measuring whether you can hear it. It doesn't pause apps or change audio settings.
