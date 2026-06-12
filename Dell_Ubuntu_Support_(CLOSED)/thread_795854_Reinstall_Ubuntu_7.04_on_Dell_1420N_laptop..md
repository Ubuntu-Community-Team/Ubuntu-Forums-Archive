---
title: "Reinstall Ubuntu 7.04 on Dell 1420N laptop."
date: 2008-05-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by duanekf2jc on 2008-05-15
Hi Everyone,
 My son tried to update from Ubuntu 7.04 to Ubuntu 7.10 via the internet, & the update failed. The computer will not boot Ubuntu 7.10. It gives a warning that the build failed.

I am trying to reinstall Ubuntu 7.04 from the CD that came with the Dell 1420N laptop. So far I have tried these 3 menu selections:
- Start or install Ubuntu.
- Install with driver CD.
- Start in safe graphics mode. 

I get this same message for the above 3 selections:

Busybox V1.1.3 (Debian1:1.1.3-3ubuntu3) Built in shell (ash)
Enter 'help' for a list of built in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)

Any suggestions? Thanks in advance for your help.
Duane

---

### Post by hermes0710 on 2008-05-16
First of all check if you have a floppy in. If yes remove it. Then, select "Install with driver CD" but leave the normal installation cd inside and proceed. Does it work?

(Check this thread if it doesn't: [http://ubuntuforums.org/showthread.php?t=415009]("http://ubuntuforums.org/showthread.php?t=415009"))

---

### Post by notwen on 2008-05-16
Unfortunately Dell ships their N-Series machines w/ the regular vanilla Ubuntu install.  However, the Ubuntu install running on these machines require additional drivers/packages for certain hardware.  Since Dell began offering the N-Series machines w/ Ubuntu pre-installed they generally release these custom Ubuntu images a month or so after each official Ubuntu release, so be expecting a custom Hardy Heron image sooner or later.

You can find Dell's custom Ubuntu images [here]("http://linux.dell.com/wiki/index.php/Products/Client#Operating_Systems").  Just download which version you prefer to use, however keep in mind that Hardy Heron was just released and Dell will be releasing a custom image for the Inspiron 1420n somewhere in the near future.  Be sure to explore the Dell Linux Wiki for any issues your specified model may have w/ certain Ubuntu versions.  The wiki does a good job of giving easy workarounds for some issues that may be found, normally simple editing of some configuration files or simply copying & pasting some commands into a terminal.  Please post if you have any questions.  =]

---

### Post by dicecca112 on 2008-05-16
> **notwen said:**
> Unfortunately Dell ships their N-Series machines w/ the regular vanilla Ubuntu install.  However, the Ubuntu install running on these machines require additional drivers/packages for certain hardware.  Since Dell began offering the N-Series machines w/ Ubuntu pre-installed they generally release these custom Ubuntu images a month or so after each official Ubuntu release, so be expecting a custom Hardy Heron image sooner or later.

You can find Dell's custom Ubuntu images [here]("http://linux.dell.com/wiki/index.php/Products/Client#Operating_Systems").  Just download which version you prefer to use, however keep in mind that Hardy Heron was just released and Dell will be releasing a custom image for the Inspiron 1420n somewhere in the near future.  Be sure to explore the Dell Linux Wiki for any issues your specified model may have w/ certain Ubuntu versions.  The wiki does a good job of giving easy workarounds for some issues that may be found, normally simple editing of some configuration files or simply copying & pasting some commands into a terminal.  Please post if you have any questions.  =]

7.10 Start in Safe Graphics should have worked, but in some cases it doesn't.  Be sure to run the live CD first so you can remove any needed files from the computer.  To run the live cd from the Dell Images, just type live.

---

### Post by cheetaux on 2008-05-17
I recommend doing a fresh install of 8.04.  I did a fresh install of 8.04 on my 1420n and have had  absolutely no problems (other than the wifi light doesn't work).

---

### Post by duanekf2jc on 2008-05-17
Thanks for all your helpful comments:
- I don't have a floppy on the laptop.
- I downloaded the Ubuntu 7.04 version from Dell with my work pc & burned an ISO CD.
- The wireless access works - tried it at the wireless access at the pizza restaurant today.
- I still have to download the modem software & install it, for home use.

Duane

---

### Post by duanekf2jc on 2008-05-17
I'm going to sign up for broadband internet access at home before doing a fresh install of 8.04. My pc at work uses IE & it won't download the larger files. Not sure if it's an IE problem or an ISP problem.

Duane

---

