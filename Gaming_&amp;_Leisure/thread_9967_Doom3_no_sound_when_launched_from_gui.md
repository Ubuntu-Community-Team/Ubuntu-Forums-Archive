---
title: "Doom3: no sound when launched from gui"
date: 2005-01-03
forum: Gaming &amp; Leisure
---

### Post by Dylanby on 2005-01-03
I'm running Ubuntu AMD64.

Doom 3 was installed into a 32bit chroot in my home directory.
(I installed the chroot 'cause I'm a PC gamer with no windows)

I wasn't getting any sound until I started from the console using:
```
$ ./doom3 +set s_driver oss
``` 

Now if I start a terminal & do:
```
$ dchroot -d ./doom3/doom3
``` 
everything works fine. Although I get these errors:
```
------ OSS Sound Initialization ------
opened sound device '/dev/dsp'
ioctl SNDCTL_SYSINFO failed: Invalid argument
this ioctl is only available in OSS/Linux implementation. If you run OSS/Free, don't bother./dev/dsp - bit rate: 16, channels: 2, frequency: 44100
allocated a mix buffer of 16384 bytes
WARNING: ioctl SNDCTL_DSP_SETTRIGGER PCM_ENABLE_OUTPUT failed: Broken pipe
``` 
Like I said, sound works this way (I don't think my onboard sound card works with alsa & emulated oss). (<= edit: forgot alsa doesn't work under 32bit chroot)

I created a launcher to launch Doom 3 from the 'Applications => Games' menu.
But when started this way I get no sound.
Under 'Launcher Properties', 'Command' I've tried "dchroot -d /home/dylan/doom3/doom3" & also "dchroot -d ./doom3/doom3".

So what am I doing wrong?

---

