---
title: "USB STICK mount problem"
date: 2005-05-15
forum: Desktop Environments
---

### Post by dqsis on 2005-05-15
Hello all!!!

Well, I cannot mount my usb stick. 

1st I edited my /etc/fstab by adding the line:

/dev/sda   /mnt/usb_stick  auto   rw,users,noauto   0   0

and then I gave the command:

root@dk:/home # mount /dev/sda /mnt/usb_stick/

and get the response:

mount: you must specify the filesystem type

Do you know how I can manage to mount my usb stick???

Thanks a million!!!

dqsis

---

### Post by crane on 2005-05-15
[QUOTE=dqsis]Hello all!!!

Well, I cannot mount my usb stick. 

1st I edited my /etc/fstab by adding the line:

/dev/sda   /mnt/usb_stick  auto   rw,users,noauto   0   0

and then I gave the command:

root@dk:/home # mount /dev/sda /mnt/usb_stick/

and get the response:

mount: you must specify the filesystem type

Do you know how I can manage to mount my usb stick???

Thanks a million!!!

dqsis[/QUOTE]

What brand may have something to do with it as well. I have one stick that is a sony memstick and it works fine, My other, a San Disk memorystickPro and it doesn't work!

---

### Post by k.ODOMA on 2005-05-15
[QUOTE=dqsis]Hello all!!!

Well, I cannot mount my usb stick. 

1st I edited my /etc/fstab by adding the line:

/dev/sda   /mnt/usb_stick  auto   rw,users,noauto   0   0

and then I gave the command:

root@dk:/home # mount /dev/sda /mnt/usb_stick/

and get the response:

mount: you must specify the filesystem type

Do you know how I can manage to mount my usb stick???

Thanks a million!!!

dqsis[/QUOTE]

Most usb sticks are formatted with vfat so you'd do:
mount -t vfat /dev/sda /mnt/usb_stick/

---

### Post by alastair on 2005-05-15
Or even use the partition :

/dev/sda1

Check the system logs i.e.

Before plugging it in, open a shell and :

sudo tail -f /var/log/syslog

Plug it in and watch for messages.

Your fstab should be something like (assuming partition 1) :

/dev/sda1 /mnt/usb_stick auto rw,users,noauto 0 0

---

### Post by dqsis on 2005-05-15
May 15 22:42:09 dk usb.agent[9651]:      usb-storage: already loaded
May 15 22:42:09 dk udev[9698]: configured rule in '/etc/udev/rules.d/udev.rules' at line 28 applied, 'sda' becomes '%k'
May 15 22:42:09 dk udev[9698]: creating device node '/dev/sda'
May 15 22:42:09 dk udev[9699]: configured rule in '/etc/udev/rules.d/udev.rules' at line 28 applied, 'sda1' becomes '%k'
May 15 22:42:09 dk udev[9699]: creating device node '/dev/sda1'
May 15 22:42:09 dk kernel: FAT: invalid first entry of FAT (0xfff8 != 0xff00)
May 15 22:42:09 dk kernel: VFS: Can't find a valid FAT filesystem on dev sda1.
May 15 22:42:09 dk kernel: udf: registering filesystem
May 15 22:42:10 dk kernel: UDF-fs: No partition found (1)
May 15 22:42:10 dk kernel: Unable to identify CD-ROM format.
May 15 22:42:10 dk kernel: HFS+-fs: unable to find HFS+ superblock
May 15 22:42:10 dk kernel: VFS: Can't find a HFS filesystem on dev sda1.
May 15 22:42:10 dk kernel: VFS: Can't find ext3 filesystem on dev sda1.
May 15 22:42:10 dk kernel: VFS: Can't find ext2 filesystem on dev sda1.
May 15 22:42:10 dk kernel: ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
May 15 22:42:10 dk kernel: SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
May 15 22:42:10 dk kernel: SGI XFS Quota Management subsystem
May 15 22:42:10 dk kernel: XFS: bad magic number
May 15 22:42:10 dk kernel: XFS: SB validate failed


These are the warnings I get...

It still doesn't work  ](*,) 

Any ideas???

---

### Post by RastaMahata on 2005-05-15
looks to me that ubuntu is unable to recognize the format of your pendrive. :/
> May 15 22:42:09 dk kernel: FAT: invalid first entry of FAT (0xfff8 != 0xff00)
Or that your fat partition is broken somewhere...

---

### Post by alastair on 2005-05-15
OK - the kernel sees /dev/sda. Does it have a FAT filesystem on it?

fdisk -l /dev/sda

There's a problem with the filesystem. Perhaps re-make it (copy data off first on something that can read it).

---

