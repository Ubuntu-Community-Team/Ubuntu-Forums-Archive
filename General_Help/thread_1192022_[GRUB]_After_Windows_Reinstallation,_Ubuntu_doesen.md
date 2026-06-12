---
title: "[GRUB] After Windows Reinstallation, Ubuntu doesen't boot"
date: 2009-06-19
forum: General Help
---

### Post by Alefux on 2009-06-19
This is because Windows rewrote MBR.

Hi, I'm Alefux, and I'm new in this forum. Excuse me for my bad english, but i'm italian.

I can't login in Ubuntu Jaunty: Windows boots automatically.
I've executed some commands on shell (live cd Ubuntu 9.04), but i got some errors:

```
grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)


grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition


```


This is fdisk -l

```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33083308

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2           12749       19457    53890042+   5  Extended
/dev/sda3           19215       19457     1951866   82  Linux swap / Solaris
/dev/sda5           12749       19214    51938082   83  Linux
```


Can you help me please? ;)

---

### Post by TeoBigusGeekus on 2009-06-19
Look at this:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Alefux on 2009-06-19
I have an error..

```
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition
```

---

### Post by merlinus on 2009-06-19
Give this a try:

```

sudo grub
root (hd0,4)
setup (hd0)
quit

```

But I wonder why sda4 is missing?

---

### Post by Alefux on 2009-06-19
grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition


> But I wonder why sda4 is missing? 	
I think I deleted it

---

### Post by merlinus on 2009-06-19
Can you post a screenshot from gparted?

It looks as though your partitions are now numbered incorrectly, if you look at the results of sudo fdisk -l and the starting and ending blocks.

sda5 comes before sda3.

---

### Post by hibliss on 2009-06-19
Try Super Grub Disc.

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

Windows Bootloader writes over Grub, when installing (like doing a FixMBR). Super Grub Disc worked for me in the past.

---

### Post by Alefux on 2009-06-19
@merlinus Now i'm on live cd so Gparted doesn't found properly.

@hibliss Should I burn another cd? :S

---

### Post by merlinus on 2009-06-19
You should be able to run gparted from System/Administration/Partition Editor.  It does not matter that you are running from the live cd.

---

### Post by hibliss on 2009-06-19
> **Alefux said:**
> 
@hibliss Should I burn another cd? :S

If you decide to try this, you can use a flash drive.

From the link posted earlier -- [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

> Using the Unofficial "Super Grub Disk"

From within Windows

    *

      Download Auto Super Grub Disk
    *

      Double-click auto_super_grub_disk_1.0 icon, install it, and reboot.
    *

      On the next boot, select the UNetbootin-supergrubdisk menu entry; this will launch the Auto Super Grub Disk.
    *

      Do nothing till you see your Grub menu again.
    * Next time you boot Windows, click yes when asked to remove UNetbootin-supergrubdisk to remove the Super Grub Disk menu entry. 

As a standalone cd/floppy/usb

    *

      Download Super Grub Disk
    * Burn into a cdrom (better) or a floppy
    * Boot from it
    *

      Select: GRUB => MBR & !LINUX! (>2) MANUAL |8-)
    *

      Select the Linux or Grub installation you want to restore.
    * You see the message: SGD has done it!
    * Reboot
    * You're done. 

Preserving Windows Bootloader

The method shown above puts GRUB back on the MBR (master boot record) of the hard drive instead of in the root partition. But you probably won't want that, if you use a third-party boot manager like Boot Magic or System Commander. (The original poster also suggested that this would be useful to restore the Grub menu after a re-ghosting.) In that case, use this alternative.

This alternative, used without a third-party boot manager, will not cause Ubuntu to boot.

This alternative will let you boot your second hard disk Linux installations from Windows while the Using the Ubuntu Desktop/Live CD Preserving Windows Bootloader instructions will not.

Either:

    *

      Download Super Grub Disk
    * Burn into a cdrom (better) or a floppy
    * Boot from it 

Or:

    *

      Download **_[UNetbootin Super Grub Disk Loader]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=261880")_** (Windows .exe version)
    * Run the installer and reboot when once done installing.
    * On the next boot, select the "UNetbootin-supergrubdisk" menu entry; this will launch the Super Grub Disk interface. 

Then:

    *

      Super Grub Disk (WITH HELP) :-)))
    *

      Select: your language
    *

      Select: Windows
    *

      Select: Windows chainloads Grub!
    *

      Select the Linux or Grub installation you want to restore to its own partition.
    * You see the message: SGD has done it!
    * Reboot
    * You're done. 

Pretty easy on CD or USB.

---

### Post by Alefux on 2009-06-19
I got an error:

Error 15: File not found

---

### Post by louieb on 2009-06-19
What you did is the normal way to restore the MBR. But grub setup probably got confused because you have a non-standard (invalid) partition table. Primary partition sda3 is inside extended partition sda2.   

I've seen others fix this using sfdisk, but I haven't.

---

### Post by Alefux on 2009-06-19
So what should i do? I have a lot of important files..

---

### Post by merlinus on 2009-06-19
Try this:

```

sudo fdisk /dev/sdX  # Example: sudo fdisk /dev/sda  Don't put a partition number, just the device.
#  Then select the following menu items:
m  # Menu
x  # Expert mode
f  # Fix partition order
w  # Write to partition table (saves the changes)

```

---

### Post by Alefux on 2009-06-19
```
Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.

```

---

### Post by hibliss on 2009-06-19
As far as accessing the data, it can be done from within Windows, so you are in no danger of losing it and it is still there.

Once you fix the MBR, all should be well. Did you think about trying Super Grub Disc?

---

### Post by Alefux on 2009-06-19
I tried Super Grub Disk, it doesn't work: Error 15: file not found.

---

### Post by louieb on 2009-06-21
Found out how to use **sfdisk** to fix a partition table. [sfdisk to fix partition table problems]("http://ubuntuforums.org/showthread.php?t=1192598")

If you look at the very 1st example [http://ubuntuforums.org/showthread.php?t=1095606](http://ubuntuforums.org/showthread.php?t=1095606) this guy has the same problem and it showed up right after a windows re-install. Coincidence - I think not.

Note that sfdisk is a very powerful partition table editor. It can fix your partition table. 
 ( rearranged the output in start order)
   > 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2           12749       19457    53890042+   5  Extended
/dev/sda5           12749       19214    51938082   83  Linux
/dev/sda3           19215       19457     1951866   82  Linux swap / Solaris

From the looks of it all that needs to be done is change the end of extended partition sda2 to match the end of your swap partition sda5. Leaving sda3 outside the extended partition sda2.

to start please post the resulting pt.txt from this command.

```
sudo sfdisk -d /dev/sda > pt.txt
```

---

### Post by egalvan on 2009-06-21
Is it be possible to erase the /sda3 swap partition,
then re-create it as a primary /sda3 swap in the empty space that seems to exist after sda1?

If so, then I suggest saving /sda3's UUID before removing the partition,
and assining it after the partition is re-created.

I don't know which would be easier, or safer.

I haven't used fdisk ( or sfdisk ) in some ten years,
but I think you can delete a partition by designation.
No need to resort to starting and ending blocks, or bytes.

Picks you your poison... :)

---

