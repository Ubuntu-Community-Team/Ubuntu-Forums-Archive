---
title: "Wine + ALSA = No wub?"
date: 2005-06-06
forum: Gaming &amp; Leisure
---

### Post by DarkKnight on 2005-06-06
I'm trying to get my sound in wine working with ALSA but I'm not having much luck. 

If I disable the sound(set it to oss), everything runs smooth as, but as soon as, just no sound. When I enable the ALSA drivers, I get this error message just before the xserver locks up and stops responding.

```
ALSA lib pcm_dmix.c:812:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
err:wave:ALSA_WaveInit open pcm: Invalid argument
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c921d0)->(00010022,00000011)
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c921d0)->(00010022,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:mmtime:timeBeginPeriod Stub; we set our timer resolution at minimum
fixme:mmtime:timeEndPeriod Stub; we set our timer resolution at minimum
err:ntdll:RtlpWaitForCriticalSection section 0x777e0940 "../../windows/user.c: USER_SysLevel" wait timed out in thread 000e, blocked by 000d, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x77efb6e0 "loader.c: loader_section" wait timed out in thread 0009, blocked by 000e, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x77efb6e0 "loader.c: loader_section" wait timed out in thread 000d, blocked by 000e, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x77efb6e0 "loader.c: loader_section" wait timed out in thread 000a, blocked by 000e, retrying (60 sec)

```

Anyone here had this problem or gotten wine working with ALSA?

---

### Post by DarkKnight on 2005-06-07
*bump*

Anyone? 

The game hangs when set to alsa drivers, I got it working under OSS, but with no software mixing... 

I've setup ALSA correctly, software mixing is working, I've apt'd libwine-alsa and still no go...

I want starcraft with background music... :'(

---

### Post by DarkKnight on 2005-06-08
*THUMP*

If any one has ALSA working with wine, please respond. :( 

I have tried ESD, ALSA and OSS. 

OSS works fine, but it doesn't have software mixing, so it kinda defeats the point. 

I've tried runnign aoss, but that does nothing either...

---

### Post by DarkKnight on 2005-06-12
Well, thanks to the over whelming responce, I was able to get it working.
ALSA needed midi support, so I setup timidity. 

Although the sound quality is rather choppy and it plays some sounds faster then others... any idea's on this?

---

### Post by JamesRock on 2005-07-23
Thanks DarkKnight this helped me a lot ;)

---

### Post by strikeforce on 2005-07-23
My understanding is that its very buggy

---

### Post by zek725 on 2006-11-04
I've installed Wine from the official Edgy repository.

```
sudo aptitude install wine
```

Installation went fine. However, clicking the AUDIO tab in winecfg returns this error.

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/zek/.kde/socket-warrior2.
can't create mcop directory
```

Edit:
> **Eliseo said:**
> Found the solution here!:
[http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f](http://groups.google.nl/group/comp.emulators.ms-windows.wine/browse_thread/thread/4e0e59c7bb6c6410/2298146dcf72d61f)

I just had to do this:
```
mkdir -pv $HOME/.kde/socket-$HOSTNAME 
```

And voila! No more crashing!

IT WORKED! No longer crashes but terminal outputs these lines:

```
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
/bin/sh: /usr/bin/esd: not found
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

```

**winecfg** tells me that there are no audio drivers installed/found in registry. It chose for me OSS. I think ALSA is more stable?

---

### Post by intuited on 2010-03-13
Not sure how useful this is.  I'm not actually using sound under wine, I just didn't like the error message.  Meaning that I'm not really set up to test this out.  Anyway, after installing timidity I was still getting the message.

I managed to make the message disappear by loading the sequencer kernel module:
$ sudo modprobe snd-seq

Note that even in the case where this is useful, you'll have to add that kernel module to the list of those loaded on boot.  I don't recall offhand how to do that, there's a file in /etc somewhere... perhaps obviously.  Otherwise you will have to run that command every time you boot.

I'm currently running jaunty.

---

### Post by PmDematagoda on 2010-03-13
Closed due to necromancy.

---

