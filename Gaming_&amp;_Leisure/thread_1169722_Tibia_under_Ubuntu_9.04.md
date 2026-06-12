---
title: "Tibia under Ubuntu 9.04"
date: 2009-05-25
forum: Gaming &amp; Leisure
---

### Post by Oxious on 2009-05-25
Greetings everyone!

I have recently upgraded my Ubuntu machine from version 8.10 to version 9.04.
When I was using 8.10 it was possible for me to use ATI's (I have a Radeon x850 xt) proprietary "fglrx" driver package in order to activate hardware acceleration and other features. The native Tibia Linux client was working fine there.
(Tibia is a 2d isometric MMORPG, it has DirectX and OpenGL support. The Linux client natively only runs under OpenGL)

Now after I have upgraded to Ubuntu v9.04 I cannot use the "fglrx" drivers any longer. This is because ATI has set driver support to legacy for many of their cards. The newest Catalyst driver package for Linux does not support my graphics card and I cannot install any older versions as Ubuntu 9.04 is using xServer 1.6 which does not support older versions of "fglrx". But you are probably aware of all that fglrx trouble ATI is causing us..

My system is running perfectly fine on Ubuntu 9.04 using the OpenSource "radeon" drivers.
That was some basic knowledge I thought could be of importance to you. Here's my problem:

When I try to start Tibia using the "StartTibia.sh" file (as I always did on Ubuntu 8.10. That file is working as a starter for the game. If it's needed I can also post what that file contains) I see the game window pop up for a split second until it vanishes without further notice.

This is what I get when I try to start the client using the shell terminal:

[I]jens@jens-desktop:~$ cd Tibia
jens@jens-desktop:~/Tibia$ ./Tibia
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  128 (XFree86-DRI)
  Minor opcode of failed request:  7 ()
  Resource id in failed request:  0x3600008
  Serial number of failed request:  68
  Current serial number in output stream:  68
[/I]
I cannot make anything out of this.. If needed I can also post my xorg.conf file.

I would greatly appreciate any help.

---

### Post by Oxious on 2009-05-26
Any suggestions? :/

---

### Post by Oxious on 2009-05-27
Noone has a clue?

Can someone atleast give me any hints on how to repartition my hdd?
This is the case:

I have a 160gb hdd partitioned in 2gb linux-swap and the rest in ext3 (the rest contains the OS and files). However the remaining ext3 partition is way too big hence there's much unused space.
Is there a way I can shrink this partition and split it so that I can create another 50~gb partition in fat32 or ntfs to install WindowsXP on it (so in the end I have the possibility to dual-boot Windows for gaming and Linux for everything else). I don't feel like formating the whole thing and set up a new Ubuntu as well. :/

---

### Post by carml on 2009-05-27
The only solution I can see is the same you found: install a previous version of Ubuntu.
Said that I think of two ways: 1.boot with a Live-CD of e.g. 8.04 and install it following the instructions provided by the wizard; 2. use the Live-CD or a GParted LiveCD to shrink your Ext3 partition and then install a previous version of Ubuntu.

---

### Post by oldrocker99 on 2009-05-27
It's a sad thing that Canonical and ATI, operating separately, have hosed the adoption of 9.04 by people who bought a laptop manufactured last August (such as myself) simply rolled their system back to good ol' 8.10 and all is well again. 

I'm still waiting for someone more able than me to figure out a way (an XOrg rollback, maybe?) for the fglrx drivers to work under 9.04.](*,)

:guitar:

---

### Post by Oxious on 2009-05-27
Well, I guess it seems like the only option for now. But I am convinced that this will be more or less fixed in the future. I appreaciate the great work all the contributors are doing.. I was probably just a bit hasty with upgrading. :)

---

