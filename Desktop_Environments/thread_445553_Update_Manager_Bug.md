---
title: "Update Manager Bug"
date: 2007-05-16
forum: Desktop Environments
---

### Post by tejuwala on 2007-05-16
I did fresh install of feisty. After that I was trying to down-grade the kernel version as some of O'Reilly drivers that I was trying to compile wasn't compiling. But I cudn't compile the kernel(2.6.18.8).. So I compiled it on my other m/c (with feisty on it) with .config file of my m/c.  Generally I install .deb packages with dpkg in shell but just this time I double clicked on the generated .deb packages (on my m/c offcourse).. it didn't go through and it got stuck!!
           After that I killed the process (actually I wasn't able to kill it with xkill) and I had to re-login.. and ever since I get following message when I try to use update-manager or apt-get..

"Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package linux-image-2.6.18.8 needs to be reinstalled, but I can't find an archive for it.'"


I would really appreciate any help. thanks. :KS 

Note: Although I was able to compile the same kernel(2.6.18.8) on my other m/c with its .config file, I wasn't able to boot in it in that machine. Can't I use any lower kernel than 2.6.20 in fiesty ??

---

