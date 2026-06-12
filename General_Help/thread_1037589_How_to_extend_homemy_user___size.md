---
title: "How to extend /home/my_user   size"
date: 2009-01-11
forum: General Help
---

### Post by grimanda on 2009-01-11
Dear All..., 

Sorry, i just joined ubuntu 8.10
, currently i have dual OS on my laptop, vista and ubuntu 8.10

i would like to install windows application through wine..
but the space available is insufficient, so i need to extend my /home/user/.wine/..., the additional space should be taken from other directory, let say /tmpfs for instance.

but due to i'm a newbie, i'm not familiar with ubuntu yet.
can anyone give me any easy step how to do it?, i just want to leave windows actually,


Kindly need your help.


BR,

---

### Post by andresmh on 2009-01-11
You probably want to resize the partition where /home resides. Do you know the name of the partition?

Post the output of:
```

mount
df -sh

```

If you need to resize a partition you can use an application called GParted but if the partition is being used by the OS you will need to unmount it first. If the partition is your main partition then it's probably easier to do it from a LiveCD.

---

### Post by grimanda on 2009-01-11
Hi andres...
here is the result,
i have no df- sh

grimanda@ubuntu:/$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       13G  3.5G  8.8G  29% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  220K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.9M 1009M   1% /dev
tmpfs                1012M  720K 1011M   1% /dev/shm
/dev/sda2              75G   56G   20G  75% /host
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-9-generic/volatile


BR,

---

### Post by grimanda on 2009-01-11
just additional information

grimanda@ubuntu:/$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/grimanda/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=grimanda)

---

### Post by andresmh on 2009-01-11
most likely your /home directory lives in the root partition, the one listed at the top.

If you want to resize the root partition the easiest is probably to boot with the LiveCD repartition it from there.

Google "how to resize root partition"

---

### Post by grimanda on 2009-01-12
ok while in parallell i'm googling, it save for the available data? i mean, i have vista with ntfs, and the ubuntu data it self, will it "disturb" the available data, or just resize the size and keep all the data safe ?

regrds,

---

### Post by cb34 on 2009-01-12
look into gparted.

with gparted you can resize the partitions pretty easily.

i've done it many times without any problems, but alwayz back up your data first to make sure.

---

