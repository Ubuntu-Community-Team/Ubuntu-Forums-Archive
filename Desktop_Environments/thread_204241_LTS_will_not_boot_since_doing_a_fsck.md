---
title: "LTS will not boot since doing a fsck"
date: 2006-06-26
forum: Desktop Environments
---

### Post by fyassine on 2006-06-26
Yesterday I was playing with a few commands and ran through a fsck.  Since doing this when I reboot it never starts X.  Recieve quite a few input/output errors and errors noting all the files are Read only.

Anyone familiar with this or more importantly have any ideas how I should move forward?  Thus far I have downloaded a LTS live cd so that I can at least get into the OS.

---

### Post by Sonofmoog on 2006-06-26
Run e2fsck from the LiveCD.  Make certain the device is *not mounted.*  Do man e2fsck for options ..Sounds like your filesystem is still messed up.  The bad news is you may be looking at a fresh install.  I had a similar problem: ran e2fsck and got a clean bill of health on the filesystem, and I still had to reinstall, because the kernel panicked.  It's a hard lesson, and I'm sorry if this sounds cruel, but for the benefit of anyone else reading this, *you **never** run fsck on a mounted file system .. *

---

### Post by fyassine on 2006-06-26
Is there any way that I could load the live cd, copy the contents to the hdd to make the os bootable, then simply overwriting all the files on the hdd from my previous installation?

I had quite a few configuration files that took me days to figure out and would likely give up if I had to do it all over again.

---

### Post by Sonofmoog on 2006-06-26
[QUOTE=fyassine]Is there any way that I could load the live cd, copy the contents to the hdd to make the os bootable, then simply overwriting all the files on the hdd from my previous installation?[/QUOTE]

I have tried this.  It worked .. maybe .. *once*.  

> I had quite a few configuration files that took me days to figure out and would likely give up if I had to do it all over again.

I've been there.  If you had the same problem I did, those config files are likely trashed anyway.

---

