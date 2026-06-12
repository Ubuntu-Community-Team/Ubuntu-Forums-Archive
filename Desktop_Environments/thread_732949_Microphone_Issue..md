---
title: "Microphone Issue."
date: 2008-03-23
forum: Desktop Environments
---

### Post by micproblem112 on 2008-03-23
Some time ago (Not quite sure how long - many changes have taken place since I last attempted to use Teamspeak), my microphone seems to have stopped working. This has been verified via multiple applications.

The strange thing is, I'm able to record audio files by reading directly from /dev/audio, though, no other programs seem to be able to access the microphone. Command used to read from /dev/audio is as follows:
dd bs=8k count=5 < /dev/audio > strange.au

amixer output:
```
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 150 [59%]
  Front Right: Playback 185 [73%]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [on]
  Front Right: Playback 64 [100%] [on]
Simple mixer control 'Front Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [on]
  Front Right: Playback 0 [0%] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [on]
  Front Right: Playback 0 [0%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 0 [0%] [off]
  Front Right: Playback 0 [0%] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 0 [0%] [off]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [on]
  Front Right: Playback 0 [0%] [on]
Simple mixer control 'CD',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 47 [72%] [on]
  Front Right: Playback 47 [72%] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 31 [48%] [on]
  Front Right: Playback 31 [48%] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 31 [89%] [on]
  Front Right: Capture 31 [89%] [on]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 31 [89%] [on]
  Front Right: Capture 31 [89%] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 35
  Front Left: Capture 31 [89%] [on]
  Front Right: Capture 31 [89%] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%]
  Front Right: Capture 120 [100%]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'Front Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'Front Line' 'CD'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line' 'Front Line' 'CD'
  Item0: 'Mic'

```

Not quite sure what the issue is. I'm using ALSA for audio, KDE for WM, and haven't had an issue before this.
The microphone is a headset type microphone, which is plugged in to my soundcard.

Any help would be appreciated.

---

### Post by micproblem112 on 2008-03-23
I seem to have posted this on the wrong forum. Could a Mod move this to Multimedia & Video?

---

### Post by micproblem112 on 2008-03-24
Hrm. The issue seems to have mysteriously solved itself with a reboot (Hate having to reboot.Not sure why this helped - had tried restarting alsa already). Oh well, Thanks anyways.

---

