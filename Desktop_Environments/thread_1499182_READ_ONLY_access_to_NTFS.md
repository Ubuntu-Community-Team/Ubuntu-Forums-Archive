---
title: "READ ONLY access to NTFS"
date: 2010-06-01
forum: Desktop Environments
---

### Post by cccc on 2010-06-01
hi

I have Ubuntu 10.04 with Gnome and Windows XP on the same machine.
Using Nautilus 2.30.1 I can write into NTFS system partition from windows.
This is very dangerous.
Howto setup just READ ONLY access to NTFS?

---

### Post by pricetech on 2010-06-01
I'm pretty sure you have an entry for it in your fstab file.  Just change that entry to make it read only.

---

### Post by cccc on 2010-06-01
> **pricetech said:**
> I'm pretty sure you have an entry for it in your fstab file.  Just change that entry to make it read only.

No, is not:```

# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=25c4035d-f5a0-4e2b-a1cb-eac4f0f5f2e7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bb88b6df-81a1-42f1-804f-314660f8119b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by John Bean on 2010-06-01
> **cccc said:**
> Using Nautilus 2.30.1 I can write into NTFS system partition from windows.
This is very dangerous.

Why do you think it is dangerous?

---

### Post by Morbius1 on 2010-06-01
I added the following line to my** /etc/fstab** to do what you want:
> UUID=DA9056C19056A3B3 /WinXP  ntfs    defaults,nls=utf8,umask=227,gid=46 0       0Each position in umask represents a type of user: owner - group - others 

A "2" in umask turns off write
A "7" in umask turns off everything
gid=46 represents the group that all local login users are members of by default ( plugdev )

So what all this will do is mount WinXP with read only access to owner ( which is root ) and group ( which is all local login users - including me ) and with no access at all to everyone else.

To find the correct UUID number for your hardware:

```
 sudo blkid -c /dev/null
```BTW, I have NTFS partitions that I allow write access to, but I wouldn't allow a write to my Windows System partition on a drunken bet. Too old school I guess. :wink:

---

### Post by cccc on 2010-08-14
Thx, I've add in /etc/fstab the following line:```

UUID=F004EE0104EDCAA4 /windows ntfs defaults,nls=utf8,umask=0227,gid=46 0       0
```
Normal user cannot write into the mounted windows directory, but if I login as a root then I can write without any problems.
Howto deny write access for the root user?

---

### Post by AndersAA on 2010-08-15
If you check mount after you've got a ntfs drive set up you'll see it uses fuseblk. Which means it uses the fuse ntfs driver, which is a wine hack using windows'es own ntfs driver.

There's no risk in writing to a ntfs partition using microsoft's ntfs driver...

---

### Post by Morbius1 on 2010-08-15
cccc, root on any given linux system has the power of life and death. Even if you set umask to 777 root will still have access. I don't think there's a way to disable that.

AndersAA,
This statement is true:
>  There's no risk in writing to a ntfs partition using microsoft's ntfs driver...     This statement is not:
> Which means it uses the fuse ntfs driver, which is a wine hack using windows'es own ntfs driver.
The fuse part is correct, the "ntfs" filetype is actually a symlink to the ntfs-3g driver, it has nothing to do with wine, and it does not use windows' ntfs driver. A better way to describe ntfs-3g ( although it still may not be accurate ) is that it is a reverse engineered ntfs driver.

---

### Post by cccc on 2010-08-15
**ro** in the fstab entry solved this problem!

---

### Post by Morbius1 on 2010-08-15
> **cccc said:**
> **ro** in the fstab entry solved this problem!
I'll have to remember that. :wink:

---

### Post by AndersAA on 2010-08-15
> **Morbius1 said:**
> cccc, root on any given linux system has the power of life and death. Even if you set umask to 777 root will still have access. I don't think there's a way to disable that.

Through fuse not allowing _other or _root will block root access.

> **Morbius1 said:**
> 
AndersAA,
This statement is true:
This statement is not:
The fuse part is correct, the "ntfs" filetype is actually a symlink to the ntfs-3g driver, it has nothing to do with wine, and it does not use windows' ntfs driver. A better way to describe ntfs-3g ( although it still may not be accurate ) is that it is a reverse engineered ntfs driver.

I haven't looked into it in a long time, but the way it worked before was pulling files from the windows system. Meaning if you had a ntfs drive without windows on it you couldn't get it working.

It could also not be bundled, because that process wasn't automated. You needed to grab the ntfs drivers before you could mount (either from a windows ystem, or using the read only kernel driver to access windows/system32).

---

