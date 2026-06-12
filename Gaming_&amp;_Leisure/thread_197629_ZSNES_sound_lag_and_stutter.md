---
title: "ZSNES sound lag and stutter"
date: 2006-06-16
forum: Gaming &amp; Leisure
---

### Post by Punio4 on 2006-06-16
The sound is very stuttery, and it has a 1 second delay.
I searched the forums, and found this thread:
[http://ubuntuforums.org/showthread.php?t=140823&highlight=zsnes+sound](http://ubuntuforums.org/showthread.php?t=140823&highlight=zsnes+sound)
However, switching to OSS only made it worse. There was no sound at all, and the cpu usage was 100%, dropping my fps down do 20.
I'm sure I switched to OSS playback in the multimedia system selector.

By the way, I have a nForce2 with Soundstorm.

If anyone knows of another workaround/solution please let me know.

---

### Post by CronoDekar on 2006-06-16
Mine sound was staticy, so what I heard to do was to install the package libsdl1.2debian-oss, and it worked perfectly.  It'll remove the package libsdl1.2debian-alsa, but if this trick doesn't work you should be able to switch back to it easily.

---

### Post by Punio4 on 2006-06-16
Wow... i cannot believe this... forgot to restart linux... that's what has been giving me issues :D
Had only one sound source at a time, and fixed it by selecting ESD in the MMS output... but now i have lag when stopping music and such...
I can have gaim sounds with rythmbox, but any combination with zsnes... no go.

Is there any way to enable true hardware mixing... i have ABIT NF7-S... It has soundstorm, so everything should run smooth... right?
If i download the ones from the nVidia website, could that fix my problems?

---

### Post by srt4play on 2006-06-18
[QUOTE=CronoDekar]Mine sound was staticy, so what I heard to do was to install the package libsdl1.2debian-oss, and it worked perfectly.  It'll remove the package libsdl1.2debian-alsa, but if this trick doesn't work you should be able to switch back to it easily.[/QUOTE]

Thanks a lot for posting this, it fixed my staticy sound in zsnes. :)

---

### Post by hornett on 2006-06-19
Thanks! Worked for me too! :D

---

### Post by Zyprexa on 2011-01-20
When running ZSnes without having done anything after installing it, sound was ok but there was some small lag.

I then tried typing
```
zsnes -ad sdl
```in terminal, and the lag was gone but now the sound was cracking.
Then i tried typing
```
zsnes -ad esd
```and that seemed to fix both problems and the sound was fine.

I had to do this to each user on the computer.

---

