---
title: "Unable to mount"
date: 2009-05-14
forum: General Help
---

### Post by Hate on 2009-05-14
After removing w/o unmount my pendrive (the pc wasn't let me remove that) if I try to plug my pen drive in the usb port in the file browser I see that ubuntu recognize the device but if I click mount I get

```
Unable to mount 8.1 GB Media

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
```

How can I fix this ? (possibly w/o loosing datas...)

---

### Post by KhurramM on 2009-05-14
which format is your pen drive partitioned?

what is the result of:

sudo /sbin/fdisk -l

and

cat /proc/partitions

and

cat /proc/mounts

with pen attaced to the USB port?

---

### Post by Hate on 2009-05-14
sudo /sbin/fdisk -l

(I cut the other devices to avoid useless info)

```
Disk /dev/sdc: 8054 MB, 8054636032 bytes
255 heads, 63 sectors/track, 979 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e7da7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         979     7863786    7  HPFS/NTFS

```


cat /proc/partitions

```
major minor  #blocks  name

   8        0  312571224 sda
   8        1  308022246 sda1
   8        2          1 sda2
   8        5    4546363 sda5
   8       16  732574584 sdb
   8       17  732572001 sdb1
   8       32    7865855 sdc
   8       33    7863786 sdc1

```

cat /proc/mounts
```
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw,mode=755 0 0
/dev/disk/by-uuid/39f2dec9-1df3-44f5-842c-a5e9b1b749f5 / ext3 rw,relatime,errors=remount-ro,data=ordered 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=755 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
varrun /var/run tmpfs rw,nosuid,mode=755 0 0
varlock /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,nosuid,noexec,gid=5,mode=620 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec 0 0
gvfs-fuse-daemon /home/hate/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user_id=1000,group_id=1000 0 0
/dev/sdb1 /media/OneTouch4 fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096 0 0

```

It's a Sandisk Cruzer micro 8Gb (I've removed the U3 software with a tool)

---

### Post by KhurramM on 2009-05-14
I think where the problem is.

You musnt use the ntfs

It has caused many people many problems.

Boot into your win OS

Reformat it to FAT32

FAT32 has very no errors as compared to daily headaches of ntfs.

Hope u can go ahead now.

Adios~~~~~~~

---

### Post by Hate on 2009-05-14
is there any way to recover the files on the pendrive  before format ?

---

### Post by KhurramM on 2009-05-14
In windows, if it mounts, u can recover the data before formatting. It will mount Insha-Allah, dont worry.

Dont forget to backup..... Just in case ;)


Enjoy Linux.............

---

### Post by mechdave on 2009-05-14
NTFS is supported by the Linux kernel, I would suggest NOT to format it to FAT32 for a start. Secondly can you please post the last 20 or so lines of dmesg after you plug in the drive so we can see what is happening with the drive? Thirdly have you tried manually mounting the drive with mount? eg: sudo mount -t ntfs /dev/sdc1 /mnt

---

### Post by hobo14 on 2009-05-14
Try force mounting and unmounting through the terminal.  That usually fixes it for me:

mkdir /media/tempdisk
sudo mount /dev/sdc1 /media/tempdisk -o force
sudo umount /dev/sdc1

After this, the next time you plug it in it should be ok again.

---

