---
title: "Re/formatting USB devices"
date: 2009-04-12
forum: Desktop Environments
---

### Post by dlrider on 2009-04-12
Using the installed Gnome in 8.04 (and later), how do I _easily_ re/format a USB flash drive or memory card?  It seems to me to use *parted programs is overkill in that they scan (takes a long time) all drives before allowing a re/format on a simple USB device.  I have had need to format from some other file systems on these things and don't see the point in scanning my local hard drives, and possibly re/formatting those by mistake.  Geez, even in Windows, all I have to do is right-click the device and Format.  How do I do the same in Ubuntu or at least with Nautilus?  Thanks.

D.

---

### Post by sharathpaps on 2009-04-12
Hey,
         I read your post and I know you want an easy way to format your usb device. But I just wanted to point out that using gparted is not difficult at all and it does not take anytime, atleast on my system which is a 5 year old laptop!! Identifying your usb device should not be a problem because you can choose it from the drop down menu on the right upper corner. Once you do that, its just a matter of right-clicking and choosing 'Format' . Choose the filesystem and you're done. I can give you more detailed information if you want but trust me, it takes less than 40 seconds to format a 8gb usb device to FAT32 .. I can vouch for that.

---

### Post by dlrider on 2009-04-13
Thanks Sharathpaps, but I had already looked at gparted extensively.  Here're the problems I have with it:  1) takes almost 1 1/2 minutes to scan everything (hd with Ubuntu and Windows partitions, and card reader with a single card), 2) user must use root access (I'm not giving out the password, nor am I going to be there to do it for them), 3) they need to know what /dev/sdc is in the list.

Here's the situation:  I don't want ordinary users fooling with a partitioning program with access to the system partitions, but I have no problem to allow them to screw up their own card or USB stick, and not to bother me in the process.  It has to be obvious which device they are accessing (not /dev/sdc).

Is there anything out there that meets these requirements?  I suppose Nautilus doesn't or someone would have already said so.

Thanks.

---

### Post by miegiel on 2009-04-13
> **dlrider said:**
> Geez, even in Windows, all I have to do is right-click the device and Format.

Well, when I help people with their windows problems and they start to annoy me I right-click a disk and hover the mouse over the format option :twisted:

> **dlrider said:**
> Here's the situation:  I don't want ordinary users fooling with a partitioning program with access to the system partitions, but I have no problem to allow them to screw up their own card or USB stick, and not to bother me in the process.

If they want to they can always do that by booting from a liveCD.

What I'm wondering is why do they need to format anything anyway. Is it their "windows brain" that's telling them they need to format their USB disk? If they need to delete what's on the disk they can just delete it.

The only reason to [s]format[/s] make a new file system on the USB disk I can think of, is to change the file system type from fat to fat32 or ntfs or ext3 or whatever apple uses.

---

### Post by binbash on 2009-04-13
you can use gnome format

---

### Post by miegiel on 2009-04-13
> **binbash said:**
> you can use gnome format

He's using hardy, gnome-format is a jaunty package.

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gnome+format](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gnome+format)

---

### Post by Jakey_TheSnake on 2009-04-13
What if you added Jaunty repositories to your sources, then "sudo apt-get install gnome-format"? 

Just out of interest, would it work?

---

### Post by dlrider on 2009-04-13
> **miegiel said:**
> 
If they want to they can always do that by booting from a liveCD.

What I'm wondering is why do they need to format anything anyway. Is it their "windows brain" that's telling them they need to format their USB disk? If they need to delete what's on the disk they can just delete it.

The only reason to [s]format[/s] make a new file system on the USB disk I can think of, is to change the file system type from fat to fat32 or ntfs or ext3 or whatever apple uses.

Live CD is not very "friendly" either in that it takes time to boot...

I only use Windows when I absolutely need to (e.g. work) because this computer doesn't run it very well anyway.  But my Windows brain has experience with corrupted memory cards from the devices (camera; MP3 player; etc) and usually needs to be reformatted.  Also, if I have a new USB stick that has been partitioned and loaded with a bunch of "extras" (for Windows) and I want the full space, I want a simple way (so as not to confuse my Windows brain) to reformat the device.  And sometimes, I may want to do what you have already thought -- change file systems.  The "just works" Ubuntu is supposed to be easy and user friendly... you know, not some system programmer or M$ way.

I didn't want to update to Jaunty so soon, but if it is there and works (like I stated above)... cool -- it's long overdue.  If it doesn't, how about scripting?  or another program?

---

### Post by edthefox on 2009-04-14
I can't think of any program that will fit your specifications. But I can show you what I do. It's quite easy and very fast if you're comfortable with the CLI.

Insert <flash/media_card/external_hdd/whatever> then *immediately after* open a terminal and type dmesg 

```
user@computer:~$ dmesg ....
[ 3724.008404] usb-storage: device found at 9
[ 3724.008407] usb-storage: waiting for device to settle before scanning
[ 3729.008282] usb-storage: device scan complete
[ 3729.040023] scsi 9:0:0:0: Direct-Access              USB Flash Memory PMAP PQ: 0 ANSI: 0 CCS
[ 3729.668739] sd 9:0:0:0: [sdc] 3921920 512-byte hardware sectors (2008 MB)
[ 3729.669235] sd 9:0:0:0: [sdc] Write Protect is off
[ 3729.669238] sd 9:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 3729.669240] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 3729.672737] sd 9:0:0:0: [sdc] 3921920 512-byte hardware sectors (2008 MB)
[ 3729.673236] sd 9:0:0:0: [sdc] Write Protect is off
[ 3729.673239] sd 9:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 3729.673241] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[ 3729.673245]  sdc: sdc1
[ 3729.718940] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[ 3729.719025] sd 9:0:0:0: Attached scsi generic sg3 type 0
user@computer:~$
```

You need to look at the very last entries to identify the device id you want to work with. In this case its sdc.

If you want  a list of all the partitions on ALL your disks you can get it by issuing the fdisk -l command.

```
user@computer:~$ sudo fdisk -l
[sudo] password for user: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00049977

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd68c020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 2008 MB, 2008023040 bytes
62 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 3844 * 512 = 1968128 bytes
Disk identifier: 0x0e074860

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        1020     1960409    b  W95 FAT32
user@computer:~$ 
```

Next, you can't format a mounted file system so unmount it with umount. (sudo may or may not be needed)

```
user@computer:~$sudo umount /dev/sdc1
```

then you can format the file system according to your needs. fat32 for example...

```
user@computer:~$ sudo mkfs.vfat -n my_flash -v /dev/sdc1
[sudo] password for user: 
mkfs.vfat 2.11 (12 Mar 2005)
Auto-selecting FAT32 for large filesystem
/dev/sdc1 has 62 heads and 62 sectors per track,
logical sector size is 512,
using 0xf8 media descriptor, with 3920818 sectors;
file system has 2 32-bit FATs and 8 sectors per cluster.
FAT size is 3822 sectors, and provides 489142 clusters.
Volume ID is 49e4aa99, volume label my_flash   .
user@computer:~$ 
```

All of these steps may sound really complicated but they aren't. You just need to understand what you're doing so that you don't hose your system. Learn to use the terminal. You will NEVER regret it.

---

