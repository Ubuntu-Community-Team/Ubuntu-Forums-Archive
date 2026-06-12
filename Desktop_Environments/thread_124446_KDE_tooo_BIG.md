---
title: "KDE tooo BIG"
date: 2006-02-01
forum: Desktop Environments
---

### Post by ashrack on 2006-02-01
am an UBUNTU user. But wanted to try KDE also, as this was the desktop I was using in my previous linux distro Mandrake. Installed KUBUNTU-DESKTOP package and now at a resolution of 1125x768 this is how it looks:
[ATTACH]5770[/ATTACH]

how to make it smaller?

ps. upon the first bootup the resolution was set at 1600x1200 and KDE was looking normally but my non-kde apps eg. BMP player vere very small.
ps2.Get the same behavior with KDE 3.4 and the current one 3.5.1

---

### Post by gamma on 2006-02-01
I'm guessing you're using the nvidia drivers. For some reason whenever you use these drivers the fonts become huge. Default KDE at Kubuntu runs at 75dpi for fonts when the standard is generally 96dpi. A quick hack to fix this is go to /etc/kde3/kdm/kdmrc and line 468 'ServerArgsLocal=-nolisten tcp' change to 
'ServerArgsLocal=-nolisten tcp -dpi96' Hope that helped!

---

### Post by ashrack on 2006-02-02
No, am using ATI native drivers.
Apperantly I just had to restart X. Have been running the machine for 2weeks without restart, with the help of the wonderful hibernation

---

### Post by corneliusline on 2006-03-23
Ther's not any guru to handle this problem? I have some problem too.

---

### Post by stoeptegel on 2006-03-23
[QUOTE=ashrack]
how to make it smaller?
[/QUOTE]

The icons in konqueror?
K menu>System settings>top left button(uiterlijk in Dutch)>icons>tab advanced>Desktop/File Manager

---

### Post by aysiu on 2006-03-23
It looks to me as if a visit to Alt-F2 ```
kcontrol
``` is all that's necessary to fix that problem.

---

### Post by corneliusline on 2006-03-24
"kcontrol" really works! Change fonts from there.

---

