---
title: "Change file permission for external drive?"
date: 2009-02-10
forum: General Help
---

### Post by zami on 2009-02-10
Change file permission for external drive?

I have a USB "stick" I use to move files from machine to machine, which has decided this evening it is "read-only file system".

How can I force this back into a writeable stick?

The locked files are one thing, and curiously they are all .rec files and are like ghosts of files deleted months and months ago.  

The real problem is the **entire disk **is "read-only" so I can look at these strange ghost files (and copy them), but I can't add new files to the stick.

Any help appreciated!

-zami

---

### Post by zami on 2009-02-11
What I've tried so far - all failures

Idea One : fail!
sudo chmod 777 /media/LEXAR
gives
"chmod: changing permissions of `/media/LEXAR': Read-only file system"

Idea Two : fail!
gksudo nautilus  LEXAR>properties>permissions tab and settings
gives
"Sorry, could not change the permissions of "LEXAR": Error setting permissions: Read-only file system"

Idea Three : ?
I haven't yet tried "safely remove hardware" via Windows, because I haven't used this disk on a Windows system in a rather long while, and feel I should be able to solve this without borrowing someone else's computer.  

Idea Four : fail!
I tried formatting the dang thing via gparted.  No go.  I can see it, but all I can do is look at it, or unmount it.  Argh!

-zami

---

### Post by amac777 on 2009-02-11
Your USB disk is probably corrupted so it was mounted as read only. You can try to repair using the following steps.

1. With the USB drive mounted, use the command:

```
mount
```

to figure out which device it is. (for example, /dev/sdd1 on my computer... it will probably be different on your computer.

2. Unmount the USB device using:

```
sudo umount /dev/sdd1
```

3. Check and repaire the errors on the USB device:

```
sudo fsck -r /dev/sdd1
```

4. Then unplug it and plug it back in and see if it mounts correctly as read/write.

---

### Post by zami on 2009-02-11
Holy smokes!  There were just a ton of errors on that thing!

"differences between boot sector and its backup"
"FATs differ but appear to be intact."
lots of "....contains a free cluster....." fragments to delete

Amazing.

It's working perfectly now though.  amac777? Thank you so much!!

-zami

---

### Post by aryangor on 2009-12-19
worked for me as well - thanQ !! :KS

---

### Post by ggpauly on 2010-06-15
Worked for me too - what's the issue with these thumbdrives - is it necessary to manually umount them befor pulling them out?

---

### Post by ouq77 on 2010-08-10
Thanks amac777.  You saved the day!

---

### Post by dmrkonjic on 2010-11-07
I also had a same problem with USB stick, but fsck did not work - because it's not ext2 fs or something... My stick is fat32. Finaly I scaned it with WXP and fixed... 

Is it possible to do fsck for fat32 in Ubuntu?

---

### Post by salterlee on 2011-04-14
Excellent solution - thanks so much. I've been trawling the boards all morning - I should have guessed it was something so simple! I guess it happened when I removed the drive from a windows machine without ejecting properly.

---

### Post by AkiraCrosshair on 2011-07-16
Perfect solution. Worked like a charm. Found 600 error on the drive. Last time Im letting windows format a drive for me.

---

### Post by fmoyota on 2011-08-11
I have a problem with usb drive was ntfs formatt

fsck -r /dev/sdb1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdb1

---

### Post by bo.vestergaard on 2011-08-12
I get the exact same error on 11.04. Does anyone know why?

---

### Post by coffeecat on 2011-08-12
> **fmoyota said:**
> I have a problem with usb drive was ntfs formatt

fsck -r /dev/sdb1
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sdb1

> **bo.vestergaard said:**
> I get the exact same error on 11.04. Does anyone know why?

Because, if I'm reading earlier posts correctly, fsck was being used on a FAT formatted filesystem. There is no fsck for ntfs - "fsck.ntfs" does not exist. If you want a Linux tool you need to run ntfsfix. However, that is no substitute for Windows' chkdsk, and if you want to know the reasons for this read man ntfsfix. If you have a corrupted NTFS filesystem, use chkdsk in Windows. Use a Microsoft utility for a Microsoft filesystem.

Second piece of advice for both fmoyota and bo.vestergaard. Try not to tag onto an old thread that was already beginning to go off-topic. You're more likely to get help by starting your own threads.

---

### Post by m42tyger on 2011-12-20
> **amac777 said:**
> Your USB disk is probably corrupted so it was mounted as read only. You can try to repair using the following steps.

1. With the USB drive mounted, use the command:

```
mount
```

to figure out which device it is. (for example, /dev/sdd1 on my computer... it will probably be different on your computer.

2. Unmount the USB device using:

```
sudo umount /dev/sdd1
```

3. Check and repaire the errors on the USB device:

```
sudo fsck -r /dev/sdd1
```

4. Then unplug it and plug it back in and see if it mounts correctly as read/write.

This worked perfectly. There were files on my device that were corrupt, and working with the disk would get crazy with the permission errors in OP's problem. 

I used Ubuntu's disk utility to find the /dev/location and ama7777's advice to repair my mp3 player.

---

