---
title: "Decrypt my partitions permanently"
date: 2009-05-25
forum: General Help
---

### Post by edwardblum on 2009-05-25
Hi There,

When I originally installed Ubuntu, (8.04) I thought I would be really clever and use the encryption option on the alternative install.

I've now realised that installing something like true crypt which encrypts the entire hardrive would have been more sensible.

How do I decrypt my partitions permanently without re installing the OS?


Does the setup use dm-crypt to encrypt the drive?

Any help would be greatly appreciated!

here are the results of mount:

/dev/mapper/sda2_crypt on / type ext3 (rw,errors=remount-ro,commit=600)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda1 on /boot type ext3 (rw,relatime,commit=600)
/dev/mapper/sda6_crypt on /home type ext3 (rw,commit=600)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ed/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ed)

---

