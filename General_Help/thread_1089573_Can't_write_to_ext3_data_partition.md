---
title: "Can't write to ext3 data partition"
date: 2009-03-07
forum: General Help
---

### Post by nemarona on 2009-03-07
Hi all

When installing Kubuntu 8.10 a couple of days ago, I created a data partition (ext3, /dev/sda10) to be mounted on /media/bodega (that's Spanish for "storage place"). However, for some reason I can't write to it. Here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=92653652-e113-4c86-84dc-57c0346f1fb4 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
UUID=955b076a-3e99-4033-914d-a711ff3f73e4 /media/bodega   ext3    relatime,noexec        0       2
# /dev/sda2
UUID=0A36FE5336FE3EEF /media/recovery ntfs-3g    auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8 0       1
# /dev/sda3
UUID=B0AE0127AE00E7A4 /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=0e03ff07-829a-463c-ad1d-25803922fab6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
Any ideas? Thanks in advance!

---

### Post by hexanol on 2009-03-07
What's the output of "mount". And when you say you can't write to it, what do you mean exactly (what kind of error message are you getting?). You can read from but can't write ?

---

### Post by nemarona on 2009-03-07
Thanks for the reply. Here's the ouput of mount:
```
~$ mount
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda10 on /media/bodega type ext3 (rw,noexec,nosuid,nodev,relatime)
/dev/sda2 on /media/recovery type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3 on /media/windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda8 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda5 on /media/MEDIADIRECT type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000)
/dev/sda9 on /media/disk-1 type ext3 (rw,nosuid,nodev,uhelper=hal)

```
When I say I can't write to it, I mean that I can't e.g. create a new directory in /media/bodega from Dolphin (KDE's file manager).
If I use the command line to copy a file, I get
```
~$ cp mnenhy-0.7.6.666-fx+mz+tb+sm.xpi /media/bodega/
cp: no se puede crear el fichero regular «/media/bodega/mnenhy-0.7.6.666-fx+mz+tb+sm.xpi»: Permiso denegado
```
"no se puede crear el fichero regular" is Spanish for "can't create regular file".
"Permiso denegado" is Spanish for "permission denied".

---

### Post by taurus on 2009-03-07
You need to change the ownership of that mount point, /media/bodega, from root to your login name so you can write to it anytime you want.  _Assuming_ your login name is nema, do

```
sudo chown -R nema:nema /media/bodega
touch /media/bodega/testing
ls -la /media/bodega
```

---

### Post by wangsuda on 2009-03-07
I've had the same problem and have found that this code works for me:
```
sudo chown -R COMPUTER NAME:COMPUTER NAME /media/NAME OF DISK HERE!
```

Good luck!

---

### Post by nemarona on 2009-03-07
Thanks for the advice. I see that changing ownership of /media/bodega would most likely solve the problem. However, I'm puzzled as to why then I *can* write to two ntfs partitions which I set up in analogous way when installing.
Check this out:
```
eduardo@fondecyt:~$ cd /media/
eduardo@fondecyt:/media$ ls -l
total 32
drwxr-xr-x 3 root    root    4096 2009-03-04 12:20 bodega
lrwxrwxrwx 1 root    root       6 2009-03-04 12:21 cdrom -> cdrom0
drwxr-xr-x 2 root    root    4096 2009-03-04 12:21 cdrom0
drwxr-xr-x 3 root    root    4096 2009-03-04 12:21 disk
drwxr-xr-x 3 root    root    4096 2009-03-04 12:20 disk-1
drwxr-xr-x 6 eduardo root    4096 1969-12-31 21:00 MEDIADIRECT
drwxrwx--- 1 root    plugdev 4096 2009-03-03 23:20 recovery
drwxrwx--- 1 root    plugdev 8192 2009-03-04 21:02 windows

```
Would changing group ownership of /media/bodega to "plugdev" be a better solution? I ask this because I intend all users to be able to write to this partition.
Thanks again!

---

### Post by Moop on 2009-03-07
I don't think ntfs uses file permissions, anyone can read and write to them.

---

### Post by hexanol on 2009-03-07
Well, it's a good idea to create a group of users "that can access public data". This way you have more control than just setting the permission to "rwx" for everyone (i.e. permissions = "rwxrwxrwx").

So, what you could do is:
[LIST]
[*]change the group of /media/bodega (be sure the file-system is mounted when you do this) to group *XYZ* (you'll need to create a group named *XYZ* before if it's not already done)
[*]change the permissions of /media/bodega to something like "rwxrwxr-x"
[*]add pertinent users to the group *XYZ*
[/LIST] Personnaly, that's what I did on my system.

NTFS use file persmission on Ubuntu, like FAT, but they are "general" file permissions that you specify when you mount the file-system (or in fstab) and not file-specific permission.

---

### Post by nemarona on 2009-03-07
That's what I did in the end, with only one minor difference: the "plugdev" group was already created (and the ntfs partitions belonged to it).
```
sudo chown -R root:plugdev /media/bodega
sudo chmod -R g+w /media/bodega
```
Everything's fine now. I'm calling this a solved thread :D
Thanks to all who contributed!

---

