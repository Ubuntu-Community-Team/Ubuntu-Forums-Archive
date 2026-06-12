---
title: "Installing Parallels"
date: 2009-04-19
forum: General Help
---

### Post by Fredvs79 on 2009-04-19
Hi,

 I'm trying to install Parallels workstation. I got a .deb file from them, and it installed fine, but then I need to configure Parallels, and it says that it can't find kernel sources.

I'm running Jaunty with the latest kernel
$ uname -r
2.6.28-11-generic

# apt-cache install linux-source-2.6.28
linux-source-2.6.28 is already the newest version.

$ ls /usr/src
linux-headers-2.6.27-11-generic      linux-source-2.6.28
linux-headers-2.6.28-11-generic      linux-headers-2.6.28   

I've read the walk-through [here]("http://ubuntuforums.org/showthread.php?t=1018159&highlight=parallels+install") and did everything it said to... but it still wont configure.

I'm stuck, what is it that Parallels is looking for?

---

