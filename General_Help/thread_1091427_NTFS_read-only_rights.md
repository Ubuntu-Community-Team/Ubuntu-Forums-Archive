---
title: "NTFS read-only rights?"
date: 2009-03-09
forum: General Help
---

### Post by Kentrino on 2009-03-09
Just switched from XP to Ubuntu. I have never used Ubuntu before and now I have a problem:p

I have a ntfs harddrive, but it only has "read-only" rights.. And if I go to preferences- Rights/priviliges I get an error: "The priviliges for sdb1 could not be decided" (sorry for the bad english, but my ubuntu is in norwegian).

Anyone who could help? :)

---

### Post by Vince4Amy on 2009-03-09
Try this, Unmount that drive and do the following:

```
sudo mkdir /media/sdbdrive && sudo mount -t ntfs /dev/sdb1 /media/sdbdrive
```

If this works then we can add it to fstab so it mounts at boot if you want to. See if it works first anyway. When you go into Computer or Places it should show as sdbdrive. We'll rename it to whatever else later if you want.

---

### Post by kpatz on 2009-03-09
Type "mount" by itself and post what you get.

As for Vince4Amy's response, check and see what device name the drive really is (the mount command above will tell you), it may not necessarily be sdb1.

---

### Post by Kentrino on 2009-03-09
That worked, but its still the same as before, "The rights/privilies could not be decided".. :(

Typed mount in terminal: 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/hygen/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hygen)
/dev/sdb1 on /media/sdbdrive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

---

### Post by Vince4Amy on 2009-03-09
It is sdb as he says in his first post.

---

### Post by kpatz on 2009-03-10
Try this first:

> 
sudo umount /media/sdbdrive
sudo mount -t ntfs-3g /dev/sdb1 /media/sdbdrive


If that works, add this to your /etc/fstab:

> /dev/sdb1 /media/sdbdrive ntfs-3g defaults 0 0

---

