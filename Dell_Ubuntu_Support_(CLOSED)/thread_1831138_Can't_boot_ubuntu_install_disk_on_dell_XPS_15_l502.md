---
title: "Can't boot ubuntu install disk on dell XPS 15 l502x"
date: 2011-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zonedabone on 2011-08-23
The install disc freezes right after the accessibility screen, and doesn't get anywhere from there. Thee disk has a regular sound as though it's trying to read something over and over again. I have downloaded bot the 32 and 64 bit versions and have tried it from a disk and a usb drive. If you need any hardware info please tell me.

Thanks for all the help in advance!:guitar:

---

### Post by Idefix82 on 2011-08-23
Did you check the disc [MD5 sum]("https://help.ubuntu.com/community/HowToMD5SUM")? See also [here]("https://help.ubuntu.com/community/BurningIsoHowto") for a few tips, e.g. try burning the CD at low speed.

Can you run a live session (try Ubuntu from CD without installing)? Is all the hardware recognised in the live session?

---

### Post by snimavat on 2011-08-23
I had very similar issue with l502x where screen will go black.
I solved it by setting NOMODSET as explained here 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by zonedabone on 2011-08-23
Ok! I burned a brand new disk last night and it actually booted. Now I'm just plagued by a little doubt that came form the partition screen. I have a screenie below. Anyway, I have a 750gig drive, but it says it's 12giig, and the says windows is 13gig! Anyway, I'm wondering if I should continue the install or abort and procrastinate some more.

Also, the second screeny contains the advanced partition table, which actually looks correct. (The medium one is dell backup and the small one is microsoft's slowness storage partition ;))
Oh! Also, I can't resiize the large partition, which means ubuntu wasn't going to. Stupid ntfs.

---

### Post by Idefix82 on 2011-08-23
I strongly recommend you not to resize an ntfs partition from Ubuntu. Remember, this is Windows, so the partition is all fragmented, so it might be half empty, but have data all over the place. Boot Windows, defragment several times (once or twice might be enough), then resize from within Windows. Just leave the space unallocated that you want to use for Ubuntu and let Ubuntu create the partitions there. See if the strange issue with lost space then still persists.

---

### Post by zonedabone on 2011-08-23
> **Idefix82 said:**
> I strongly recommend you not to resize an ntfs partition from Ubuntu. Remember, this is Windows, so the partition is all fragmented, so it might be half empty, but have data all over the place. Boot Windows, defragment several times (once or twice might be enough), then resize from within Windows. Just leave the space unallocated that you want to use for Ubuntu and let Ubuntu create the partitions there. See if the strange issue with lost space then still persists.

Isn't it a system partition? Can you resize system partitions?

---

### Post by web-e on 2011-08-30
> **zonedabone said:**
> Ok! I burned a brand new disk last night and it actually booted. Now I'm just plagued by a little doubt that came form the partition screen. I have a screenie below. Anyway, I have a 750gig drive, but it says it's 12giig, and the says windows is 13gig! Anyway, I'm wondering if I should continue the install or abort and procrastinate some more.

Also, the second screeny contains the advanced partition table, which actually looks correct. (The medium one is dell backup and the small one is microsoft's slowness storage partition ;))
Oh! Also, I can't resiize the large partition, which means ubuntu wasn't going to. Stupid ntfs.

The screenshot is showing correct data.Your windows partition is of 13GB, ubuntu is of 7GB.The total HDD is 750GB that is written in the device selector for grub installation(The top drop down box)

---

### Post by web-e on 2011-08-30
> **zonedabone said:**
> The install disc freezes right after the accessibility screen, and doesn't get anywhere from there. Thee disk has a regular sound as though it's trying to read something over and over again. I have downloaded bot the 32 and 64 bit versions and have tried it from a disk and a usb drive. If you need any hardware info please tell me.

Thanks for all the help in advance!:guitar:



When the accessibility screen comes, Press F6, move cursor to nomodeset and press enter.Now you are ready to go.. :popcorn:

---

### Post by skyburner on 2011-09-03
Boot from USB3.0 does not work. Boot from the USB-Port on the right side inside of the esata. Worked OOTB for boot from USB with 11.04.

---

