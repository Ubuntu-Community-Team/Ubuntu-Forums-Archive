---
title: "updatedb + exclude partition/directory?"
date: 2009-02-10
forum: General Help
---

### Post by peterramesh on 2009-02-10
Hi,

I have duel-boot (Ubuntu & Windows), On login to Ubuntu, the windows partition gets mounted automatically. So the 'updatedb' indexes all the devices mounted.

Is there any way to exclude a specific device(partition) or directory on running 'updatedb' command. 

Here is the list of mount points

```
root@localhost:/home/ramesh# mount -a
root@localhost:/home/ramesh# mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda5 on /home type ext3 (rw,relatime)
/dev/sda7 on /shared type vfat (rw,uid=1000,gid=1000)
/dev/sda1 on /windows type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/ramesh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ramesh)
root@localhost:/home/ramesh
```

When I try to umount the windows partition, it says busy..

```
root@localhost:/home/ramesh# umount /windows/
umount: /windows: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
root@localhost:/home/ramesh#
```

How can i fix this?

TIA,
Ramesh

---

### Post by sdennie on 2009-02-10
Try adding "/windows" to the PRUNEPATHS in /etc/updatedb.conf.  That will at least prevent updatedb from scanning it.  Whether or not that is causing your umount problem, I'm not sure.

---

### Post by peterramesh on 2009-02-10
Hi sdennie,

It worked! (BTW, I'm using Ubuntu 8.10)

Thanks,
Ramesh

---

