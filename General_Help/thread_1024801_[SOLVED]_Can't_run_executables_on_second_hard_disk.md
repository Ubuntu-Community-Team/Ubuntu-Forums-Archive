---
title: "[SOLVED] Can't run executables on second hard disk"
date: 2008-12-29
forum: General Help
---

### Post by jyaan on 2008-12-29
I recently moved all of my source code to a second hard disk. The problem is that I cannot execute any of the binaries I build! If I make a binary under /home, I am able to execute it. This is the situation : ```
jyaan@ubuntu:~$ ./a.out 
What is going on?
jyaan@ubuntu:~$ ls -l a.out && ls -ld .
-rwxr-xr-x 1 jyaan jyaan 9040 2008-12-29 12:50 a.out
drwxr-xr-x 103 jyaan jyaan 4096 2008-12-29 12:50 .
jyaan@ubuntu:~$ cp a.out disk && cd disk
jyaan@ubuntu:~/disk$ ./a.out 
bash: ./a.out: Permission denied
jyaan@ubuntu:~/disk$ ls -l a.out && ls -ld .
-rwxr-xr-x 1 jyaan jyaan 9040 2008-12-29 12:55 a.out
drwxr-xr-x 15 jyaan jyaan 4096 2008-12-29 12:34 .
jyaan@ubuntu:~/disk$ 

```

How does this make any sense? The permissions are exactly the same. I cannot run bash scripts, either. Python does work, though.

---

### Post by taurus on 2008-12-29
What filesystem is that second harddrive?

---

### Post by albinootje on 2008-12-29
> **jyaan said:**
> I recently moved all of my source code to a second hard disk. The problem is that I cannot execute any of the binaries I build! If I make a binary under /home, I am able to execute it. 


What is the file-system on that disk ?
What are the mount options of that disk ?
Can you post the output of the following :
```

sudo fdisk -l
mount
cat /etc/fstab
echo $PATH

```

---

### Post by prshah on 2008-12-29
> **jyaan said:**
> I recently moved all of my source code to a second hard disk. The problem is that I cannot execute any of the binaries I build! 

if the second hard disk is mounted with the "noexec" option, it will not allow execution of binary files.

If you are not sure of whether or not you have used such an option, either mention what command you are using to mount the disk, or post your /etc/fstab file.

You can quickly check if "noexec" is the problem using the terminal (Applications-Accessories-Terminal)```
mount | grep noexec
``` Check to see if your second drive is listed in the results.

---

### Post by jyaan on 2008-12-29
They are both EXT3. They have the same permissions aside from the addition of 'user' on the second drive (for normal user access). Oddly, the second disk is /dev/sda. I don't know why it was like this, considering that the first drive is specified is #1 in BIOS. They are the same model as well.

```
jyaan@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe4f90474

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c5a18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          12       96358+  83  Linux
/dev/sdb2              13         255     1951897+  82  Linux swap / Solaris
/dev/sdb3             256        3294    24410767+  83  Linux
/dev/sdb4            3295       30401   217736977+  83  Linux

Disk /dev/sde: 62 MB, 62390272 bytes
8 heads, 32 sectors/track, 476 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1         476       60912    6  FAT16

```
```
jyaan@ubuntu:~$ mount
/dev/sdb3 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
/dev/sdb1 on /boot type ext2 (rw,relatime)
/dev/sdb4 on /home type ext3 (rw,relatime)
/dev/sda1 on /media/ext3bk type ext3 (rw,noexec,nosuid,nodev,relatime,errors=remount-ro)
none on /proc/bus/usb type usbfs (rw,devgid=46,devmode=664)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jyaan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jyaan)
/dev/sde1 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

```
```
jyaan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=835c3f0f-5d96-4e1a-8d30-9f777e5acf2f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=359949e1-5b51-4cf4-af14-7fec7ead891c /boot           ext2    relatime        0       2
# /dev/sda4
UUID=915367af-f77c-44ee-9431-83565e4e9923 /home           ext3    relatime        0       2
# /dev/sda2
UUID=af76094b-32c4-4033-ac18-f6f63eb7d2ae none            swap    sw              0       0
# backup partition & media ext
UUID=3d33ec63-76cf-48c7-b817-6695d9a8c272 /media/ext3bk	  ext3	  relatime,errors=remount-ro,user  0 2
# old IDE drive -- n/a atm
#UUID=6407312f-e222-42ed-8e87-49a0453c0d46 /media/disk	  ext3	  relatime,errors=remount-ro,users 0 2


/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

# usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

```

---

### Post by jyaan on 2008-12-29
Wow that's really odd. I didn't specify noexec, but it is indeed set. I suppose all I need to do is specify exec in /etc/fstab.

---

### Post by jyaan on 2008-12-29
Yea, it's working now. It seems that the Gnome disk mounter applet added those options. They should probably make it stick to the options specified in /etc/fstab. :S

---

### Post by albinootje on 2008-12-29
> **jyaan said:**
> Wow that's really odd. I didn't specify noexec, but it is indeed set. I suppose all I need to do is specify exec in /etc/fstab.

/dev/sda1 on /media/ext3bk type ext3 (rw,noexec,nosuid,nodev,relatime,errors=remount-ro)

Just remove the noexec option, and remount it.

---

