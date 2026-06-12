---
title: "Ubuntu won't boot: cannot find GRLDR"
date: 2009-03-06
forum: General Help
---

### Post by kogger on 2009-03-06
I'm running a dual-boot Ubuntu with Windows Vista, but my Ubuntu doesn't want to boot anymore. Here's the message I get when I try to boot into it:

Try (hd0,0): invalid or null
Try (hd0,1): NTFS5: No wubildr
Try (hd0,2): NTFS5: No wubildr
Try (hd0,3): NTFS5: No wubildr
Error: cannot find GRLDR in all devices. Press Ctrl+Alt+Delete to restart.

My disk is split up into four partitions. I installed Ubuntu through Windows, but I put it on a separate partition:
[C drive -- Windows]-[E drive -- Ubuntu]-[F drive -- Storage]-[Unallocated]

Any idea how to get Ubuntu to work again?

---

### Post by LegendofTom on 2009-03-06
Sounds like grub and windows are fighting it out.  Is there any way to set it to boot your Ubuntu partition?  Your best bet might be to install Ubuntu with the partition manager on the Ubuntu install disk, instead of through Windows.

---

### Post by kogger on 2009-03-06
Is there any way to fix this without having to re-install it? If all else fails I can do that, but I would really like to avoid it if I could.

---

### Post by kogger on 2009-03-06
bump?

---

### Post by kogger on 2009-03-06
I tried both opening the Uninstall Ubuntu application and re-installing it by mounting a new .iso file in Daemon Tools, but none of it works. Is the only way to fix it to use a physical CD?

---

### Post by martrn on 2009-03-06
[http://supergrub.forjamari.linex.org/?section=download]("http://supergrub.forjamari.linex.org/?section=download")

Try super grub disk.

The floppy version *shold* be able to boot your ubuntu.

Added:
-----
Hang on a minute if you are using webi ubuntu (where ubuntu installs itself to one file on a windows disc) this is not going to work.  Webi file system is just a file which itself contains a file system which has files in it.  Not a brillient solution.  The Webi faq for repairing webi file systems is at [http://wubi-installer.org/faq.php]("http://wubi-installer.org/faq.php").

I would (personaly) not recommend trusting your whole file system to one file stored on a windows disk.

---

### Post by kogger on 2009-03-06
I don't think Ubuntu did install to my Windows disk. I originally installed it using a CD, and I re-partitioned my hard drive then so I could have Windows on C, Ubuntu on E, and general storage on F. Ubuntu shouldn't be dependent on Windows.

---

### Post by martrn on 2009-03-06
Ubuntu uses a different way to repersent hard disks to windows, and the file system is different.  From the top of my memory if you had 3 partitions of the first disk and one on the second you would have /hda1 /hda2 /hda3 and hdb1.   Whith drive E, its not clear weather this is a partition with a file system on it or if it is a spearate disk or whatever.

If you have a Ubuntu Live CD you should be able to boot up with it and find out about your hard disks and you might be able to run Gparted,   Gnome Partition Editor is a usefull application that can show you graphically how your computer has partitioned its hard drives and you can see what file systems are on your hard drives.

Personally I think its always good to have a copy of this on a bootable CD around.
[http://gparted.sourceforge.net/]("http://gparted.sourceforge.net/")

The supergrub disk mentioned above should be able to boot your ubuntu installation if you have it installed properly and the file structure for you linux partition is OK.

---

### Post by kogger on 2009-03-07
How do I use the supergrub disk?

---

### Post by kogger on 2009-03-07
Okay, I somehow got it working again. I think it's because I shifted some wubildr files over from E: to C:...but it works now.

---

### Post by varun.nagpaal on 2009-11-26
I'm running a dual-boot Ubuntu with Windows Vista. I was working in Ubuntu with some data intensive applications. As whole RAM got full, my system stopped responding, and I forced a restart by using the power button. After that Ubuntu doesn't want to boot anymore. Here's the message I get when I try to boot into it:

Try (hd0,0): NTFS5: 2
Try (hd0,1): NTFS5: No wubildr
Try (hd0,2): invalid or null
cannot find GRLDR 
Press space bar to hold the screen, any other key to boot previous MBR ...
Timeout : 5

Then it shows a 5 second countdown, and reaches the windows bootloader menu again
My disk is split up into 2 partitions. I installed Ubuntu through Windows, but I put it on a separate partition:
[C drive -- Windows]-[D drive -- Ubuntu]-[Maybe Unallocated]

Any idea how to get Ubuntu to work again?

---

