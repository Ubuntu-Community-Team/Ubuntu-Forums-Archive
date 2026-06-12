---
title: "[SOLVED] Mounting an NTFS Partition"
date: 2008-12-07
forum: General Help
---

### Post by Arnitak on 2008-12-07
How do I mount an NTFS Partition always at startup, from which I could read/write also, as a normal non root user?

---

### Post by Rocket2DMn on 2008-12-07
Is the drive internal or external?  Please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
If the drive is external, it should mount automatically, unless it is conflicting with an entry in fstab.

---

### Post by Arnitak on 2008-12-07
> **Rocket2DMn said:**
> Is the drive internal or external?  Please post the output of
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
If the drive is external, it should mount automatically, unless it is conflicting with an entry in fstab.

The drive is internal. It is actually a partition, I got the option to mount it, during the install process, but aparently it would not mount then. This happens only on the alternate install disk. Here is the output:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3441e0a9
```
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       32540   261368828    7  HPFS/NTFS
/dev/sda2           32541       36968    35567910    5  Extended
/dev/sda3           36969       38184     9767520   83  Linux
/dev/sda4           38185       38913     5855692+  82  Linux swap / Solaris
/dev/sda5           32541       36968    35567878+  83  Linux
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=964604c6-2eb7-4d14-8170-c0ab86587ef6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=2dccf234-5013-45a4-a6bf-94c0e0c92c22 /home           ext3    relatime        0       2
# /dev/sda4
UUID=d046e083-0859-4b5f-959c-c7caa1ca2d8f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

```
/dev/sda1: UUID="96783ECF783EAE3D" TYPE="ntfs" 
/dev/sda3: UUID="2dccf234-5013-45a4-a6bf-94c0e0c92c22" TYPE="ext3" 
/dev/sda4: TYPE="swap" UUID="d046e083-0859-4b5f-959c-c7caa1ca2d8f" 
/dev/sda5: UUID="964604c6-2eb7-4d14-8170-c0ab86587ef6" TYPE="ext3" 
```

```
/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jpeter/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jpeter)
```

---

### Post by Rocket2DMn on 2008-12-07
OK, so it's there, but just no entry in fstab, so it should be a quick fix.  First decide on a mount point, let's say, /media/windows
Open fstab for editing
```
gksudo gedit /etc/fstab
```
Now add this line to the bottom:
```
UUID=96783ECF783EAE3D /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
Save and close.  Create the mount point, then mount all:
```
sudo mkdir /media/windows
sudo mount -a
```
The drive should now be mounted and mount automatically on boot.  If for some reason you get errors, please post them back here and include the command you ran.

---

### Post by Arnitak on 2008-12-07
I got the following error, although the partition is not in use!

```
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /windows -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /windows ntfs-3g force 0 0
```

---

### Post by Rocket2DMn on 2008-12-07
I see you want to mount at simply /windows instead of /media/windows or /mnt/windows - this is fine, just isn't really the "best practices" location.
This means that the drive was uncleanly disconnected or shut down.  If this is a dual boot setup, you should reboot into windows then shutdown cleanly - this is the best method.  Alternatively, you can force the mount as it suggested
```
sudo mount -t ntfs-3g /dev/sda1 /windows -o force
```
That is the only time you should have to do it, unless the drive experiences other unclean disconnects.  Otherwise it will mount automatically.

---

### Post by Rocket2DMn on 2008-12-07
I see you want to mount at simply /windows instead of /media/windows or /mnt/windows - this is fine, just isn't really the "best practices" location.
This means that the drive was uncleanly disconnected or shut down.  If this is a dual boot setup, you should reboot into windows then shutdown cleanly - this is the best method.  Alternatively, you can force the mount as it suggested
```
sudo mount -t ntfs-3g /dev/sda1 /windows -o force
```
That is the only time you should have to do it, unless the drive experiences other unclean disconnects.  Otherwise it will mount automatically.

---

### Post by taurus on 2008-12-07
You need to boot into windows again.  Then, run scandisk and/or defrag.  Now, shut it down cleanly and Ubuntu should not have any problem mounting it this time.

---

### Post by Arnitak on 2008-12-07
Thanks, it worked. Problem solved.

---

