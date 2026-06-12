---
title: "Sounf in ubuntu minimal on inspiron 13"
date: 2010-09-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Makosz on 2010-09-13
I installed Ubuntu minimal, gnome gui, wicd, and b43 drives. My sound still does not work I have Inspiron 13, please help.

---

### Post by mörgæs on 2010-09-14
What exactly do you mean by 'does not work'? Which application are you trying to run?

Do you have sound on the machine if booted with a live CD?

---

### Post by Makosz on 2010-09-14
Well I tried to look up how to get it to work online but htere is nothing for ubuntu minimal. I have video on youtube now but no sound. AQlso it is onloy on mute and seem like I cant do anything because it does not have anydrives

---

### Post by mörgæs on 2010-09-15
Again: Do you have sound when booting with a live CD? Do you hear the Ubuntu sound while booting?


If that works:
Take a look in Synaptic at which packages you have. Especially the packages beginning with 'pulseaudio' are interesting.

On a minimal 9.10 with sound, I have the following installed:

pulseaudio
pulseaudio-esound-compat
pulseaudio-module-udev
pulseaudio-module-x11
pulseaudio-utils

Add them, reboot and try again.

If it does not work, please post your package list as described here:
[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

