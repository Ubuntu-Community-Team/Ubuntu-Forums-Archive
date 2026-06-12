---
title: "Black screen after boot with one white dot"
date: 2010-01-01
forum: Desktop Environments
---

### Post by middlechild on 2010-01-01
This problem is entering its second day, I cannot use the computer in its current state.  My wife complains of multiple computers in the house, but at least I can access the forum from another machine.

New computer, Intel DG41TY motherboard, E5400 processor, reformatted drive on install, single OS - Ubuntu 9.10 Desktop. 2 Gbytes of RAM, also new. On board graphics port without any additional video card.

Computer has been working for a week, through various reboots, installing games, reading email.  A family of users using the computer to do what families do.  Yesterday the screen went black, meaning no desktop of any kind, just black.  At the time we were using a game with space invading chickens that runs full screen.  The system hung.  Rebooting it (through power off/on) produced a black display after normal boot processes.  Reboots of the system produce the white Ubuntu circle, no GRUB menu (Grub appears for less than one second) as this is a sole OS, and then sits at a totally black screen with one white dot in the upper left corner.

Right now I am sitting at the command prompt.  Repeated attempts at CTR-ALT-F1 were necessary, as it does not work consistently.  CTL-ALT-DEL does appear to reboot the system consistently though.

I am sitting at a command prompt now, do not want to lose it as it was difficult to get.
The output from "lspci -nn | grep VGA" is as follows:
VGA Compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
I do not have an Xorg.conf file

I am OK with turning off desktop effects, if I can find how to do it from the command line if that will fix the issue.

Thanks in advance

---

### Post by middlechild on 2010-01-02
Re-installed Workstation software.  Works now.  No idea what the root cause was for losing the desktop.  Perhaps installing and removing an old game, PyScrabble?  Perhaps Chicken Invaders (Unix edition) perhaps I still have an old monitor driver issue that will raise up once again. I don't know.  Not confident at all that the problem is fixed.  However the symptoms are gone now.

---

