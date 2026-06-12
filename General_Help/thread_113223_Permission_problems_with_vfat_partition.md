---
title: "Permission problems with vfat partition"
date: 2006-01-05
forum: General Help
---

### Post by bwaskiew on 2006-01-05
I have a dual boot system set up with Windows XP and Ubuntu each on their own partition, and a shared fat32 / vfat partition that both OSes can access. The only problem is I can only move stuff onto that partition if I use sudo, or run nautilus as root. I checked my fstab and it is on default, which should have the rw and user options, and even if it didn't I tried doing that manually, but I still couldn't write to the vfat partition. Anyone got any ideas what I'm doing wrong?

Thanks,
Brandon

---

### Post by aysiu on 2006-01-05
[QUOTE=bwaskiew]I checked my fstab and it is on default, which should have the rw and user options[/QUOTE] Actually, the defaults exclude user read/write. See the fourth link of my sig.

---

### Post by bwaskiew on 2006-01-06
Thank you very much. I got so far as looking at the general options, and the reference I was looking at said rw was the default, but then I looked up the man page and looked at the vfat specific options and saw there was a lot of other options, including the user permissions using the numbers, which I still don't understand how to use yet (both the vfat mount options and chmod permissions and anything like that).

Thank you for the quick help!

---

### Post by bwaskiew on 2006-02-21
Alright, sorry to dredge up an old thread, but I am now having problems with my vfat partition in Linux. It will be read only most of the time, and a few of the times it will be correctly mounted as read/write. The only thing that fixes the problem is rebooting Linux several times. Eventually I will get lucky and it will be mounted correctly. I used the options in /etc/fstab that was recommended in one of the above posts, and just confirmed that it is still that way (and that fstab was not corrupted). Does anyone have any ideas what could be making my shared windows fat32 drive be mounted incorrectly?

Thanks,
Brandon

---

### Post by aysiu on 2006-02-21
Can you post the output of these three separate commands (they should be entered one at a time, which is why they're on separate lines)? ```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by dcstar on 2006-02-22
[QUOTE=aysiu]Can you post the output of these three separate commands (they should be entered one at a time, which is why they're on separate lines)? ```
sudo fdisk -l
cat /etc/fstab
df -h
```[/QUOTE]
Add in the output of "mount" as well.......

---

### Post by bwaskiew on 2006-02-22
```
************* sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/hda2            4865        7235    19045057+  83  Linux
/dev/hda3            7236        7296      489982+  82  Linux swap / Solaris
/dev/hda4            7297        9726    19518975    b  W95 FAT32
************* cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>                      <dump>  <pass>
proc            /proc           proc            defaults                       0       0
/dev/hda2       /               ext3            defaults,errors=remount-ro     0       1
/dev/hda4       /media/shared   vfat            iocharset=utf8,umask=000       0       0
/dev/hda3       none            swap            sw                             0       0
/dev/hdc        /media/cdrom0   udf,iso9660     user,noauto                    0       0
/dev/fd0        /media/floppy0  auto            rw,user,noauto                 0       0
************* df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              18G  2.3G   15G  13% /
tmpfs                 253M     0  253M   0% /dev/shm
tmpfs                 253M   13M  240M   5% /lib/modules/2.6.12-10-386/volatile
/dev/hda4              19G  1.4G   18G   8% /media/shared
************* mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda4 on /media/shared type vfat (rw,iocharset=utf8,umask=000)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
```

As a little extra info, only 2 things I can think of have been different lately. First off, I'm not hooked up on broadband, so I usually end up Ctrl-C-ing the time sychronization at startup. Secondly, right around the time of this error, I  also had problems moving a 50 meg file from a USB Memory key in Linux. It would see the file fine, but could never fully transfer it. Other smaller files transferred fine, and when I tried to transfer the same file on a friend's USB Key, it didn't even auto-mount the key at all.

-Brandon

---

### Post by aysiu on 2006-02-22
Maybe dcstar can see something I can't, but it looks good to me. I don't know what the problem is.

---

### Post by patrickfromspain on 2006-02-22
try this:

/dev/hda4       /media/shared            vfat    rw,iocharset=utf8,user,auto,umask=0             0       0

Works fine to me, although I haven't haven't the iocharset options. What's it for?

---

