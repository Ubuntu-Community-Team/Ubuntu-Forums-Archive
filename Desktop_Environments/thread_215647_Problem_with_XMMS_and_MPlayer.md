---
title: "Problem with XMMS and MPlayer"
date: 2006-07-14
forum: Desktop Environments
---

### Post by psixpsi on 2006-07-14
hi all!

after switching to Dapper, I got this two problems:

1) XMMS won't play most of the times, asking me to check if sound card is installed, the plugins are correct or another program is blocking the sound card (which I doubt). When running from terminal I get this:

** WARNING **: oss_open(): Failed to open audio device (/dev/dsp): Device or resource busy


2) MPlayer won't start at all as a stand-alone program (only within Firefox). Starting it from Applications menu I receive for a fraction of a second some error message and the nothing. Same when trying to open mp3's with File Browser. Starting from terminal just prints the options.

Uninstallation and reinstallation of both programs did not help :-( Any ideas?

Thanks!
psixpsi

---

### Post by Riverine on 2006-07-14
I encounter a very similar problem with xmms this morning.

I fixed the problem by changing the output device selection of the output plugin from "default" to "hw:0,0".   I can't explain why it worked for me and it may not work for you, but it is easy to try and easy to reverse (if it doesn't work).

Right click on the xmms player, then Options --> Preferences  to open the preferences dialog.  In the "Output Plugin" section of the "Audio I/O Plugins " tab click the "Configure" button to open the ALSA Driver Configuration dialog.  On the "Device settings" tab select "hw:0,0" from the Audio Device section box (or try any setting other than default).

Remember to click the Apply button before closing the Preferences dialog.

Hope it helps.

---

### Post by mrbaz on 2006-07-14
I have a slightly different issue.  XMMS plays all my local media just fine, but it will not play anything across the network.  Is this unsupported, or am I doing something wrong?

---

### Post by psixpsi on 2006-07-15
Thanks Riverine!

What helpped was actually switching to ALSA. The price to pay was that I somehow lost the ability to controll volume with keyboard shortcuts on my Fujitsu P1510, but XMMS works fine now + I got rid of the distorted sound due to too high PCM level.

Any ideas re MPlayer, though???

Best,
psixpsi

---

### Post by taurus on 2006-07-15
Open a terminal (Applications -> Accessories -> Terminal) and run from it to see exactly what the error is!!!

```

mplayer

```

---

### Post by utnubu001 on 2006-07-15
if u have amarok:
amarok is blocking the sound card
make sure u say quit and not just exit amarok
otherwise it stays in ur system tray
i also had that problem

---

### Post by psixpsi on 2006-07-17
> **taurus said:**
> Open a terminal (Applications -> Accessories -> Terminal) and run from it to see exactly what the error is!!!

```

mplayer

```

that's the point - i don't seem to see any errors, it just list the program options. this begins with:

MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Pentium M Dothan (Family: 6, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv[:dev]>  select video output driver & device ('-vo help' for a list) ... etc

best,
psixpsi

PS I'm not using Amarok. The XMMS problem I solved switching output to ALSA

---

### Post by Yleeyas on 2006-07-18
Hello psixpsi,

When I upgraded to Dapper I had the same problem with mplayer. The solution I found was to use Synaptic to reinstall the mplayer-skins.
Here is the thread that helped me:
[http://www.ubuntuforums.org/showthread.php?t=193528](http://www.ubuntuforums.org/showthread.php?t=193528)

Hope this helps

Yleeyas

---

