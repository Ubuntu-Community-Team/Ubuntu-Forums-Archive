---
title: "Unable to transfer files to internal media"
date: 2009-06-01
forum: General Help
---

### Post by talava on 2009-06-01
Hey there!

I've been struggling to fix my Fstab since I last modified it to automount my internal drives. The problem is that I now can't write anything to two of my internal disks.

Here's my fstab:
```
proc            /proc           proc    defaults        0       0

UUID=a14c5a4a-cec2-4b88-84d5-650e24b29b2e / ext3 relatime,errors=remount-ro   0    1

UUID=bcf8fe0c-90c8-4762-a496-f017c0595176 none    swap    sw   0       0

UUID=471B-B043 /media/Iso    vfat    defaults   0   0

UUID=4931-4134 /media/Pieni    vfat    defaults   0   0
```

The last two are the ones causing problems. When I try to transfer anything to either of those, I get the message "Error opening file '/media/Iso/textfile.odt': Permission denied"


Any help is appreciated!

---

### Post by Legace on 2009-06-01
Terve :)

Try something like this:
```
UUID=471B-B043 /media/Iso    vfat    nodev,noexec,nosuid,gid=fat32,umask=007    0       0

UUID=4931-4134 /media/Pieni    vfat    nodev,noexec,nosuid,gid=fat32,umask=007    0       0
```

Note, make sure the UUID values are correct. (To get UUID, type in **blkid** in Terminal)

---

### Post by drs305 on 2009-06-01
You could also make yourself the owner of the files by adding this to the default options to make the previous entry look like this:

> nodev,noexec,nosuid,gid=fat32,**uid=1000,**umask=007

This addition assumes you are the first user with an ID of 1000. You can check by running "id" in a terminal, which will display your uid number. If it is different (1001, 1002, etc), make the appropriate change to the above entry.

---

### Post by talava on 2009-06-01
Thanks, but still having the same problems. After the latest id-permission fix, both disks are unmountable via gnome.

What now? Anyone? I assumed all this needed was a simple fix... :)

---

### Post by drs305 on 2009-06-01
Sorry you are still having problems. Let's get back to basics. Please post the following:
```

sudo blkid -c /dev/null  # gives us UUIDs should we use them in fstab
sudo fdisk -l            # Lowercase L, shows us what the system found for devices/partitions
mount                    # tells us where and what is currently mounted
ls -la /media            # shows us the permissions of /media folders

```

---

### Post by talava on 2009-06-02
```

sudo blkid -c /dev/null # gives us UUIDs should we use them in fstab

```

The UUIDs are checked and double-checked. so I'll save some space here.

```

sudo fdisk -l       # Lowercase L, shows us what the system found for devices/partitions

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x229b31da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  17  Hidden HPFS/NTFS
**/dev/sda2            1275        4314    24414062+   b  W95 FAT32**
/dev/sda3   *        4315        6022    13719510   83  Linux
/dev/sda4            6023       19457   107916637+   5  Extended
**/dev/sda5            6381       19457   105040971    b  W95 FAT32**
/dev/sda6            6023        6380     2875572   82  Linux swap / Solaris


```

mount             # tells us where and what is currently mounted

```

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/USER1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=USER1)


```

ls -la /media     # shows us the permissions of /media folders

```

total 24
drwxr-xr-x  6 root root 4096 2009-06-02 10:14 .
drwxr-xr-x 21 root root 4096 2009-05-14 08:54 ..
lrwxrwxrwx  1 root root    6 2009-05-08 21:03 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-05-08 21:03 cdrom0
drwxr-xr-x  2 root root 4096 2009-05-08 21:03 cdrom1
-rw-r--r--  1 root root    0 2009-06-02 10:14 .hal-mtab
[B]drwxr-xr-x  2 root root 4096 2009-05-09 18:22 Iso
drwxr-xr-x  2 root root 4096 2009-05-09 18:23 Pieni[/B]

---

### Post by dcstar on 2009-06-02
> **talava said:**
> Hey there!

I've been struggling to fix my Fstab since I last modified it to automount my internal drives.
..........
Any help is appreciated!

Do not stuff around with your fstab file, just install the **pysdm** package and let it set things up correctly.

---

### Post by talava on 2009-06-02
What a great application! Thanks for the advice.

This was easily better than MountManager, which I have tested in earlier versions.

---

### Post by drs305 on 2009-06-02
> **dcstar said:**
> Do not stuff around with your fstab file, just install the **pysdm** package and let it set things up correctly.

> 
What a great application! Thanks for the advice.


I wrote a tutorial on pysdm a while ago. Over time I felt the package left a lot to be desired (no UUIDs, etc). Guess it's time I go back and update the guide and return it to my signature line!

---

