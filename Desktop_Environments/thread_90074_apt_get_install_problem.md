---
title: "apt get install problem"
date: 2005-11-14
forum: Desktop Environments
---

### Post by hollowhead on 2005-11-14
Oops I think I posted this to the wrong forum sorry I'll try again hopefully this is the right one.   Trying to install xmms in deb package format using apt get install.  I run the command at the terminal within the dir with xmms.  The package installer starts working (saying its unpacking the file or something) then says E: cannot find xmms_blahblah.deb even though that is the name I have just told it to start installing.  What is going on- is it a path problem?  I tried apt-get update this runs w/o error but does not solve the problem.  Ta. Hollowhead.

---

### Post by r4ik on 2005-11-14
Why not ty to install xmms with synaptic ?

---

### Post by oskude on 2005-11-14
try```
dpkg --install yourpackaganame.deb
```

---

### Post by ubuntu_demon on 2005-11-14
you should enable universe and multiverse in your sources.list (multiverse isn't necessary for xmms but handy for other stuff)

Or use my sources.list : [http://www.ubuntuforums.org/showthread.php?t=87946](http://www.ubuntuforums.org/showthread.php?t=87946)

To edit your sources.list :
$ sudo gedit /etc/apt/sources.list

After that just do  in the terminal (without $):
$ sudo apt-get update ; sudo apt-get install xmms

---

### Post by hollowhead on 2005-11-14
Cheers I'll try these.  The reason why I am not using syntapic is due to the fact that I have an unsupported modem Conexant chip.  A company has written a free 14.4 driver which I'm going to try when they tell me which download is the right one (none exactly matches my kernal name).  Also they are in deb format.....

---

### Post by ubuntu_demon on 2005-11-14
[QUOTE=hollowhead]Cheers I'll try these.  The reason why I am not using syntapic is due to the fact that I have an unsupported modem Conexant chip.  A company has written a free 14.4 driver which I'm going to try when they tell me which download is the right one (none exactly matches my kernal name).  Also they are in deb format.....[/QUOTE]
If you need a special kernel or special to make something work this doesn't mean you need to install the rest of your software in a special way too.

good luck!

---

