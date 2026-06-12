---
title: "I'm having trouble building headers."
date: 2007-10-07
forum: Debian
---

### Post by jingo811 on 2007-10-07
I'm trying to install NDISwrapper on a non connected Debian machine.  I got these commands from someone to try.  But it didn't work, can you help me out?

**Somone told me to do this.**
> If you dont have an internet connection on the computer you will need the installation cd. Put it in the drive:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install linux-headers-`uname -r` build-essential

**The error.**
> 
$ **cat error**
Reading package lists...
Building dependency tree...
Reading extended state information...
Initializing package states...
Reading task descriptions...
Building tag database...
Couldn't find any package whose name or description matched "linux-headers-&#65533;2.6.18-5-686"
Couldn't find package "build". However, the following
packages contain "build" in their name:
linux-kbuild-2.6 linux-kbuild linux-kbuild-2.6.18 build-essential
Couldn't find package "essential". However, the following
packages contain "essential" in their name:
build-essential
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.



**Instructions from NDISwrapper readme file.**
> Prerequisites
=============

You need a recent kernel, at least 2.6.6 or 2.4.26, with header files
for the kernel. Make sure there is a link to the kernel source from
the modules directory. The command

**ls /lib/modules/`uname -r`/build**

should have at least 'include' directory and '.config' file.
Which didn't work in the first place that's why I got those commands from someone at the beginning of this post.

---

### Post by SkyNet2029 on 2007-10-23
This should work for you alot smoother...

[http://forums.debian.net/viewtopic.php?p=92284&]("http://forums.debian.net/viewtopic.php?p=92284&")

---

### Post by jingo811 on 2007-10-23
Tnx.

---

