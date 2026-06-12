---
title: "Repartitioning help"
date: 2006-01-03
forum: General Help
---

### Post by TrinitronX on 2006-01-03
I've just stumbled upon a problem while trying to repartition my ubuntu hard drive.  Here's the setup of the partitions:
```
|   Ubuntu root disk space   (ext3)  ||  swap partition  ||    OS share disk space   (fat32) |
```

I recently discovered the ext2/3 file system driver for windows, making my OS share fat32 partition unneeded.  So, I decided to try and remove it, expanding the main ext3 partition and leaving the swap partition.  So, I've copied the contents of the OS share drive to the ext 3 partition in preparation of removing it.  Anyways... I shut down my machine, and booted from the live cd, hoping to be able to use gparted to repartition the drive.  However, I've run into a problem.  Because of the way the partitions are arranged, it seems impossible to expand the original ext3 partition, and move the swap partition.  In gparted, the swap partition has a lock symbol on it, and I'm not able to move it to the end of the disk.  Is there any way to get this to work?

---

### Post by plors on 2006-01-03
use the [gparted livecd]("http://gparted.sourceforge.net/livecd.php"). This cd will not mount any drives so you can do whatever you want.

cheers..

---

### Post by TrinitronX on 2006-01-06
I just tried using the latest version of this, but I can't even get past the screen that asks for the language I want to use.  It won't respond to my keyboard.
Is there any way to force a live linux CD to not mount a swap partition at boot?
I've tried knoppix, and ubuntu so far, and both show the swap partition as being in use for some reason.  However, when I try to force it to unmount using: ```
sudo umount /dev/sdb2
``` it says that it's not mounted?
I looked in my /etc/fstab file, and that is the device path for that particular partition.  What's going on here?

---

### Post by plors on 2006-01-06
you should use 'swapoff' instead of 'umount'.

this livecd is still in developmentstage, so i'd like you to send your comments to the developer. ([http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php"))

thanks!

---

### Post by TrinitronX on 2006-01-06
ok... I used ```
sudo swapoff -a
``` to turn off my swap partition.  I was then able to use gparted in the ubuntu live cd to delete my fat32 partition, and move the swap to the end of the drive.  However, it crashed with an error window while resizing my root ext3 partition.  The window just had "error" in the titlebar, and nothing in it at all.  I just closed out of it, and then tried resizing the ext3 partition again, this time freezing my whole computer.  I had to do a hard reboot to recover, and when I rebooted with the live cd, it shows that the ext3 partition is resized, but it's 93% full?  I then booted from the root partition, and looked at the disks manager program, which still shows my 3 old partitions on the drive?

I really am confused now... it seems something really got messed up here.  Is there any way to fix my partitions now?  Maybe I'll try using partition magic (assuming it works with ext3 partitions).

---

### Post by plors on 2006-01-07
hmmz, sounds nasty.
most likely the partition got resized and the filesystem didn't. Best solution is to resize it again with a small amount (say 20 mb) to let the resizer fix stuff. So just grow (or shrink) that partition with 20 meg and if everything went succesfull shrink (or grow) it back.

good luck!

(also, running resize2fs <partition> may fix a lot)

---

### Post by TrinitronX on 2006-01-11
Thanks!  I finally fixed it for good.  After being able to move the swap partition to the end of the drive, I didn't have to use noswap again before using gparted.  This is because that part of the drive would not be getting touched with the resizing.  I took your advice on re-sizing the first ext3 partition (subtracting 20 MB), and hit apply.  Then I waited until it finally finished, this time without an error!  I rebooted into the ubuntu live DVD again, and much to my surprise, the partitions were back to what they were supposed to be before!  It was as if it rounded up those 20 MB, and made the partition correctly this time.  I haven't lost any data, and everything is fine now.  

I have looked into the amount of free space on the first partition, and it is now correct as well.  After all this, I merely had to edit my /etc/fstab again, removing the old fat32 entry.

Thanks for the advice!

---

