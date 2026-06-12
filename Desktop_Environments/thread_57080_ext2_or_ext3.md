---
title: "ext2 or ext3?"
date: 2005-08-15
forum: Desktop Environments
---

### Post by xmastree on 2005-08-15
Which is it?

Every 30 bootups, hdb1 is fdisked. This time it failed.  :neutral: 
The system advised me to run fdisk manually, I wasn't comfortable doing this from a console, and wanted to read up a little first so I booted from the live CD to rtfm.

Once I was ready, I did ```
sudo fdisk /dev/hdb1
```and it started by saying ext2 system found, and repaired it, prompting me all the way.

After that it booted up just fine, but I'm left wondering.

/etc/fstab says:
```
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
```
mount says:
```

chris@ubuntu:~$ mount
/dev/hdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/hda5 on /mnt/windisk type ntfs (rw,umask=0222)
/dev/hdb3 on /mnt/shared type vfat (rw,umask=0000)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
chris@ubuntu:~$
```

So which is it? ext2 or 3?

I know why it happened. The drive is on a removable caddy (that's why it's hdb) and I think there's a bad connection somewhere. Every so often it will clunk like the power went off, then the system will need a reboot. Not a good setup, and one which I plan to change sometime soon.

Strange thing is, it seemed to be working but CDs wouldn't automount, or manually either. I booted into Windows to check the hardware, which was fine, then rebooted into linux and it puked.  :-?

---

### Post by heimo on 2005-08-15
It's ext3. The program it asked you to run is probably fsck, not fdisk. ext2 is very similar to ext3 and you can convert ext2 to ext3 and mount ext3 as ext2. If I were you, I would now go back to Live CD and run /sbin/fsck.ext3 on that system - OR mount that file system as an ext2 and convert to ext3. I don't know for sure, but your file system may now be in inconsistent state. However, it's probably just fine as is. :)


ext2 + journaling is basicly ext3

---

### Post by xmastree on 2005-08-15
Yeah, it was fsck...  :roll: Don't know where I got fdisk from... 

So, when fsck claimed it had found an ext2 partition, was it wrong? Or is it similar enough?

It seems fine now, at least until it clunks again. must fix that. :eek:

---

### Post by heimo on 2005-08-15
Don't know why it behaves like that. When you next time need to run it, use /sbin/fsck.ext3 - that should work best.

---

### Post by matthew on 2005-08-15
[QUOTE=xmastree]Yeah, it was fsck...  :roll: Don't know where I got fdisk from... 

So, when fsck claimed it had found an ext2 partition, was it wrong? Or is it similar enough?[/QUOTE]
Truth be told, ext2 and ext3 are identical and interchangable with only one exception. ext3 is an ext2 filesystem that is journaled for better/faster/easier recovery in the event of a problem. So when fsck said it found an ext2 filesystem it was telling the truth...you have an ext2 filesystem with journaling added. 

There are technical reasons for leaving the naming as it is in fsck and other places even though it can cause a bit of confusion. There were discussions about whether to just continue to call what is now ext3, ext2 with journaling. That sort of information and history can be found in greater detail if you are interested with a bit of google-searching. I just thought I would try to give a simple, quick answer to your question...my wife says I tend to answer questions people aren't asking so I will stop now.  :)

---

### Post by matthew on 2005-08-17
While doing some unrelated research I found an excerpted chapter from an O'Reilly book on the publisher's web site that specifically relates to this topic--the ext2 and ext3 filesystems. Here is a link for anyone that might want to read/know more.

[http://www.oreilly.com/catalog/linuxkernel2/chapter/ch17.pdf](http://www.oreilly.com/catalog/linuxkernel2/chapter/ch17.pdf)

Hope someone finds that interesting.

EDIT: Page 600 directly relates to this discussion as it begins to discuss ext3 (don't worry the linked pdf is only 36 pages as it is only one chapter of a long book.)

---

