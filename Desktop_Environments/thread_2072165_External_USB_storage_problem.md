---
title: "External USB storage problem"
date: 2012-10-17
forum: Desktop Environments
---

### Post by aevora on 2012-10-17
Dear members:
I'm using Xubuntu 12.04 LTS and happens that when I insert any external USB storage that is displayed on the desktop (icon) but as root (readonly), ie, to save information on it I must:
** - Open a terminal and remove the external USB storage (sudo umount /media/usb0)
** - Once done I can double click on the drive icon and this now if mounted correctly.

The solution is simple but annoying especially when you are testing with several external USB storage.

Best regards and thanks in advance.

(Sorry for my English ;-|)

---

### Post by LewisTM on 2012-10-17
Hi,
Could you post the terminal outputs of the [FONT="Courier New"]mount[/FONT] command (just 'mount') **1)** After your first attempt (when the drive is readonly) **2)** After your second mount (which is rw).

Thanks!

---

### Post by aevora on 2012-10-18
Hi LewisTM, first thanks.

The terminal outputs are:

1)
[B]aevora@isaevora:~/Escritorio$ sudo mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aevora/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aevora)
/dev/sdb1 on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime)[/B]

2)
[B]aevora@isaevora:~/Escritorio$ sudo mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda5 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aevora/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aevora)
/dev/sdb1 on /media/08F9-81DB type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
[/B]

I see that before and after are mounted with different options :confused::confused:

Best regards.

---

### Post by LewisTM on 2012-10-18
I might have an explanation. The only process (that I know of) that mounts devices in /media/usb# is **usbmount**. It's an old and deprecated software that conflicts with the way modern Ubuntu automounts USB devices. 

You should see if package usbmount is installed and remove it. Also verify that directory /etc/usbmount is absent or at least empty.

---

### Post by aevora on 2012-10-19
Now everything works fine, thank you very much!!!
The package in question probably install it by following some manual to solve another problem (certainly not solved, but I will tell you).

Best regards and good weekend.

---

### Post by LewisTM on 2012-10-19
Glad to be of assistance. Please mark the thread as SOLVED.

---

### Post by aevora on 2012-10-19
Sorry, it is marked as resolved.

Thank you.

---

