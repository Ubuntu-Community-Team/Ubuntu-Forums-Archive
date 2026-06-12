---
title: "Installation XFCE"
date: 2006-09-12
forum: Desktop Environments
---

### Post by knuth_ on 2006-09-12
PC-Configuration: PIII (600), 128MB SDRAM (PC133), 15GB HDD, GForce2 64MB, 15" Monitor. The System shall only be used for listening music (mp3=XMMS)

Hello,

Tried (unsucessfully) to install XFCE on that System. But step by step. Be informed that i don't have an internet-access yet. Downloaded the Ubuntu-DVD and the Xubuntu-Alternate CD (both 6.06).
1. Choosed "install a server"
2. manually edited the partitions:
/ = 1GB
swap = 256MB
/home = the rest

3. after installing the minimal-system i added the DVD/CD with ```
sudo apt-cdrom add
```
4. Then installed the xserver-xorg, x-window-system-core and xterm without  any problems.```
sudo apt-get install xserver-xorg, etc.
```
5. As Desktop-environment i choosed XFCE - tried to install it with ```
sudo apt-get install xfce4
```but everytime i got this message saying ```
Reading package list ... Done
Building dependency tree ... Done
Package xfce4 is missing, has been obsoleted, or is only available from another source
E: Package xfce4 has no installation candidate
```
Tried it with the Ubuntu-DVD (which incl. *universe*) as well the Xubuntu-CD (which comes with XFCE). What am I doing wrong?

---

### Post by knuth_ on 2006-09-14
Edit:

funnily enought i installed the Xubuntu-Desktop```
sudo apt-get install xubuntu-desktop
``` But it doesn't worked really propper with that system - to slow. But that means it installed the desktop-environment which uses xfce. Anyway I'm not able to install xfce alone??!!

---

### Post by moore.bryan on 2006-09-14
[I]you could try ```
sudo aptitude install xfce4-core
``` have you looked at openbox?
[http://www.icculus.org/openbox](http://www.icculus.org/openbox)
 [/I]

---

### Post by knuth_ on 2006-09-14
thanks,
I'll try..

---

