---
title: "computer wont turn on after installing ubuntu 9.10"
date: 2010-04-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Seithe on 2010-04-02
my computer will not run on start up as it usually would, when I installed ubuntu 9.10 on my desktop I get this run up saying or showing my computer details as it usually does but nothing will load up after this one line saying on my monitor: Ultra DMA Mode-5, S.M.A.R.T. Capable and Status OK       after it says this nothing loads but it is as my computer hung up and nothing works. Any ideas on how to fix this?

---

### Post by NightwishFan on 2010-04-02
Did the live CD of Ubuntu work? If so, then right after the BIOS (SMART.. etc) hold shift. You should see a screen asking you to boot Ubuntu. If not, then either you are not set to boot from hard disk, or grub did not install. Check your bios settings, if the disk is set to boot first, read this link, more specifically installing GRUB from the live CD.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by gibbylinks on 2010-04-04
> **Seithe said:**
> my computer will not run on start up as it usually would, when I installed ubuntu 9.10 on my desktop I get this run up saying or showing my computer details as it usually does but nothing will load up after this one line saying on my monitor: Ultra DMA Mode-5, S.M.A.R.T. Capable and Status OK       after it says this nothing loads but it is as my computer hung up and nothing works. Any ideas on how to fix this?

I'm know this sounds silly, but are you sure it's not booting ?

If I boot normally I get a black screen !! I have had to include the "nomodeset" command in GRUB to get the graphics to work !!

---

### Post by rokalacs on 2012-05-15
I know this post is REALLY old, but some may search for an answer just as I did.

I don't know about how to fix this for Ubuntu since I'm not familiar with those ext partitions, but for Windows you just have to format your C drive and make it active. For this you have to take your hdd into another machine as a secondary one and format it there. (or maybe if it has a jumper just make it as a slave drive and it may 'boot' up, tho I've never tried this).

Hope it helps someone.

---

### Post by dandnsmith on 2012-05-18
One of the features of installs which use the grub loader is that they don't care about partitions having the boot flag on or off as they use different means to effect the boot process.
You might, however, get a complaint originating in the BIOS, if you have none or more than one partition with boot flags on - but this will be manifested before you get properly into the boot.

---

### Post by coffeecat on 2012-05-18
Old thread closed.

---

