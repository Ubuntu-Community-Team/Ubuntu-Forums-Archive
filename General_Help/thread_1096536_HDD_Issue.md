---
title: "HDD Issue"
date: 2009-03-15
forum: General Help
---

### Post by iAnth on 2009-03-15
I have been unable to successfully mount my secondary HDD after creating a single patrition using Gparted.  I created a mount point, made it world writable, and put an according entry into the fstab file.

**ls -al /mnt/data**

> total 24
drwxr-xr-x 3 anth root  4096 2009-03-14 21:42 .
drwxr-xr-x 3 anth root  4096 2009-03-14 18:20 ..
-rw-r--r-- 1 anth anth     0 2009-03-14 21:42 frakitgodsdammit
drwx------ 2 anth root 16384 2009-03-13 08:36 lost+found


**cat /etc/fstab**

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7cb2e4ea-409d-4302-b551-3e33025be043 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=52dde0b5-9470-46f7-ba35-f90cb3aeea09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=d80bc230-0427-44c0-a4c3-b448aa8dee4f    /mnt/data    ext3    relatime,errors=remount-ro   0   0


I am able to successfully mount the disk. However, it only doesn't automagically show the mounted disk after reboot.
Any suggestions?

---

### Post by dcstar on 2009-03-15
> **iAnth said:**
> I have been unable to successfully mount my secondary HDD after creating a single patrition using Gparted.  I created a mount point, made it world writable, and put an according entry into the fstab file.
.........
I am able to successfully mount the disk. However, it only doesn't automagically show the mounted disk after reboot.
Any suggestions?

What do you mean "Show"?, not fstab mounted disks "show", they are just there.

---

### Post by userfriendly on 2009-03-15
he tried mounting the disk via an entry in fstab, but it fails, obviously (as opposed to manually mount it, which works).

---

### Post by mrsteveman1 on 2009-03-15
Is the UUID correct? Look in the kernel messages for mount errors, and look in the main syslog for anything else that might give us a clue

---

### Post by iAnth on 2009-03-15
Yes, the UUID is correct.

---

### Post by miegiel on 2009-03-15
Do you get any errors when you do```
sudo mount -a
```

---

### Post by iAnth on 2009-03-15
I get the following errors when I input **sudo mount -a**:

> [mntent]: line 4 in /etc/fstab is bad
[mntent]: line 6 in /etc/fstab is bad
[mntent]: line 8 in /etc/fstab is bad
[mntent]: line 9 in /etc/fstab is bad


---

### Post by miegiel on 2009-03-15
> **iAnth said:**
> I get the following errors when I input **sudo mount -a**:

There must be something wrong with those lines, I can't see what though.

---

### Post by iAnth on 2009-03-15
That's what I gathered when I ran **sudo mount -a**. Thanks for the suggestion though miegiel!

---

### Post by iAnth on 2009-03-15
Bump.

---

### Post by Hobgoblin on 2009-03-15
Is this a USB drive?

---

### Post by miegiel on 2009-03-15
```
ls -l /dev/disk/by-uuid
```
Gives the UUIDs of your partitions. Make sure the UUIDs in /etc/fstab are exactly the same.

---

### Post by iAnth on 2009-03-16
@ Hobgoblin: No, internal drive.

@ miegiel: The UUIDs are the exact same.

---

### Post by mrsteveman1 on 2009-03-16
If we go by number, the lines it listed as being bad listed everyone except for this 2nd hard drive.

Delete that fstab line entirely and start over, perhaps use the device name directly for now for testing. Also remove all mount options except "defaults".

---

### Post by userfriendly on 2009-03-16
we tried it with the device name first. no joy. and the line is the only one we added, the other four lines were in there after a fresh ubuntu install.

i'm kinda wondering why he seems to have to go to such lengths anyway. in my machine, ubuntu "recognised" the second hard drive without me having to do any of this, i never touched my fstab at all.

---

### Post by iAnth on 2009-03-16
The problem has been fixed.

 Thank you.

---

