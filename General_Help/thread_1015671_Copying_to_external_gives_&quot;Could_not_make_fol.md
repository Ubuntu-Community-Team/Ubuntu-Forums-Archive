---
title: "Copying to external gives &quot;Could not make folder&quot;"
date: 2008-12-19
forum: General Help
---

### Post by zephyrus17 on 2008-12-19
I just bought an external and quick formatted it in XP to NTFS. I'm trying to copy stuff inside, but it just gives "Could not make folder /media/Bakura/Cambodia Photos."

I'm using dolphin. I have ntfs-3g and stuff, because I could read/write my other external from gnome/nautilus.

I've tried ```
 sudo chown gary:gary -R /media/Bakura
``` but that just gives me "invalid group: 'gary:gary'. I think it's possible due me using Arch.

So, how?

---

### Post by dcstar on 2008-12-20
> **zephyrus17 said:**
> I just bought an external and quick formatted it in XP to NTFS. I'm trying to copy stuff inside, but it just gives "Could not make folder /media/Bakura/Cambodia Photos."
......

```
ls -al /media
```

---

### Post by zephyrus17 on 2008-12-20
I see what you're getting at.

It came out with:
drwx------  1 gary root 4096 2008-12-18 12:04 Arda-2

I did a:
sudo chmod 777 /media/Arda-2

and now it's:
drwxrwxrwx  1 gary root 4096 2008-12-18 12:04 Arda-2

But it still gives me "Could not make folder", and in Dolphin, the permissions are still:
Can View & Modify Content
Forbidden
Forbidden

---

### Post by caljohnsmith on 2008-12-20
Are you mounting Arda-2 as read-write or just read-only? And are you manually mounting it or is it done in your fstab? If you have Arda-2 being mounted automatically on start up with your fstab, please post the contents:
```
cat /etc/fstab
```

---

### Post by zephyrus17 on 2008-12-20
```
#
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0


/dev/cdrom /media/cdrom   auto    ro,user,noauto,unhide   0      0
/dev/dvd /media/dvd   auto    ro,user,noauto,unhide   0      0
UUID=200c4f2c-35a4-41ef-8e4d-532932a95439 / ext3 defaults 0 1
UUID=2f0520a1-eff7-46b8-b32e-fa7f273732e0 /home ext3 defaults 0 1
UUID=5d2b8630-bc4e-4b37-97a3-0cd8d09231f0 swap swap defaults 0 0
```

All along I've just plugged it in, then nautilus would automatically open it and I'll use it like that. That was with gnome, though.

So, what's the next step?

---

### Post by caljohnsmith on 2008-12-20
OK, so Arda-2 is not being automatically mounted on start up I see. How about posting:
```
sudo fdisk -lu
```
And for whichever partition sdXY is being mounted on Arda-2, try doing:
```
sudo umount /dev/sdXY
sudo mount -w /dev/sdXY /media/Arda-2
ls -l /media
mkdir /media/Arda-2/test_folder
ls -l /media/Arda-2/
whoami
```
And please post the output.

---

### Post by zephyrus17 on 2008-12-20
```
sudo fdisk -lu
```
gives
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xed1f86f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    19535039     9767488+  83  Linux
/dev/sda2        19535040    23535224     2000092+  82  Linux swap / Solaris
/dev/sda3        23535225   230018669   103241722+  83  Linux
/dev/sda4   *   230018670   312576704    41279017+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS
```


```
sudo umount /dev/sdXY
```is ok, but
```
sudo mount -w /dev/sdb1 /media/Arda-2
```
gives "mount: mount point /media/Arda-2 does not exist"

---

### Post by unutbu on 2008-12-20
Please post the output of these commands:
```
df /media/Arda-2
mount

```

---

### Post by caljohnsmith on 2008-12-20
OK, my mistake, I think I see where the problem is now. How about doing:
```
sudo mkdir /media/Bakura
sudo mount /dev/sdb1 /media/Bakura
dolphin /media/Bakura
```
And then try again to make a folder in /media/Bakura.

---

### Post by zephyrus17 on 2008-12-20
> **unutbu said:**
> Please post the output of these commands:
```
df /media/Arda-2
mount

```

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb1            312568640 187463384 125105256  60% /media/Arda-2
```

> **caljohnsmith said:**
> OK, my mistake, I think I see where the problem is now. How about doing:
```
sudo mkdir /media/Bakura
sudo mount /dev/sdb1 /media/Bakura
dolphin /media/Bakura
```
And then try again to make a folder in /media/Bakura.

Since I'm using my other drive, I'll replace "Bakura" with "Arda-2".

It all worked out until I got to "dolphin /media/Arda-2" where the poor dolphin just said "Could not enter folder /media/Arda-2" and there were no visible files/folders

---

### Post by caljohnsmith on 2008-12-20
Please also post the "mount" command output that Unutbu asked for so we can see if sdb1 mounted on /media/Arda-2 has read-write permissions.

---

### Post by zephyrus17 on 2008-12-20
> **caljohnsmith said:**
> Please also post the "mount" command output that Unutbu asked for so we can see if sdb1 mounted on /media/Arda-2 has read-write permissions.

```
/dev/sda1 on / type ext3 (rw)
none on /dev type ramfs (rw)
none on /proc type proc (rw)
none on /sys type sysfs (rw)
none on /dev/pts type devpts (rw)
none on /dev/shm type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw)
/dev/sdb1 on /media/Arda-2 type ntfs (rw)
/dev/sda4 on /media/disk type ntfs (rw,nosuid,nodev,uid=1000,utf8)
```

---

### Post by caljohnsmith on 2008-12-20
OK, so sdb1 is mounted as read-writable. How about trying:
```
mkdir /media/Arda-2/test_folder
ls -l /media /media/Arda-2
```

---

### Post by zephyrus17 on 2008-12-20
> **caljohnsmith said:**
> OK, so sdb1 is mounted as read-writable. How about trying:
```
mkdir /media/Arda-2/test_folder
ls -l /media /media/Arda-2
```

"mkdir: cannot create directory `/media/Arda-2/test_folder': Permission denied"

Could this be due to the fact that I'm using Arch and something's quirky somewhere? But, I could do this all right in GNOME. Hmm...

---

### Post by unutbu on 2008-12-20
What is the proper way to issue commands with root privileges in Arch? Is it su? If so, what is the output of
```

whoami
su
whoami
mkdir /media/Arda-2/test_folder
ls -l /media /media/Arda-2
```

---

### Post by zephyrus17 on 2008-12-20
> **unutbu said:**
> What is the proper way to issue commands with root privileges in Arch? Is it su? If so, what is the output of
```

whoami
su
whoami
mkdir /media/Arda-2/test_folder
ls -l /media /media/Arda-2
```

I install sudo, since I came from Ubuntu. Old habits die hard. (And now, GNOME is beckoning me more and more.)

```
sudo mkdir /media/Arda-2/test_folder
```gives```
mkdir: cannot create directory `/media/Arda-2/test_folder': Operation not permitted

```
This is unbelievably odd. How do I check what groups I'm in?

---

