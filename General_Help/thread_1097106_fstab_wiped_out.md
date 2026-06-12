---
title: "fstab wiped out"
date: 2009-03-15
forum: General Help
---

### Post by run1206 on 2009-03-15
ok, so while trying to get my printer to work i tried various .deb files while trying to use other drivers.  For some reason my fstab file was wiped and the the only thing showing is the usbfs filesystem :shock: :(

my question:  Is there any way to "recompile" the original list that i had? Is there any place where i may be able to re-list all the filesystems that were on /etc/fstab?  
 
(I can still restart/shutdown Linux and reboot fine, but i know I need that file with the original list of filesystems i had before.)

any suggestions would be great, thanks in advance. :)

---

### Post by taurus on 2009-03-15
If you can still boot Ubuntu, then there has to be /etc/fstab or the system won't know where to mount what.

What's the output of this command from a terminal?

```
ls -la /etc/fstab*
```

---

### Post by run1206 on 2009-03-15
```

run1206@run1206-laptop:~$ ls -la /etc/fstab*
-rw-r--r-- 1 root root 112 2009-03-15 16:32 /etc/fstab
-rw-r--r-- 1 root root  71 2009-03-15 16:31 /etc/fstab~
-rw-r--r-- 1 root root  43 2009-03-15 15:31 /etc/fstab.lexmark-z600.bak

```

is there any way that i might use mtab to fill in the missing filesystems?
i see most of them are there...
```
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
rootfs / rootfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-11-generic/volatile tmpfs rw,mode=755 0 0
usbfs /proc/bus/usb usbfs rw,devgid=14 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/run1206/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=run1206 0 0
/dev/sdb1 /media/My\040GS\040Drive vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sda2 /media/ACER fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sda3 /media/DATA fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0

```

---

### Post by taurus on 2009-03-15
```
cat /etc/fstab
```

---

### Post by drs305 on 2009-03-15
Nevermind - taurus has it covered. If fstab is empty, take a look at the contents of fstab~ and you might be able to recover that file.

---

### Post by run1206 on 2009-03-15
```

run1206@run1206-laptop:~$ cat /etc/fstab
# 	<file system> 		<mount point> 		<type> 		<options> 	<dump> 		<pass>
	proc 			/proc 			proc 		defaults 	0 		0
run1206@run1206-laptop:~$ 

```

and fstab~...
```

run1206@run1206-laptop:~$ cat /etc/fstab~
# 	<file system> 		<mount point> 		<type> 		<options> 	<dump> 		<pass>
run1206@run1206-laptop:~$ 

``` :?

---

### Post by taurus on 2009-03-15
```
cat /etc/fstab~
cat /etc/fstab.lexmark-z600.bak
```

---

### Post by run1206 on 2009-03-15
```
run1206@run1206-laptop:~$ cat /etc/fstab~
# 	<file system> 		<mount point> 		<type> 		<options> 	<dump> 		<pass>
run1206@run1206-laptop:~$ cat /etc/fstab.lexmark-z600.bak 
usbfs			/proc/bus/usb		usbfs	devgid=14 0 0
run1206@run1206-laptop:~$ 

```

the only one showing is the usbfs...

anyway how i can manually put the filesystem back into fstab?

---

### Post by taurus on 2009-03-15
You need to know the UUID's for all the partitions.

```
sudo fdisk -l
sudo blkid
```
Then, your /etc/fstab would look something like

```

proc            /proc           proc    defaults        0       0

UUID=qwer1234asdf5678zxcv  /  ext3  relatime,errors=remount-ro  0  1
UUID=1234qwer5678asdf90  none   swap  sw  0  0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by run1206 on 2009-03-15
thanks for the blkid command...
here's what i get.
```

run1206@run1206-laptop:~$ sudo blkid
/dev/sda1: UUID="2A08D775E49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="3C9051F19051B25E" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="E460B8DC60B8B720" LABEL="DATA" TYPE="ntfs" 
/dev/sda5: UUID="c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="5b5cd6e0-e2c0-4f79-96ce-912d82e5ce7f" 
/dev/sdb1: LABEL="My GS Drive" UUID="780E-9E13" TYPE="vfat" 
run1206@run1206-laptop:~$ 

```

my fstab thus far is the attached file..

---

### Post by taurus on 2009-03-15
If you want to add the other three ntfs partitions to /etc/fstab, you can use ntfs-config.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by run1206 on 2009-03-15
> **taurus said:**
> If you want to add the other three ntfs partitions to /etc/fstab, you can use ntfs-config.

```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

that's the thing, when i first installed Ubuntu on my laptop, i didn't have ntfs on, it already recognized the other partitions... i'll add them anyways..
thanks :)

HA! ntfs-config automatically made my fstab just now!  Awesome!!!
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=5b5cd6e0-e2c0-4f79-96ce-912d82e5ce7f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
usbfs /proc/bus/usb usbfs devgid=14 0 0
/dev/sda1 /media/PQSERVICE ntfs-3g defaults,locale=en_US.UTF-8 0 0

```
thank you guys for the help! greatly appreciated!! :) :D

---

