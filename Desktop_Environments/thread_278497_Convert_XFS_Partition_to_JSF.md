---
title: "Convert XFS Partition to JSF"
date: 2006-10-16
forum: Desktop Environments
---

### Post by john_markh on 2006-10-16
Hi,
I used XFS as my /root and /home partitions. Now, I want to convert it to JSF because XFS uses too much CPU (and the performances are not too great).
Is there a way to do it ?

---

### Post by K.Mandla on 2006-10-16
There is a way to do it, and the best instructions I've seen were here. ...

[http://gentoo-wiki.com/HOWTO_Convert_Filesystems](http://gentoo-wiki.com/HOWTO_Convert_Filesystems)

In Ubuntu terms, you would ...
[LIST=1]
[*]Back up everything, just to be safe
[*]Reboot to a live CD (I'd use a Dapper live CD if you can, but I don't think it matters)
[*]Enable the universe repository (I forget if it's enabled by default in the live CD environment)
[*]Install convertfs: *sudo aptitude install convertfs*
[*]Convert the file system: *sudo convertfs /dev/hdXY xfs jfs*
[*]Check the file system: *sudo fsck.jfs /dev/hdXY*
[*]Edit your fstab file to show /dev/hdXY is jfs ... you'll have to mount the hard drive to access that file
[/LIST]
It's not quick or easy, but it's not impossible. Let us know if you run into problems. :D Good luck!

---

### Post by jdong on 2006-10-16
BIG WARNING:

The 7 times I've used convertfs, it has consistently corrupted the filesystem just a few steps into the conversion process. I don't recommend this tool in any way, and suggest copying the files somewhere else, formatting, then restoring as the one and only safe way of converting filesystems.

---

### Post by john_markh on 2006-10-16
I heard "bad" things about convertfs.
Did any have "success" stories ?

---

### Post by kansei on 2007-09-12
*bump* to the future!

I'm converting a reiserfs partition (980GB of drive space .. it's 1.5TB of drives in a RAID5, I think the partition is ~900GB) to JFS without doing any backups as we speak. I'm doing it with the OS online because it's just a /storage partition that I use for mythtv and movie storage. The mythtv recording data can get lost and it won't end the world, and the movies are all stored on other computers in the house anyway :P

convertfs, give me your worst!

p.s. I'm running it all over an ssh connection because I didn't feel like going into the basement to issue the commands directly to the server.

so far it seems to be doing well

== Creating clone of `reiserfs' filesystem that's on `/dev/sda5'. ==
===== Creating destination `jfs' filesystem. =====
mkfs.jfs version 1.1.11, 05-Jun-2006
   \

Format completed successfully.

913953880 kilobytes total disk space.
============== Copying files ==============

I had to modprobe jfs and loop to get convertfs working. I added jfs to /etc/modules

I'm sad that JFS is a module and not built in :(

edit: it broke

============== Copying files ==============
ls: /tmp/convertfs/fs2root: No such file or directory
df: `/tmp/convertfs/fs2root': No such file or directory
umount: /dev/loop7: not mounted


but I could just 'sudo mount -a' and the old partition (reiserfs) was still there. About 280GB of data was lost though (my music collection in FLAC.. no biggie, I just put it on there earlier today).

---

### Post by jdong on 2007-09-12
aah, it's alive from the dead!

I think I said this before a year ago, but I've never actually had that tool work for me.

---

### Post by kansei on 2007-09-13
^^ saw that, but sometimes you need the personal feeling of losing hundreds of gigs of data (yay having that data on another computer.. it would take me weeks to re-rip my music collection) to know for sure :)

Plus now there's actual evidence of the failure :)

---

### Post by jdong on 2007-09-13
lol, I'm that type of person too :)

---

