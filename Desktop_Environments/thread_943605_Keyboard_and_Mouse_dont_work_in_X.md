---
title: "Keyboard and Mouse dont work in X"
date: 2008-10-10
forum: Desktop Environments
---

### Post by chrisd234 on 2008-10-10
Hello all,

Today I was upgrading my 8.1 distro, since it was in update manager. During the cleanup phase, my cat jumps on the power button. 

Computer shuts off and when I restart, everything seems fine except it boots to gdm, and my keyboard and mouse dont work.  The same applies to USB keyboards and mice, so i can't login.

Am I the only one?

I tried doing a recovery, but when it tries the package repair, it cant connect to the repositories. 

I'm currently stationed in Holland so it's trying to reach nl.ubuntu~~ and failing.

any advice?

---

### Post by Portugal on 2008-10-10
Same problem here with Xubuntu 8.10,after some updates and a restart mouse and some keys on keyboard dont work,example alt+f2 goes to a console window,so i think some updates have problems.

EDIT: found a solucion that solves the problem for me,go to recovery console and sudo apt-get install xserver-xorg-input-all after install simply reboot and go to x.

---

### Post by chrisd234 on 2008-10-11
Thanks for that! It worked perfectly

---

