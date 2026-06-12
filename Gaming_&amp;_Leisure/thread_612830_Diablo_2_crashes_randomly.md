---
title: "Diablo 2 crashes randomly"
date: 2007-11-14
forum: Gaming &amp; Leisure
---

### Post by donovanh on 2007-11-14
Hi,

I installed Diablo 2 with WINE a few weeks ago, and it's been running very nicely. Except in the last couple of days it has been randomly throwing me back to the desktop. This is what I get in the terminal:

```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on ATI IXP Modem, disabling mixer
err:ntdll:RtlpWaitForCriticalSection section 0x7bc8e7a4 "loader.c: loader_section" wait timed out in thread 000a, blocked by 0009, retrying (60 sec)
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
X connection to :1.0 broken (explicit kill or server shutdown).

```

Any idea what's causing this?

---

### Post by disturbedite on 2007-11-14
looks like it may be a driver problem.  it appears you have an ati card, give more details on this including what driver you have installed.

---

