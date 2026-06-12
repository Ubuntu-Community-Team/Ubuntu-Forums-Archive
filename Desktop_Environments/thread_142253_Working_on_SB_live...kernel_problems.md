---
title: "Working on SB live...kernel problems"
date: 2006-03-10
forum: Desktop Environments
---

### Post by Snipe3D on 2006-03-10
So im working on getting my SB Live working...using the instructions found at
[http://www.ubuntuforums.org/showthread.php?t=19307](http://www.ubuntuforums.org/showthread.php?t=19307)

I get to the point where I need to make the package, and here is the output:
> root@DD:/usr/src# cd modules/alsa-driver && sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r)/ KVERS=$(uname -r)
You don't have the compiler that your kernel was built with installed
make: *** [configure-stamp] Error 1


I go to check the kernel..
> root@DD:/usr/src/modules/alsa-driver# apt-get install kernel-headers
Reading package lists... Done
Building dependency tree... Done
Package kernel-headers is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package kernel-headers has no installation candidate


Here is the output for uname -a
> root@DD:/usr/src/modules/alsa-driver# uname -a
Linux DD 2.6.12-10-386 #1 Mon Feb 13 12:13:15 UTC 2006 i686 GNU/Linux


Any Ideas?

EDIT - got it...

---

### Post by hw-tph on 2006-03-10
The key error is this:
> You don't have the compiler that your kernel was built with installed

Try installing gcc-3.3 or gcc-3.4 - I don't recall which one is used in the stock Ubuntu kernel. You can check what gcc version was used to compile the kernel you're running using **cat /proc/version**.


Håkan

---

### Post by skirkpatrick on 2006-03-10
Hey, Snipey :)

Yeah, the problem is that Breezy installs gcc-4.0 with build-essentials but the kernel was built using gcc-3.4.

---

