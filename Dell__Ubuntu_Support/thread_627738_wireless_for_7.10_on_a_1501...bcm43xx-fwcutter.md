---
title: "wireless for 7.10 on a 1501...bcm43xx-fwcutter"
date: 2007-11-30
forum: Dell  Ubuntu Support
---

### Post by Mecka on 2007-11-30
So I've been told that getting 7.10 to run wireless on a Dell 1501 is a snap.  All you have to do is go to System>Administration>restricted driver manager and then enable the wireless driver.  At that point it is supposed to ask you where you want to find the file wl_apsta.o, but for me it says "The software source for the package bcm43xx-fwcutter is not enabled".  At that point I can only say okay.  I've found places to download this file, but I don't know what to do with it.

---

### Post by Monkey_Tales on 2007-11-30
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by jan quark on 2007-12-19
i solved this this way:

get the two files

bcm43xx-fwcutter_006-1_i386.deb   and
bcmwl5.sys

google them


than when you have installed the cutter and are in the restricted drivers menu a screen will show up. Navigate to the bcmwl5.sys file. Click OK.

The driver should be loaded and enabled. worked for me. Report failure :)

---

### Post by glitch942003 on 2008-06-12
Your information helped me. Those two files solved my problem.

---

