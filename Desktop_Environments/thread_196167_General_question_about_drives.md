---
title: "General question about drives"
date: 2006-06-13
forum: Desktop Environments
---

### Post by digimars on 2006-06-13
I have a RAID 1 SATA setup for my Windows install.  In Linux, it shows up on my desktop as sda1, sdb1 (correctly mirroring each other's contents). What I would like to do is only have 1 icon on my desktop (instead of 2) and rename it to Windows.

What file do I need to edit in order to accomplish that?

---

### Post by enopepsoo on 2006-06-13
[QUOTE=digimars]I have a RAID 1 SATA setup for my Windows install.  In Linux, it shows up on my desktop as sda1, sdb1 (correctly mirroring each other's contents). What I would like to do is only have 1 icon on my desktop (instead of 2) and rename it to Windows.

What file do I need to edit in order to accomplish that?[/QUOTE]

What file system do you have on your windows partition?

---

### Post by mlind on 2006-06-13
To rename a partition, see if this helps
[https://wiki.ubuntu.com/RenameUSBDrive](https://wiki.ubuntu.com/RenameUSBDrive)

For removing only one removable drive (hdd) from gnome's desktop,
I guess you have to remove mount point from /media and place it somewhere else
like on /mnt/

To prevent removable drive icons appearing on desktop, open gconf-editor
and untick "/apps/nautilus/desktop/volumes_visible" checkbox

---

### Post by digimars on 2006-06-13
[QUOTE=enopepsoo]What file system do you have on your windows partition?[/QUOTE]

It's NTFS.

I'll have a look at that link. Thanks.

Update:
OK, checked out the wiki page, but I have a question.  Where it says to do this: 'sudo ntfslabel /dev/sda1 newlabel', which label do I rename?

```

/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb1 on /media/sdb1 type ntfs (rw,nls=utf8,umask=007,gid=46)

```

Do I relable /dev/sda1 or /media/sda1?

---

### Post by Fatjoint on 2006-06-13
[QUOTE=digimars]I have a RAID 1 SATA setup for my Windows install.  In Linux, it shows up on my desktop as sda1, sdb1 (correctly mirroring each other's contents). What I would like to do is only have 1 icon on my desktop (instead of 2) and rename it to Windows.

What file do I need to edit in order to accomplish that?[/QUOTE]


You have these mounted in Linux as a RAID volume, or do you just have both hdd's mounted?

---

### Post by digimars on 2006-06-13
[QUOTE=Fatjoint]You have these mounted in Linux as a RAID volume, or do you just have both hdd's mounted?[/QUOTE]

In Windows, they are recognized as a single drive, but in Linux they show up as two separate mounted HDD"s.

---

### Post by mlind on 2006-06-13
[QUOTE=digimars]
Do I relable /dev/sda1 or /media/sda1?[/QUOTE]

Those are basically the same, but you should assign commands to the actual
physical device which is /dev/sda1. /media/sda1 is only mount point for it.

---

### Post by Fatjoint on 2006-06-13
[QUOTE=digimars]In Windows, they are recognized as a single drive, but in Linux they show up as two separate mounted HDD"s.[/QUOTE]

You're entering another realm here then... hehe

What I suspect that you are looking for is mounting your NTFS volumes as a RAID volume in Linux ALSO.  I'm not so sure you want to do that, or at least you shouldn't care about the contents of them during your experimentation.

If it were me, I would unmount them both so as to not write to them while booted in Linux.

I'm suspecting if you write to one of the volumes and then boot into windows you'll see that your mirrored raid is broken and you'll need to set it up again.

Unless I'm reading this wrong - You have these drives set up mirrored in windows, but just mounted in Linux - NOT mirrored.

---

### Post by digimars on 2006-06-13
[QUOTE=Fatjoint]You're entering another realm here then... hehe

What I suspect that you are looking for is mounting your NTFS volumes as a RAID volume in Linux ALSO.  I'm not so sure you want to do that, or at least you shouldn't care about the contents of them during your experimentation.

If it were me, I would unmount them both so as to not write to them while booted in Linux.

I'm suspecting if you write to one of the volumes and then boot into windows you'll see that your mirrored raid is broken and you'll need to set it up again.

Unless I'm reading this wrong - You have these drives set up mirrored in windows, but just mounted in Linux - NOT mirrored.[/QUOTE]


Correct, they are just mounted in Linux.  I have no desire to write to them.  I just want to read from them.  What I was getting at is that they both contain the same contents.  I don't want two hard drive icons on my desktop that have the same thing.  I just want to remove one of the icons from my desktop, have it say 'Windows' instead of sda1, and yet still read from the one that's left on there.

---

### Post by Fatjoint on 2006-06-13
[QUOTE=digimars]Correct, they are just mounted in Linux.  I have no desire to write to them.  I just want to read from them.  What I was getting at is that they both contain the same contents.  I don't want two hard drive icons on my desktop that have the same thing.  I just want to remove one of the icons from my desktop, have it say 'Windows' instead of sda1, and yet still read from the one that's left on there.[/QUOTE]

You would want to edit your /etc/fstab file and remove one of the entries to reduce them down to one drive.  That will give you the read access to one of the drives and as long as you don't write to it you should be fine still with your windows mirror.

Your remaining drive you'll want to create a new directory under /media named windows.  Then change your fstab to point to that as your mount point and reboot.

Make sure either before the boot or after to do a **sudo chmod 444 windows** afterwards to give owner r group r and others r

---

### Post by mlind on 2006-06-13
[QUOTE=Fatjoint]You would want to edit your /etc/fstab file and remove one of the entries to reduce them down to one drive.  That will give you the read access to one of the drives and as long as you don't write to it you should be fine still with your windows mirror.[/QUOTE]

if you don't want to mount partition on linux, which means reading its contents,
just remove it from /etc/fstab like Fatjoint said.

[QUOTE=Fatjoint]
Make sure either before the boot or after to do a sudo chmod 444 windows afterwards to give owner r group r and others r
[/quote]

nope, you don't assign chmod to any mounted foreign filesystems, you define access
permissions using umask. Procedure is described on [https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

---

### Post by digimars on 2006-06-13
Got it working!  Thanks for the help everyone!

---

### Post by Fatjoint on 2006-06-13
[QUOTE=mlind]if you don't want to mount partition on linux, which means reading its contents,
just remove it from /etc/fstab like Fatjoint said.



nope, you don't assign chmod to any mounted foreign filesystems, you define access
permissions using umask.[/QUOTE]

:oops: you are absolutely correct.

---

