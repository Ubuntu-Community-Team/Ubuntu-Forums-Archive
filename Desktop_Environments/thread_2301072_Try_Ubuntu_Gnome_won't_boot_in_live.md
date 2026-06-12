---
title: "Try Ubuntu Gnome won't boot in live"
date: 2015-10-30
forum: Desktop Environments
---

### Post by eipapp on 2015-10-30
I've run into an odd situation that I've never encountered before. I download Ubuntu Gnome 15.10
put it into my DVD drive and it loads fine. However, when I select Try Ubuntu Gnome it shows the
following message but will not boot up
(1 of 2) A start job is running for Ubuntu live CD installer (1 min 24s/no limit)
At this point beyond this message nothing happens.
I eventually have to select ctrl+alt+delete at which point it ejects the DVD.
I download the iso image from two different sites and the disks I'm using is from the same
pile of disks I've used to try other distros all of which worked just fine.
Any ideas as to what may be happening and how to correct it ??

Thank You,
Bruce

---

### Post by UncleBoarder on 2015-11-19
No answer but I have the same problem.  I also tried 15.10 KDE and Unity, they both work fine.

---

### Post by kansasnoob on 2015-11-20
It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147)

I was surprised they released without fixing that but they did.

---

### Post by kansasnoob on 2015-11-20
BTW on some hardware i was able to boot OK from the advanced boot menu:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

---

### Post by sudodus on 2015-11-20
> **kansasnoob said:**
> It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1489147)

I was surprised they released without fixing that but they did.

> **kansasnoob said:**
> BTW on some hardware i was able to boot OK from the advanced boot menu:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

Is this bug squashed for Xenial Xerus?

---

### Post by alexts2 on 2016-04-30
I've encountered the same problem, when I tried to use a live usb with Xubuntu 16.04 in it. I solved it by disabling the "ACPI APIC Support" option in my mobo's bios. 
Try to change the options in your bios which are associated with ACPI and HPET, possibly will be able to boot. I hope I helped someone to fix this irritating bug.

---

### Post by peter249 on 2016-05-24
Ive got the same problem so given up.........

---

### Post by jub2 on 2016-06-21
I sometimes get this message (A start job is running for Ubuntu live CD installer) with a Xubuntu 16.04 live ISO booted from usb flash drive. Most of the time it boots fine, so I just try again.

---

### Post by calimer on 2016-08-13
jub2 I have been getting the same problem!  With one PC it took three tries and the PC I'm trying now I haven't gotten it work after 10+ tries and I tried 16.04.1 as well.  I'm using rufus and I've tried all the variations I can think of.  I have booted ubuntu off the same USB stick and it had no problems so maybe it is something wrong in the xubuntu is0?  I'm using the 64 bit version.

---

### Post by tigi on 2016-10-22
I have had the same problem when i tried to boot from a USB stick with [COLOR=#000000][FONT=Arial]xubuntu-16.04.1-desktop-amd64.iso
I just left the computer as it was, without interrupting, while i was reading this thread on another computer.
When i went back to the affected computer, the problem disappeared, and there ws the proper GUI asking me if i wanted to try Ubuntu, or install it, etc.
I chose install it, and the installation complete fine (at first glance)
[/FONT][/COLOR]

---

