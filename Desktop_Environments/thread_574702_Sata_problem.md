---
title: "Sata problem"
date: 2007-10-13
forum: Desktop Environments
---

### Post by zadirion on 2007-10-13
Hello,
I am recently new to ubuntu, so please bare with me.
I have a SATA hard drive which i share with WindowsXP on a dual boot system.
The SATA hdd mounted successfully  i can read the files on the SATA HDD from ubuntu, but I can't write on the hard drive.
the owner of the hdd is root
this is the result for "ls -l /media":
lrwxrwxrwx 1 root root       6 2007-10-12 17:06 cdrom -> cdrom0
drwxr-xr-x 2 root root    4096 2007-10-12 17:06 cdrom0
lrwxrwxrwx 1 root root       7 2007-10-12 17:06 floppy -> floppy0
drwxr-xr-x 2 root root    4096 2007-10-12 17:06 floppy0
dr-xr-x--- 1 root plugdev 8192 2007-10-12 12:13 sda1

The last line is the sata hdd, from what i see, not even root can write on the hdd, which i find odd. Anyway, i tried "sudo chown <myusername> /media/sda1"
and I get "chown: changing ownership of `/media/sda1': Read-only file system";

 mount -o remount,rw /dev/sda1  
the hdd remounts, but i still can't write on it. Anyone can help?
Thanx in advance

---

### Post by banewman on 2007-10-13
You need to install the package -    ntfs-3g    - synaptic package manager is the easiest way :)

---

### Post by zadirion on 2007-10-13
erm, and what next?

---

### Post by PmDematagoda on 2007-10-13
Install ntfs-config as well, it gives you a nice GUI where you can make the necessary changes.

---

