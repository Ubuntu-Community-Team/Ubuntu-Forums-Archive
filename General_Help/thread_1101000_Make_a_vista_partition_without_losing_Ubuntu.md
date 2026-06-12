---
title: "Make a vista partition without losing Ubuntu?"
date: 2009-03-19
forum: General Help
---

### Post by GranteedEV on 2009-03-19
Okay here's the deal: about a month ago my laptop's HDD died on me and started looping, so i bought a new, empty harddrive. However my laptop is an HP, so it didn't come with a recovery disk, just one of those awful recovery partitions. I called HP and they told me it would take a while, and i didn't want my laptop sitting around being worthless, so i figured for the time being i'd go open source and install something like ubuntu. Thus, I installed ubuntu, and now i've got some a lot of really important files on my hard drive  

HP sent thier recovery disk, however when i popped it in, it doesn't give you that usual vista option of making a partition etc. It told me i have to format my entire hard drive for Vista.

Anyone got any ideas how I should go about this without losing my install and all the files i've got?

---

### Post by jlochhead on 2009-03-19
I can't think of a solution without spending some money.

Either move the important files to a USB flash drive, external hard disk or cd/dvd.

You can pick up a USB flash drive quite cheaply, although storage is limited. (I picked up a 16GB for £18, roughly $25) - smaller ones are much cheaper.

External hard disks are now a great investment if you want to back stuff up or increase your storage; they are a bit fragile though. I got a 1 TB one off Amazon for £60, roughly $84.

CD/DVD is the cheapest option. You need a writer though.

---

### Post by ufuxlinux on 2009-03-19
I don't understand your problem. Do you need a NTFS (windows) partition on a same hard drive with Ubuntu? Do you want to resize your Ubuntu partition without losing data? Because these are possible things.

---

### Post by Helios1276 on 2009-03-19
Backup all your important files on something, then make a bootable iso of your install with 'remastersys'. finally, wipe the drive then install vista followed by your Ubuntu?

---

### Post by jlochhead on 2009-03-19
> **ufuxlinux said:**
> I don't understand your problem. Do you need a NTFS (windows) partition on a same hard drive with Ubuntu? Do you want to resize your Ubuntu partition without losing data? Because these are possible things.

His problem is that his recovery cd will destroy all Ubuntu partitions when he uses it. This cd has no option to install to a single NTFS partition.

---

### Post by Roasted on 2009-03-19
> **jlochhead said:**
> His problem is that his recovery cd will destroy all Ubuntu partitions when he uses it. This cd has no option to install to a single NTFS partition.

If that's the case, it sounds like wiping the system is a requirement.

-Back your stuff up.
-Install Vista.
-Use the Ubuntu installer, Ubuntu LiveCD, or a GParted LiveCD to resize the Vista partition.
-Install Ubuntu.

---

### Post by ufuxlinux on 2009-03-19
> **Roasted said:**
> If that's the case, it sounds like wiping the system is a requirement.

-Back your stuff up.
-Install Vista.
-Use the Ubuntu installer, Ubuntu LiveCD, or a GParted LiveCD to resize the Vista partition.
-Install Ubuntu.

JUst adding to these, while you are backing up your data, you can use Aptoncd to backup you downloaded .deb packages in order to restore again without downloading them.

---

### Post by Nano_ext3 on 2009-03-19
Just install vista on the second partition (use gparted to make another partition or to resize the current one but backup data first if you can), then install grub again to restore the menu list entries

See:  [http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)


Cheers!

_Nano

---

