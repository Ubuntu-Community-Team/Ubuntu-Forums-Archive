---
title: "ATI - &quot;Kernel Module version does not match driver&quot;"
date: 2006-01-19
forum: Desktop Environments
---

### Post by cronholio on 2006-01-19
I just installed the new ATI drivers (8.21.7) hoping that finally OpenGL applications would stop crashing. After installation as described in the Wiki ([https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)) fglrxinfo showed the MESA driver.

In the Wiki it says:

> Note If you are having problems related to DRI or 3d acceleration and the following lines show up in your /var/log/Xorg.0.log 

(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work

then make sure you have linux-restricted-modules installed for your kernel (type sudo apt-get install linux-restricted-modules-$(uname -r)).

These lines do show up in the logfile although I DO have linux-restricted-modules installed for my kernel (2.6.12-10-386).

Any hints?

---

### Post by kaamos on 2006-01-19
I thinki you should **not** have the linux-restricted-modules installed if you use fglrx drivers other than the version in the repos (8.16.xxx). Look here: [http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466)

---

