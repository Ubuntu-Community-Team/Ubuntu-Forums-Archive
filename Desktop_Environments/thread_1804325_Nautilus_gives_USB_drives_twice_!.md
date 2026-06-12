---
title: "Nautilus gives USB drives twice !"
date: 2011-07-14
forum: Desktop Environments
---

### Post by wschulte on 2011-07-14
After setting up a new system with Ubuntu 11.04, I wanted to make 2 USB-disks available to all users. They get automounted from fstab by the next lines:[INDENT]# USB disks ..
LABEL=USB-DRIVE /media/USB-DRIVE  ntfs users,umask=000,rw,auto 0   0
LABEL=SAMSUNG /media/SAMSUNG vfat users,umask=000,rw,auto 0   0
[/INDENT]works fine, seeing all users can r/w the disks and mount gives:[INDENT]root@ubuntu11:/home/manager# mount -l
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0) [ROOT]
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
[U] /dev/sdb1 on /media/USB-DRIVE type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=1024,default_permissions) [USB-DRIVE]
/dev/sdg1 on /media/SAMSUNG type vfat (rw,noexec,nosuid,nodev,umask=000) [SAMSUNG]
[/U]binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/wschulte/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wschulte)
gvfs-fuse-daemon on /home/manager/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=manager)
[/INDENT]but .. nautilus behaves a bit weird: see attached file.
so both USB disks are listed twice: one time with the unmount sign and one time without it ..

What am I doing wrong ?

Willy.

---

### Post by Morbius1 on 2011-07-14
Give this a shot:
Rewrite this:
> LABEL=USB-DRIVE /media/USB-DRIVE  ntfs users,umask=000,rw,auto 0   0
LABEL=SAMSUNG /media/SAMSUNG vfat users,umask=000,rw,auto 0   0To this:
> [COLOR=Blue]**/dev/disk/by-label****/USB-DRIVE**[/COLOR] /media/USB-DRIVE  ntfs users,umask=000,rw,auto 0   0
[COLOR=Blue]**/dev/disk/by-label/SAMSUNG**[/COLOR] /media/SAMSUNG vfat users,umask=000,rw,auto 0   0

---

### Post by wschulte on 2011-07-14
Hi Morbius1,

Well..it worked. Using the device-name:
[INDENT]# USB disks ..
#LABEL=USB-DRIVE /media/USB-DRIVE  ntfs users,umask=000,rw,auto 0   0
/dev/sdb1 /media/USB-DRIVE  ntfs users,umask=000,rw,auto 0   0
#LABEL=SAMSUNG /media/SAMSUNG vfat users,umask=000,rw,auto 0   0
/dev/sdg1 /media/SAMSUNG vfat users,umask=000,rw,auto 0   0
[/INDENT]Using the UUID gave the same result as using the LABEL. Thanks for that 

Thinking about it it isnt that unlogical, but it makes things a bitmore tricky as the drives are removed sometimes. I wonder whether Nautilus has a option to exclude certain devices from auto-mounting in the desktop setting (I do want USB-sticks etc. being automounted off-course).

Anyway, thanks. Willy.

---

