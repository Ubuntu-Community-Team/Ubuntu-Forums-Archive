---
title: "remote desktop"
date: 2010-11-10
forum: Desktop Environments
---

### Post by TonyDiF on 2010-11-10
I have a Ubuntu desktop running 
Linux tonydif-desktop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

I use TightVnc to remote desktop to to the Ubuntu server in my office while I am at home, which works but when I connect with TightVnc it unlocks my desktop window on my Ubuntu server and everyone now has access to my system since it is unlocked.  Is there a setting I need to set so when I do log in with TightVnc it does not unlock my desktop window ?

thanks
TonyD

---

### Post by TonyDiF on 2010-11-11
with some help I was able to solve part of my problem. On my Ubuntu Server  I need to start the server display to :1 by typing in [FONT=Arial]vnc4server :1 ... now I can open my remote desktop without opening the ubuntu server desktop at the same time. But my issue now is that [/FONT][FONT=Arial]what ever work I have started on my Ubuntu server will not be seen at home when I connect remotely with tightvnc through display :1.  So, what I am looking for is being able to connect to display :0 without opening my desktop in my office while I am at home connecting remotely ?[/FONT]
[FONT=Arial][/FONT] 
[FONT=Arial]thanks[/FONT]
[FONT=Arial]TonyDiF[/FONT]

---

