---
title: "Segmentation Fault in Network Tools"
date: 2005-11-14
forum: Desktop Environments
---

### Post by dbott67 on 2005-11-14
I've searched the forums and even some other Gnome-related forums regarding this, but have been unable to find a similar situation.

Whenever I try to start Network Tools (**Application > System Tools > Network Tools**) the program window flashes for about 1 second and then disappears.

When I run it from a terminal (**gnome-nettool**), I normally get a 'segmentation fault'.  Then, as I was gathering some more info and going to post the output, I got a new message:
```
dbott@breezy:~$ gnome-nettool
*** glibc detected *** free(): invalid pointer: 0x08204f00 ***
Aborted
```
I've checked the various log files (dmesg, kern.log, syslog, daemon.log, user.log, debug, messages) but I cannot find any messages that are related to the crash --- nothing listed at or around the times that I've run Network Tools.

I have used Network Tools in the past (although, it could have been in Hoary & Warty).

I have re-installed the nettools package from Synaptic but still it fails.  Anyone have any ideas?

-Dave

---

### Post by dbott67 on 2005-11-14
*bump*

Not trying to be pushy... just get a few more looks before this post gets buried into oblivion. ;)

---

### Post by Dr. Nick on 2005-11-14
Do you have any other kernels installed? Perhaps booting into another version of the kernel may help.

Have also read that open office segfaults alot with nvidia drivers, you have a nvidia video card? 
here is the link discussing their problems / solutions [http://ubuntuforums.org/showthread.php?t=26006](http://ubuntuforums.org/showthread.php?t=26006)

Not sure how to fix the glibc error, Did you just update or anything?

---

### Post by dbott67 on 2005-11-16
Thanks, Dr. Nick.

I do have a number of earlier kernels still installed back from the preview release version.  I'll try an earlier version & see what happens.

I don't have an nVidia --- just an integrated NeoMagic (it's a Toshiba Tecra 8000 laptop).

As for updating, I've only really run the security updates... a few apps here and there... 
- tux paint and another light-weight paint program
- AbiWord
- Tux racer
- tilda
- gDesklets (although I don't run it --- it consumes 100% of my little old 300Mhz cpu!)

That's about all I can think of at the moment.

I'll post an update after I try some of the other kernels.

-Dave

---

### Post by mistryfied on 2006-07-18
Did you ever get a solution to this? I've just run into exactly the same situation. I'm using a Tecra 8000 as well, plus the latest version of the kernel.

---

### Post by dbott67 on 2006-07-18
No... I never was able to get it going.  I retired the Toshiba & purchased a Dell 6400 Core Duo 1.83 GHz, 2 GB RAM, 100 GB HD & ATI x1400 w/256 RAM back in March.

I installed Dapper on the new Dell and everything works fine (although the wifi took a couple of weeks or finagling to get it going --- compiling the latest version of ndsiwrapper seemed to be the cure).

I tried installing a less-taxing distro (Puppy, DSL) but had hardware issues, so the Toshiba is now in dust-collector mode for the time being.

-Dave

---

### Post by euphro on 2006-11-13
I'm having the same problem with a Toshiba 4030 CDT running Xubuntu 6.06.1 LTS.  It does seem to be a Toshiba-specific issue, so far.  This is the first reference I've found to someone else having the same problem.  If I find a solution I'll link it back here :)

---

### Post by did_yééé on 2008-05-07
Héhéhé just for fun.

I have the message segmentation fault error message when lauching gnome-nettool with a Toshiba Satellite 4060XCDT running with a DEBIAN 2.6.18-6-686


Ciao !

---

