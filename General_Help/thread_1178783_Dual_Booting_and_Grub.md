---
title: "Dual Booting and Grub"
date: 2009-06-04
forum: General Help
---

### Post by PropheticAngel on 2009-06-04
I'm trying to learn how to dual boot Ubuntu and Windows XP with Ubuntu installed first.  I don't really care to reinstall Ubuntu to make this easier.

Anyways, I'm following the directions here:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

After I've restored the mbr, I get the machine to boot into Ubuntu fine.  However, I am not sure how to set up grub from here.  When I use gparted to look at partitions, the partition I installed Windows on is no longer there and seems to be simply included in my ubuntu partition as used space. 

The free space is only 25 gigs, which is the amount that was to be left after I put in a ~30 gig windows partition.  This without a windows partition visible in gparted confuses me.  

Where do I go from here?

---

### Post by Word Life on 2009-06-04
Just download the latest one and install it right from your computer. Do what it says, and it will automatically dual boot. That's what it did for me.

---

### Post by merlinus on 2009-06-04
You might post the output of:

```

sudo fdisk -l

```

That will show your partitions.

---

### Post by PropheticAngel on 2009-06-04
bob@d-dx:~$ sudo fdisk -l
[sudo] password for bob: 

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8c828c82

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11785    94662981   83  Linux
/dev/sda2           11786       12161     3020220    5  Extended
/dev/sda5           11786       12161     3020188+  82  Linux swap / Solaris

---

### Post by merlinus on 2009-06-04
From what I can see, there is no windows partition.

---

### Post by PropheticAngel on 2009-06-04
I think I have an idea for what is going on.  I believe I backed up the boot record before I created the windows partition.  

Upon backing it up that boot record, the windows partition was re-assimilated into the first partition.  That is the best I can come up with.  If that is the case, how do I go about making it know that it is actually two partitions?

---

### Post by merlinus on 2009-06-04
If the fdisk command and gparted are not showing sda1 as windows, then it is most likely gone.  The space it took is now occupied by linux.

Neither of these is dependent upon a boot record.  They show the partitions that exist on your hdd, and their format.

---

### Post by VMC on 2009-06-04
> **PropheticAngel said:**
> I think I have an idea for what is going on.  I believe I backed up the boot record before I created the windows partition.  

Upon backing it up that boot record, the windows partition was re-assimilated into the first partition.  That is the best I can come up with.  If that is the case, how do I go about making it know that it is actually two partitions?

You may have backed up the mbr. That has nothing to do with what fdisk shows. You no longer have a Windows partition.

---

### Post by PropheticAngel on 2009-06-04
According to
[http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm](http://www.dewassoc.com/kbase/hard_drives/master_boot_record.htm)

The master boot record contains a master partition table.

---

### Post by raymondh on 2009-06-04
> **PropheticAngel said:**
> I think I have an idea for what is going on.  I believe I backed up the boot record before I created the windows partition.  

Upon backing it up that boot record, the windows partition was re-assimilated into the first partition.  That is the best I can come up with.  If that is the case, how do I go about making it know that it is actually two partitions?

I believe when you installed ubuntu and EXT3 format, it has overwritten any windows partition you may have set aside.  As you noted earlier thru gparted and confrimed by fdisk output, you don't see the windows partition.

Do you want to go on and install windows after ubuntu or would you like to start from the beginning with a windows + ubuntu install?

---

### Post by PropheticAngel on 2009-06-04
> **raymondhenson said:**
> I believe when you installed ubuntu and EXT3 format, it has overwritten any windows partition you may have set aside.  As you noted earlier thru gparted and confrimed by fdisk output, you don't see the windows partition.

Do you want to go on and install windows after ubuntu or would you like to start from the beginning with a windows + ubuntu install?

I was going to try to do it with ubuntu then windows to try and learn something.  I've done it the other way twice before.  

Is there any way to retrieve the 30 gig partition that got ate up with my Ubuntu one or should I just repartition and reinstall everything?

---

### Post by raymondh on 2009-06-04
> **PropheticAngel said:**
> I was going to try to do it with ubuntu then windows to try and learn something.  I've done it the other way twice before.  

Is there any way to retrieve the 30 gig partition that got ate up with my Ubuntu one or should I just repartition and reinstall everything?

You could download and boot into a gparted CD and use it to create the 30GB as well as partition it to NTSF.  

You could also use the Ubuntu LiveCD to access gparted.

Go ahead and experiment.  The learnings you'll make (specially with GRUB) will be invaluable later on.  If you run into a brick wall, just post back and the forum will try to answer/guide you :)

Good luck.

---

