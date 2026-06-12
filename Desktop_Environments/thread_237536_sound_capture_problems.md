---
title: "sound capture problems"
date: 2006-08-16
forum: Desktop Environments
---

### Post by akshaysrinivasan on 2006-08-16
Hello,i have this strange problem,whenever i use the line-in or the microphone port,i can hear the sounds but applications like sound recorder and skype cannot capture it.i had the same problem with breezy as well.this forces me to reboot to windows.My configuration:-
AMD Athlon XP 2400+,
Asus A7N8X-MX SE with builtin AC97 audio

---

### Post by DoctorMO on 2006-08-16
It's a problem with the Alsa configuration and the fact that Skype (not sure about recorded) use OSS. you can try installing aoss and running skype through it with aoss skype.

I'm still trying to figure out a problem with one of the desktops I administer, it's got two sound sources but alsa just dosn't want to know either of them and won't record anything... rather anoying. I'll let you know If I find out whats wrong with it.

---

