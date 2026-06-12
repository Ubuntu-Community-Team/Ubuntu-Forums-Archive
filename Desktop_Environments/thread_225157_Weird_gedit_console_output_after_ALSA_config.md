---
title: "Weird gedit console output after ALSA config"
date: 2006-07-29
forum: Desktop Environments
---

### Post by Nannygoat on 2006-07-29
Hello,

there are a couple of threads in the forum regarding this issue without proper solution or at least explanation because I'm not exactly sure if this is a problem at all. I configured ALSA following this excellent howto:

[http://ubuntuforums.org/showthread.php?t=44753](http://ubuntuforums.org/showthread.php?t=44753)

After editing esd.conf and asound.conf I receive some strange console messages when starting gedit in the terminal:

nannygoat@nannygoat-ubuntu:~$ sudo gedit /etc/libao.conf
- using device default
- using device default
Audio device open for 44.1Khz, stereo, 16bit failed
Trying 44.1Khz, 8bit stereo.
Audio device open for 44.1Khz, stereo, 8bit failed
Trying 48Khz, 16bit stereo.
nannygoat@nannygoat-ubuntu:~$

I experience no side effects, sound is working great (music, movies, skype, etc.) with full-duplex. Has anybody any idea what is the exact reason for this output lines? I repeat, no other side effects, just gedit. Very annoying though. Thank you for your help!

Best regards,
Dimitar

---

### Post by tph on 2006-12-04
I experience the same thing. Tt doesn't really bother me, but I find it strange.

---

