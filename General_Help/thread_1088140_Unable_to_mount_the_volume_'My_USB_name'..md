---
title: "Unable to mount the volume 'My USB name'."
date: 2009-03-05
forum: General Help
---

### Post by ATR on 2009-03-05
Hey. So the problem is, my USB memory stick wont mount all of a sudden. I've never had problems until I just turned on the computer now. I plug in the stick and it comes up with this:

Cannot mount volume.
Unable to mount the volume 'MIGHTYDRIVE'.
>Details
LsCallerPriviledged() failed

Then after about 30 seconds this comes up too:

Unable to mount MIGHTYDRIVE
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


(Mightydrive is my USB name)

As far as I know I haven't done anything that would affect the connection to either the computer or the stick.

I would really appreciate swift help on this as I have much work to be doing which is on this stick. So any assistance greatly appreciated.
Thanks :]

---

### Post by taurus on 2009-03-05
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ATR on 2009-03-05
> **taurus said:**
> What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```



This:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1e08c2a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9963    80027766    7  HPFS/NTFS

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xad63d9d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+  83  Linux
/dev/sdb2            1217        7476    50283450    5  Extended
/dev/sdb5            1217        1338      979933+  82  Linux swap / Solaris
/dev/sdb6            1339        7476    49303453+  83  Linux

Disk /dev/sdd: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        1126     3915752    b  W95 FAT32

---

### Post by taurus on 2009-03-05
I assume /dev/sdd1 is the one you want to mount.

```
sudo mkdir /media/sdd1
sudo mount -t vfat /dev/sdd1 /media/sdd1 -o umask=000
df -h
```
And when you are done using it, don't forget to unmount it first before you unplug it from your computer.

```
sudo umount /media/sdd1
df -h
```

---

### Post by ATR on 2009-03-05
> **taurus said:**
> I assume /dev/sdd1 is the one you want to mount.

```
sudo mkdir /media/sdd1
sudo mount -t vfat /dev/sdd1 /media/sdd1 -o umask=000
df -h
```
And when you are done using it, don't forget to unmount it first before you unplug it from your computer.

```
sudo umount /media/sdd1
df -h
```


Okay thank you that works :] Does this mean I'll have to manually mount it from now on?

---

### Post by taurus on 2009-03-05
Hopefully not but at least you now know how.

---

### Post by ATR on 2009-03-05
> **taurus said:**
> Hopefully not but at least you now know how.

It's always the simplest things. Just rebooted and it mounts now. But thank you I'll save those codes for future reference, thank you very much. :]

---

