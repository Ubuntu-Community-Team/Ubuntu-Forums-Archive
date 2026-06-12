---
title: "Mounting a USB image with multiple partitions on it"
date: 2009-04-18
forum: General Help
---

### Post by imbjr on 2009-04-18
I finally created a bootable Jaunty USB stick. 

The "Create a USB startup disk" function didn't work, I kept getting the Busybox prompt. Instead, I followed the instructions here:

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)

But when checking the integrity of the stick, it reported two checksums did not match, but did not say which ones. As it was, the stick booted fine.

But I wanted to find out what files were causing the problem. I ended up mounting the stick on my main PC and md5sum-checking that way and found out that the 2 files involved were autorun.inf and the wubi.exe files - so no great loss.

But in the process of all of this, I ended up backing up the stick to a dd image. I became interested in how I could do the md5sum-check by just mounting the image - except I found I could not do so.

The image contains two partitions, not one, so the issue is how to mount them from the image? Purely from an interested point-of-view since accessing the stick normally was no problem.

---

