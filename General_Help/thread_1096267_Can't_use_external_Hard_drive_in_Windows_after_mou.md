---
title: "Can't use external Hard drive in Windows after mounting in Ubuntu"
date: 2009-03-14
forum: General Help
---

### Post by -LOC- on 2009-03-14
I can no longer access my external hard drive in Windows after I mounted it to an Ubuntu install.  I have no clue what's wrong.  It mounted fine in Windows, but I wanted a file off of my Linux box so I removed it (safely) from Windows and mounted it without error in Ubuntu.  I transfered the files I needed successfully, and then unmounted it.  I then tried to acces the drive in Windows and found I could no longer use it.  It's a 1 Terrabyte drive formatted to the NTFS.  I've never had issues with it in Windows before.  This is the first time I mounted it on a Linux distro.  I should note that Ubuntu can still use the drive fine, but for work I NEED it to work in Windows Vista.

If anyone out there can help... I'll gladly give you some :popcorn:

-LOC-

PS. The :popcorn: is a lie.

---

### Post by taurus on 2009-03-14
What's the output of this command in Ubuntu, assuming you have plugged in that external drive first?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by -LOC- on 2009-03-14
I can't run that command at the momment as I came to a netCafe to use the internets to try and find a solution and my Linux computer is at home.  I've tried Google and then I thought about this forum.  Sorry, I should have mentioned that in my first post.

---

### Post by -LOC- on 2009-03-20
> **taurus said:**
> What's the output of this command in Ubuntu, assuming you have plugged in that external drive first?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

I finally got this information, please do try to help.  I'm sorry for not being able to get it sooner!

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6860e0c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1275       33934   262327148+   7  HPFS/NTFS
/dev/sda3           33935       38913    39993817+   5  Extended
/dev/sda5           33935       33995      489951   82  Linux swap / Solaris
/dev/sda6           33996       38913    39503803+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121601   976760001    7  HPFS/NTFS
```

---

### Post by taurus on 2009-03-20
> **-LOC- said:**
> I finally got this information, please do try to help.  I'm sorry for not being able to get it sooner!

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6860e0c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1275       33934   262327148+   7  HPFS/NTFS
/dev/sda3           33935       38913    39993817+   5  Extended
/dev/sda5           33935       33995      489951   82  Linux swap / Solaris
/dev/sda6           33996       38913    39503803+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      121601   976760001    7  HPFS/NTFS
```

What happens when you try to mount /dev/sdb1 by hand?

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by fieroboom on 2009-03-20
> **taurus said:**
> What happens when you try to mount /dev/sdb1 by hand?

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

OP said he/she can't mount it in *Windows...*

-LOC-, Did you unmount the drive before you unplugged it? You should always do that... It's equivalent to the "Safely remove hardware" item in Windows, and it allows the drive to finish writing, empty trash, etc.
Plug it back into the Ubuntu box, and see if it remounts automatically. If not, you might need to force mount it, or you can reboot if you like, but whatever the case, get it mounted in Ubuntu again, then unmount it, unplug it, and try again in Windows. (in that order...)
:D
-Paul

---

### Post by -LOC- on 2009-03-20
Yeah, I unmounted it in Linux.  I can still use the drive in Ubuntu just like it's supposed to.  It works fine.  But Windows cannot see it.  When I run CHKDSK on it in Windows, it reads the file system as NTFS like it should with no error in the fileing system.  Nothing negative is reported in Vista or Ubuntu.  However in the change the drive letter gui tool in Vista, it shows the filing system as RAW.  Ubuntu shows the file system as NTFS.

Lately, I've been using it with Windows by loging into Ubuntu, mounting it, copying the files I need to my Windows part and then restarting into Vista.  This isn't the best soultion.

I've tried everything short of reformatting it in Windows to NTFS.  It's a 1 TB and is nearly full.  I SO do not want to reformat it!  Maybe, if you all don't have any options for me, I can possibly use this problem to move my company closer to Linux as my boss would have to pay me to do the reformat and he doesn't want to do that either.  :-D I guess there's a silver lining to grey clouds.  Still, the best outcome would be to get it back working in Windows.

---

