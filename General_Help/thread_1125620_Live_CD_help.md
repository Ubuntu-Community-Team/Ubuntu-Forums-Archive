---
title: "Live CD help"
date: 2009-04-14
forum: General Help
---

### Post by Nicka727 on 2009-04-14
Will a 700mb CD+R disk work? And all that I have to do is burn the ISO onto a CD, Re-boot and I'm done?

---

### Post by mikewhatever on 2009-04-14
Yes, if your cdrom plays nicely with cd+r it should work. You have to burn the iso as image, do not make a data or a bootable cd. Burn at slow speed, max x4. Post back if there are any problems.

---

### Post by Nicka727 on 2009-04-14
Does it save anything to my HD?

---

### Post by Tim Sharitt on 2009-04-14
A 700MB CD should be sufficient. 

Before burning the image to disk, I would recommend checking the md5sum of the image ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)) to insure you're not burning a bad image. 

When burning the iso image to disk, it is advisable to use the slowest burn speed available to minimize the risk of burn errors.

After that, just pop in the CD and reboot. :)

One last note. If you need to do any editing to the partition table (i.e. resizing a partition to make room for Ubuntu), it is a good idea to backup any valuable data beforehand.

More info:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by jmszr on 2009-04-14
Nicka727,

   Here is some Ubuntu documentation on burning an .iso: [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto) .

---

### Post by paradigm2 on 2009-04-14
> **Nicka727 said:**
> Does it save anything to my HD?

No. As long as you strictly try the option which says "Try without installing to the hard drive" it should not touch your hard disk. 

If you do opt to install or even before using the Live CD, I highly recommend running the disk integrity check first (it is an option on the install/livecd.

---

