---
title: "Mounted an NTFS hard drive but can not see the files in it."
date: 2009-03-07
forum: General Help
---

### Post by cran73 on 2009-03-07
Hello,

After testing Xubuntu for a few weeks I decided to free myself from Windows, so I installed it on my desktop. The installation went well except that it did not mount my other hard drives, including one with all my multimedia (/dev/sdc1). I mounted it just fine, but when I access the drive, I can only see folders, all the files in the folders are not there... The folders show as empty.

Can someone please help?

Thanks,

Chakib

---

### Post by murataht on 2009-03-07
1)mount
try to see how it is mounted using "mount" command. (simply type the command without any param in the command line.)

here is an example I have got for my ntfs partition. 

```

/dev/sda2 on /media/sda2 type fuseblk (rw, nosuid, nodev, allow_other, blksize=4096)

```

maybe the output will give you some hints why your partition is not working correctly.


2)fstab 
and i have this line in "/etc/fstab":
```

/dev/sda2 /media/sda2 ntfs-3g defaults,locale=en_US.UTF-8 0 1

```

with this line, my ntfs partition is always mounted when the system is started.

---

### Post by cran73 on 2009-03-07
Thanks for the reply, this is what I get with the command "mount":

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
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /mnt/Multimedia type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

The drive is mounted and it seems to be operating propperly (but then again, I am not a linux expert)... Do you have any suggestions? I tried unmounting and mounting again, unmounting, rebooting and mounting again, etc.. but I get the exact same result.

Chakib

---

