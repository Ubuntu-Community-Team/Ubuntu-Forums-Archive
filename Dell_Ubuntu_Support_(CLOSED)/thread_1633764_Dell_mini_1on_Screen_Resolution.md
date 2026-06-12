---
title: "Dell mini 1on Screen Resolution"
date: 2010-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fjgaude on 2010-11-29
Two, maybe three, questions!

I purchased a mini 10n from Dell with the hi-res 1366 screen. I updated the box recently with the ubuntu-10.10-i386.iso converted to a USB flash drive. The remix-type graphical screens are much slower than the original 8.04 LTS installed by Dell. And the box works at only 1024 x 768, a real bummer!

I've tried to go back to the original using the Dell DVD disc supplied with the machine, but I've not been able to create a USB flash drive from it, after trying over four times with different OSs on desktop boxes. (I don't own a USB external DVD reader.) Can you tell me how to create a USB from such a DVD drive? My desktop has all the hardware, software to do it but the Startup disk Creator simply doesn't work with the over 700 megabyte DVD.

Is there a way for me to modify Xorg or whatever to handle 1366? Or install a different screen driver that works at 1366 with Ubuntu 10.10?

Thank you for a reply. <smile>

---

### Post by mikewhatever on 2010-11-29
How did you update the box? As far as I know, updating from regular ISOs is not supported, let alone updating and upgrading from 8.04 to 10.10.
The Startup Disk Creator is intended to create USB startup disks and not DVDs or CDs, not to mention the fact that 8.04 iso might not boot from USB at all.
Can you post the computer specs, especially the output of **sudo lshw -C display**.

---

### Post by fjgaude on 2010-12-01
Okay, the mini 10n uses Intel Poulsbo chipset that is no longer supported in anything by Ubuntu. But to upgrade you need much skill. This link is a start:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

I'm running 10.10 with 1366 x 768 screen now.. all is cool!

Thanks for offering to help.

---

