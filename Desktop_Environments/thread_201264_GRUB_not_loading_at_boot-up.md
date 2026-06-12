---
title: "GRUB not loading at boot-up"
date: 2006-06-21
forum: Desktop Environments
---

### Post by poper on 2006-06-21
I'm willing to switch to Ubuntu from WXP, however, since I'm a newbie I want to  keep Windows running and use Ubuntu in a different HD (a bual workstation)
Installation went smooth but after rebooting GRUB doesn't load. WXP is always loaded. In order to use Ubuntu I need the LiveCD. 

I've tried to install GRUB (as described [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")), but after typing "*rescue*" in the "*boot:*" prompt, GRUB is loaded (which is not expected).

I've also tried this:
```
sudo grub-install /dev/sda
```

and got this:
```
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda

```

but nothing happens.

So any help will be welcomed.

I'm using 6.06 AMD64, my computer has got 3 HD, as follows:

**/dev/hda **--> Hard drive #1
**/dev/hdb** --> HD #2
--hdb1 (FAT32) 
--hdb2 (Ext3) - Where linux is installed.
--hdb5 (Swap)
**/dev/sda **(NTFS) HD #3 where WXP is installed

Thanks in advance.

---

### Post by ajgreeny on 2006-06-21
How is your computer set up to boot in the BIOS.  It sounds rather as though you asked for grub to be put on sda (the windows MBR?) when you installed but for some reason either the MBR is already on another partition or grub went on to the partition where you installed ubuntu.  There certaily seems to be a mix up  in the place that grub ended up in.  What did you ask to happen to grub when installing?

Perhaps it's worth just trying each of the disks as first boot device, in sequence, in the BIOS to see if grub appears from any of those before you do anything more drastic.

PS If you don't know there's a very good site on all things Ubuntu at the following address:-
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
including a good Ubuntu 6.06 user guide.  It may not help this particular query but could be useful in the future.

---

### Post by poper on 2006-06-23
Thanks for your answer.
The BIOS boot sequence is:
1-SATA
2-HDA
3-HDB - Where Ubuntu is installed.

I've tried to install GRUB in the SATA disk, because it seems that GRUB is installed in the Linux Partition (I didn't choose this option, the whole process was automatic, I just chose the partition where to install Ubuntu). However it didn't fix the problem but made it worse.

Now when booting the system, WinXP is not automatically loaded and an infinite loop appears as follows:

[IMG]http://img101.imageshack.us/img101/1588/imagen0115zv.jpg[/IMG]

So I've tried to fix the boot with **fixmbr **and **fixboot **but it doesn't work (because it's AMD64 system?). In order to loas any OS I need to use the LiveCD, select 'boot from first HD", then GRUB loads and finally I choose Ubuntu or WinXP to load.

---

### Post by poper on 2006-06-23
well I've found [here]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/16824") this:

> 

This problem occurs when both SATA and IDE drives are installed. This continues in 6.06 LTS.

While installing SATA drives are counted first followed by IDE drives.

In menu.lst the assignment is reversed.

This problem does not occurr in Fedora, Suse and Mandriva. It may be noted that these distros allow to explicitly specify location of boot loader.

An average user is unlikely to to have a mixture of hard drives.


But no solution is provided :(

---

### Post by poper on 2006-06-24
Solved:

*grub-install /dev/hda*

then change the boot sequence (in BIOS) to load *hda* in first place.

Thanks.

---

