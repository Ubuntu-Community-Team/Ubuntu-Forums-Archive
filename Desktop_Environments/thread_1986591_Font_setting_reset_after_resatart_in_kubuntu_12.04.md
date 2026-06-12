---
title: "Font setting reset after resatart in kubuntu 12.04."
date: 2012-05-25
forum: Desktop Environments
---

### Post by Ravi5kumar on 2012-05-25
Hi, I have a very annoying problem with kubuntu. Every time when I change  the font, and after a restart or a root privilege is elevated the font  is changed to default ubuntu 9. How to fix this annoying issue:mad:?

---

### Post by cottfcfan on 2012-05-25
Same problem here.
Not after a reboot, but after root privileges.

---

### Post by Erik1984 on 2012-05-25
Happened to me also, luckily only one time: [http://ubuntuforums.org/showthread.php?t=1939803](http://ubuntuforums.org/showthread.php?t=1939803) (in 11.10) No idea what causes this behaviour, what should root privileges have to do with it? I expect the font settings to just be stored somewhere in ~/.kde Maybe it's best to file a bug upstream at [http://bugs.kde.org](http://bugs.kde.org)

---

### Post by cottfcfan on 2012-05-26
I have tried this for now.
```
kdesudo systemsettings
```
Then set the root fonts to the same as your user.
I only did this yesterday, so i'll see if the problem persists or not and reply in due course.

---

### Post by Ravi5kumar on 2012-10-13
Using the latest KDE DE and still this problem.....

---

