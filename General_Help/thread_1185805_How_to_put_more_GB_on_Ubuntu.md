---
title: "How to put more GB on Ubuntu ?"
date: 2009-06-12
forum: General Help
---

### Post by :)Brandon on 2009-06-12
Well I started out with 12GB, cos i thought i might not like it. But I actually LOVE ubuntu. Is there anyway i can transfer more GB to my ubuntu partition? Im dual booting with xp. Thanks <33

---

### Post by jbruced on 2009-06-12
I would suggest defragging Windows and then booting into the Ubuntu Live CD to a desktop, run gparted, and from there you can resize your Windows partion(smaller) and then apply changes. When that is complete, resize your Ubuntu partition(larger) and apply changes.

[EDIT} Forgot to say welcome, glad you're here.

---

### Post by merlinus on 2009-06-12
You can use gparted to resize partitions, but defrag your win install and delete temp and other unneeded files first.

Probably best to use the live disk.  Burn the .iso as a disk image and boot from it.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by Therion on 2009-06-12
Here's a little guide to using gParted to resize partitions.  You can use the aforementioned Ubuntu LiveCD or you can download a gParted LiveCD.  Either will take you to the same application.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by :)Brandon on 2009-06-13
> **Therion said:**
> Here's a little guide to using gParted to resize partitions.  You can use the aforementioned Ubuntu LiveCD or you can download a gParted LiveCD.  Either will take you to the same application.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)


This guide does not help. I dont have /dev/hda1

And I dont have any blank cds.
So the livecd is out of question.

---

### Post by t0p on 2009-06-13
> **:)Brandon said:**
> This guide does not help. I dont have /dev/hda1

And I dont have any blank cds.
So the livecd is out of question.

You can make a live usb stick too.  But maybe you don't have any sticks either?

When I dual-booted Ubuntu with XP, I used the XP partition as storage space for my files - mostly music and video.  You should be able to see your XP partition when you're running Ubuntu as it can use NTFS file systems fine.  So you can click and drag stuff to/from XP partition to Ubuntu.  You can also play, say, a video file that is in the XP partition by telling your vid player the path to it.

---

### Post by Old_Grey_Wolf on 2009-06-13
> **:)Brandon said:**
> 
So the livecd is out of question.

If you don't have a Live CD, then how did Ubuntu get installed on your computer?

---

### Post by Slim Odds on 2009-06-13
> **merlinus said:**
> You can use gparted to resize partitions, but defrag your win install and delete temp and other unneeded files first.

Delete first, then defrag....

---

### Post by QIII on 2009-06-13
Back up everything you do not want to lose from Windows!

Back up everything you do not want to lose from Windows!

Back up everything you do not want to lose from Windows!

Back up everything you do not want to lose from Windows!

Back up everything you do not want to lose from Windows!

(I know it goes without saying, but...)

---

