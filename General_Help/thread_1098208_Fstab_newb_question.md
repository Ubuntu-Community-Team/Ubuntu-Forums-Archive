---
title: "Fstab newb question"
date: 2009-03-16
forum: General Help
---

### Post by bf109 on 2009-03-16
Very new to Linux here and am trying to figure out how to get a partition that I just recently converted from NTFS to EXT3 to mount automagically at startup mainly so that I can use the 47gb it has free to load some OS's in Virtualbox since my system partition is out of space. I originally installed Ubuntu to this laptop thinking that I wanted to have a dual boot machine between Vista and Ubuntu but then decided to kill Vista. I am very new and have been reading through fstab and mount tutorials but am not really getting anywhere. Can someone in here explain this in newb terms please with all needed mount commands and fstab entries explained? Would be a great help. I have pasted in my fstab and mtab files. Thanks in advance.
fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=839e93bf-30ba-4ddf-86df-ad55d4d49f30 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0a86a971-a14a-4b65-86dd-7dcfd940eb15 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


mtab:

/dev/sda6 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-11-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/scd0 /media/cdrom0 iso9660 rw,nosuid,nodev,utf8,user=me 0 0
/dev/sda1 /media/Recovery fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
gvfs-fuse-daemon /home/me/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=me 0 0
/dev/sda2 /media/47gb ext3 rw 0 0

---

### Post by taurus on 2009-03-16
If you want /dev/sda2 (I assume that is the partition you want) to mount to /media/47gb automatically each time you boot Ubuntu, you can edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda2   /media/47gb   ext3   defaults   0   2
```
Save it.  Now, just to be sure there is /media/47gb directory.

```
ls -la /media
```
If there isn't, then you need to create it.

```
sudo mkdir /media/47gb
```
But if there is, then try to mount /dev/sda2 to that mount point.

```
sudo mount -a
df -h
```

---

### Post by bf109 on 2009-03-16
Dude, you simply rock. Thank you.

---

