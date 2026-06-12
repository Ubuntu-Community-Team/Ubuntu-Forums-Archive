---
title: "ATI x.org 6.8 drivers released!!"
date: 2005-01-17
forum: General Help
---

### Post by Xappe on 2005-01-17
FINALLY!!

[http://www.ati.com/support/drivers/linux/radeon-linux.html?type=linux&prodType=graphic&prod=productsLINUXdriver&submit.x=10&submit.y=7&submit=GO%21](http://www.ati.com/support/drivers/linux/radeon-linux.html?type=linux&prodType=graphic&prod=productsLINUXdriver&submit.x=10&submit.y=7&submit=GO%21)

---

### Post by xkcdmagic8 on 2005-01-17
Someone Release Them Into Reposotories!!

---

### Post by albersag on 2005-01-17
You mean they are into repositories now?. Or you are requesting them to be on ?

:)

Daniels is working on it

[http://www.ubuntuforums.org/showthread.php?p=50603#post50603](http://www.ubuntuforums.org/showthread.php?p=50603#post50603)

---

### Post by Xappe on 2005-01-17
they're being put together for the hoary repos as we speak I think. jippijay!

---

### Post by albersag on 2005-01-17
When i bought my laptop (compaq presario) only vesa works.... now 3d.... always happen the same. With time and wait everything works in linux...

Some years ago nvidia did not have drivers, ati neither, now they both release binary (someones would like freely glp code), but at least we can enjoy in linux, that it is what we want.

:)

---

### Post by scotty2hott2k on 2005-01-17
hey, i installed warty today, just wondering will they also be released into warty so i can atp-get it? also will there be an updated how to of how to get the drivers working as im pretty newb and would need the how to ;)

thanks in advanced

---

### Post by daniels on 2005-01-17
Not in Warty, sorry; but Hoary will get this:
linux-restricted-modules-2.6.10 (2.6.10.2-1) hoary; urgency=low

  * Update fglrx driver to 8.8.25 (new Catalyst series); this version adds
    support for X.Org and amd64.  Update Build-Depends accordingly; split
    fglrx-driver into xfree86-driver-fglrx and xorg-driver-fglrx, and
    fglrx-driver-dev into xfree86-driver-fglrx-dev, and xorg-driver-fglrx-dev.
    The original packages are retained as dummy packages.  Bump versions
    accordingly.  Change 'grafics' to 'graphics' in ati/*.desktop.  Add
    8.08-kernel-2.6.10.patch, an official ATI patch to deal with changed
    pci_*() semantics in 2.6.10.  Update list of supported cards.  Add libGL
    diversions for fglrx.
  * Fix dependencies between l-r-m-2.6.10-2-power* and l-i-2.6.10-2-power*; this
    fix seems to have got lost in a previous revision.
  * Bump nvidia_minor, ati_minor, avm_minor.

 -- Daniel Stone <daniel.stone@ubuntu.com>  Sat,  8 Jan 2005 05:10:17 +1100

---

### Post by scotty2hott2k on 2005-01-17
[QUOTE=daniels]Not in Warty, sorry; but Hoary will get this:
linux-restricted-modules-2.6.10 (2.6.10.2-1) hoary; urgency=low

  * Update fglrx driver to 8.8.25 (new Catalyst series); this version adds
    support for X.Org and amd64.  Update Build-Depends accordingly; split
    fglrx-driver into xfree86-driver-fglrx and xorg-driver-fglrx, and
    fglrx-driver-dev into xfree86-driver-fglrx-dev, and xorg-driver-fglrx-dev.
    The original packages are retained as dummy packages.  Bump versions
    accordingly.  Change 'grafics' to 'graphics' in ati/*.desktop.  Add
    8.08-kernel-2.6.10.patch, an official ATI patch to deal with changed
    pci_*() semantics in 2.6.10.  Update list of supported cards.  Add libGL
    diversions for fglrx.
  * Fix dependencies between l-r-m-2.6.10-2-power* and l-i-2.6.10-2-power*; this
    fix seems to have got lost in a previous revision.
  * Bump nvidia_minor, ati_minor, avm_minor.

 -- Daniel Stone <daniel.stone@ubuntu.com>  Sat,  8 Jan 2005 05:10:17 +1100[/QUOTE]


so how do i go about upgrading to hoary ;)

---

### Post by coolbreeze on 2005-01-17
Ok help a newbie like me out.  What is the significance of the.org driver?  how is itdifferent?  and who should use it?

---

### Post by scotty2hott2k on 2005-01-17
[QUOTE=coolbreeze]Ok help a newbie like me out.  What is the significance of the.org driver?  how is itdifferent?  and who should use it?[/QUOTE]

the new ati driver is a major stepup (hopefully) from their previous released drivers, it now supports org, glsl (or somthing) has better stability and performance.

---

### Post by HiddenWolf on 2005-01-17
[QUOTE=scotty2hott2k]so how do i go about upgrading to hoary ;)[/QUOTE]
Don't, unless you know what you're doing.

---

### Post by albersag on 2005-01-17
How to update. via apt-get update i can not install it :)

Help needed

---

### Post by scotty2hott2k on 2005-01-17
[QUOTE=HiddenWolf]Don't, unless you know what you're doing.[/QUOTE]
 awww ok then, basically all i want to do is enable 3d rendering using the newest ati drivers on warty tbh, i iwll be completely satisfied with that, so any help would be much appreciated :).

---

### Post by Xappe on 2005-01-18
the new driver are now running on my comp. everything seems to work except XRandR, which means I cannot change resolutions when xserver is running.

off@tuxracer :D

---

