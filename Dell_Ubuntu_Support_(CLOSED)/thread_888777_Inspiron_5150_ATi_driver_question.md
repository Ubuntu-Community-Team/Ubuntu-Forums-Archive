---
title: "Inspiron 5150 ATi driver question"
date: 2008-08-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zx6r1033 on 2008-08-13
I've been at this one for the past week, and I seem to be getting nowhere, so I am in hopes that someone can give me a push in the right direction.  

I have an Inspiron 5150 Laptop with an ATi Mobility Radeon 9000 graphics card. I am trying to find drivers for it. The graphics right now, even when playing small video files, are very glitchy. 

I have found a number of pages that make reference to both AMD drivers and 3rd party drivers, but 90% of them seem to be outdated or nonexistent. The ones I can actually download either don't work or I cannot install them. 


[http://www2.ati.com/drivers/linux/linux_8.8.25.html](http://www2.ati.com/drivers/linux/linux_8.8.25.html)

This page lists my card, but has no link to the drivers. 


[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

This page doesn't list any 9000 series in their download. 


[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

This page offers instructions, but when I type sudo apt-get update, I get an error message: "the method driver /usr/lib/apt/methods/htto could not be found."


Gatos fought me every step of the way on install, and then it crashed my computer completely. 


Any ideas here?

---

### Post by zx6r1033 on 2008-08-13
oh, I also should have added... I cannot adjust the screen resolution. It is locked at 1600 x 1200, so everything is quite hard for me to read, as well.

---

### Post by mehtdosa11 on 2008-08-14
just a thought have you tried add/remove applications?

search for ati drivers [under show: all available applications]

download
ATI binary X.org driver package

some 9000 drivers seem to be listed there

---

### Post by zx6r1033 on 2008-08-14
That driver doesn't offer support for my graphics card. 

> * Mobility Radeon: X1800, X1600, X1400, X1300, X800, X700, X600, X300, X200, 9800, 9600, 9550, 9500


:( Of course it couldn't be *that* easy.

---

### Post by superm1 on 2008-08-14
That description needs to be updated.  They no longer support the R200 hardware.  You are best off with the open source driver.

---

### Post by zx6r1033 on 2008-08-14
Thanks for the reply.

---

### Post by nanotube on 2008-09-22
i also have a 5150 with ati mobility radion 9000 (64 mb)
it fails to boot from the hardy livecd (freezes right after the orange progress bar goes away and it should go into the desktop). it only works in safe graphics mode (vesa driver)

so... could you tell me how you got it to work with the FOSS ati driver at all? i am currently running feisty, but since that's about to go out of its support period, i'm gonna be upgrading to hardy one way or another...

---

