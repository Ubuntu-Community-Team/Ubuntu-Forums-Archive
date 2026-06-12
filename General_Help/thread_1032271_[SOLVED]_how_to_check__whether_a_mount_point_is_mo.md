---
title: "[SOLVED] how to check  whether a mount point is mounted or not"
date: 2009-01-06
forum: General Help
---

### Post by brijith on 2009-01-06
Hai All

how to check  whether a mount point is mounted or not through command line

**[COLOR="DarkOrange"]Thanks[/COLOR]**

---

### Post by orlox on 2009-01-06
What precisely do you want to do this for?

I do you know the device name under the /dev folder. For instance, I have a partition at /dev/sda1. If I try to mount it like this:

```

sudo mount /dev/sda1

```

It yells that the partition is already mounted.

---

### Post by Lars Stokholm on 2009-01-06
df

---

### Post by drs305 on 2009-01-06
Run the command below to see what is currently mounted:
```

mount

```
This prints the list of currently mounted devices according to /etc/mtab.

---

### Post by amauk on 2009-01-06
df will show you info on all mounted devices

so you can do this:
df | grep '/your/mount/point'

---

### Post by heindsight on 2009-01-06
you can use either
```
mount
```
or
```
cat /etc/mtab
```

to see a summary of all mounted filesystems.

---

### Post by orlox on 2009-01-06
I had no idea about df! it seems pretty usefull. Also, df -h shows you the partition sizes in a more friendly way.

---

### Post by ivotedforkodos on 2009-03-14
OK, I am trying to resize the partitions on a new HD, which in this case is /dev/sda2. I'm booting off of a USB drive, which is /dev/sdb2. In Gparted, the volume /dev/sda2 appears to be unmounted, as the "Unmount" command is greyed out. The resize operation fails on the e2fsck command. 

So watch this:
```

neurostv@neurostv:~$ umount /dev/sda2
umount: /dev/sda2 is not mounted (according to mtab)
neurostv@neurostv:~$ e2fsck -fvy /dev/sda2
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda2 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
neurostv@neurostv:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 886M     0  886M   0% /lib/init/rw
varrun                886M  236K  885M   1% /var/run
varlock               886M     0  886M   0% /var/lock
udev                  886M  2.9M  883M   1% /dev
tmpfs                 886M     0  886M   0% /dev/shm
rootfs                3.4G  2.3G  973M  71% /
lrm                   886M  2.0M  884M   1% /lib/modules/2.6.27-9-generic/volatile
tmpfs                 192M  1.7M  191M   1% /tmp
/dev/sdb1             236M   15M  209M   7% /media/BOOT
/dev/scd0             7.6G  7.6G     0 100% /media/cdrom0
neurostv@neurostv:~$ 

```

WTF??!! Is this partition mounted or not? Am I crazy?

---

### Post by ivotedforkodos on 2009-03-14
UPDATE: I solved the problem by booting from a GParted LiveCD, and doing the partitioning there.

---

