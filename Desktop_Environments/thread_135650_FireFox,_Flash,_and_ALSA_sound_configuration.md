---
title: "FireFox, Flash, and ALSA sound configuration"
date: 2006-02-24
forum: Desktop Environments
---

### Post by FIONEX on 2006-02-24
Hi, I've been looking at a few articles about enabling sound in firefox and flash but I don't think they're using the ALSA server.  Does anyone know how to enable sound in firefox and the flash plugin on ubuntu using the ALSA sound server?
Thx in advance,
I K

---

### Post by jchau on 2006-02-24
I have the same problem.  Flash apps in firefox don't make sounds.

---

### Post by FIONEX on 2006-02-24
Umm well there's a small fix but doesn't really work well.  You go to your /dev directory and type:
 $ sudo ./MAKEDEV audio
That will make the sound work but only if no other sounds are currently playing.  It doesn't do software mixing, which sucks IMO.  This is such a deterrent that ruins your linux experience, you know?

---

### Post by victorgreen on 2007-10-06
I did that and got:

:/dev$ sudo ./MAKEDEV audio
udev active, devices will be created in /dev/.static/dev/


But when I opened youtube, there was no sound....

---

