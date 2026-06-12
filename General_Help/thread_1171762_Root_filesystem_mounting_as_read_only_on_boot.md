---
title: "Root filesystem mounting as read only on boot"
date: 2009-05-27
forum: General Help
---

### Post by googlegot on 2009-05-27
My root filesystem is mounting as read only, and I cannot for the life of me figure out why.

I have done everything I can think of, including modifying my menu.lst, fstab and mtab, as well as going so far as to compile another kernel just to see if that would fix it.

Here is my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/nvidia_babedbeb3 during installation
UUID=2689311f-6d00-4369-aa88-64ad5c02c9cc /               ext4    rw,relatime     0       1
# /boot was on /dev/mapper/nvidia_babedbeb1 during installation
UUID=cac93c15-f89b-447e-9100-200d2bb1a962 /boot           ext3    rw,relatime        0       2
# swap was on /dev/mapper/nvidia_babedbeb2 during installation
UUID=c6c01db7-b5a8-4e9a-bafc-902c7f2cbbdb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

here is my menu.lst

```

title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.28-11-generic root=/dev/mapper/nvidia_babedbeb3 ro quiet splash 
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.28-11-generic root=/dev/mapper/nvidia_babedbeb3 ro  single
initrd		/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin

```

and here is my mtab


```
/dev/mapper/nvidia_babedbeb3 / ext4 rw,relatime 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
shmfs /lib/init/rw/splashy tmpfs rw 0 0
lrm /lib/modules/2.6.28-11-generic/volatile tmpfs rw,mode=755 0 0
/dev/mapper/nvidia_babedbeb1 /boot ext3 rw,relatime 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/teaton/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=teaton 0 0
/dev/sdh2 /media/TEATON'S\040IP vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
gvfs-fuse-daemon /root/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev 0 0
/dev/mapper/nvidia_babedbeb1 /boot ext3 rw 0 0
```


Im running jaunty 64 bit on a fakeraid (dmraid), and this all started after reinstalling usplash

Help me out here.

---

### Post by googlegot on 2009-05-27
thanks for all the help! I guess Im reinstalling then

---

