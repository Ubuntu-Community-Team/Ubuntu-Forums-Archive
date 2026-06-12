---
title: "(xm)Grace look bad"
date: 2009-04-30
forum: Education &amp; Science
---

### Post by Ladgalen on 2009-04-30
Hello

Since I have installed ubuntu9.04, xmgrace shows black square instead of the numbers or the text.

See here for a screenshot :

[http://ftp-developpez.com/germain-vallverdu/grace_vue.png](http://ftp-developpez.com/germain-vallverdu/grace_vue.png)

Is it a way to fix it ?

Thanks

---

### Post by Ladgalen on 2009-05-01
I have found this bug on the net :

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/325169](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/325169)

But I am a basic linux users and I do not really all understand. If someone can help me to fix this bug I will be very glad.

Thanks

---

### Post by molbio_rush_2009 on 2009-09-14
I am having the same trouble. Can anybody help in fixing it ? Is it due to ubuntu 9.04 installation ?
thanks

---

### Post by pellao on 2009-09-15
Hello!!!
Is not a problem of ubuntu 9.04... i have a laptop (core duo) and grace works fine with ubuntu 9.04.
In my office i have a quad core (new) with ubuntu 9.04 and i have this problem!!!!!!
I have no idea hor to fixed!!!!

---

### Post by lebonstemps on 2009-10-01
Hi, 

I had the same problem and was told the following solution: 

edit as root /etc/X11/xorg.conf, include the two lines starting with Option given below in the section "Device"

Section "Device"
  [INDENT]Identifier      "Configured Video Device"[/INDENT]      
  [INDENT]Option "EXAOptimizeMigration"   "true"[/INDENT]  
  [INDENT]Option "MigrationHeuristic"     "greedy"[/INDENT]
EndSection

Afterwards you have to restart the X window manager or reboot the computer!

It worked fine for me!

Good luck!

---

### Post by crotchet on 2009-10-21
> **lebonstemps said:**
> Hi, 

I had the same problem and was told the following solution: 

edit as root /etc/X11/xorg.conf, include the two lines starting with Option given below in the section "Device"

Section "Device"
  [INDENT]Identifier      "Configured Video Device"[/INDENT]      
  [INDENT]Option "EXAOptimizeMigration"   "true"[/INDENT]  
  [INDENT]Option "MigrationHeuristic"     "greedy"[/INDENT]
EndSection

Afterwards you have to restart the X window manager or reboot the computer!

It worked fine for me!

Good luck!
It works for me, thanks a lot!!

---

