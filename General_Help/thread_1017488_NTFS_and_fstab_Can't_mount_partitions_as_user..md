---
title: "NTFS and fstab: Can't mount partitions as user."
date: 2008-12-21
forum: General Help
---

### Post by KaoDome on 2008-12-21
Hi everyone, I have a NTFS partition that I added to the fstab. I can unmount it as a user, but I can't mount it as user (using the mounter applet).

This is how I have that part in fstab:

```
/dev/sda1	/media/Data	ntfs-3g	defaults,users,locale=en_US.UTF-8	0	0
```

Is there any solution?

Thank you for your answers in advance.

---

### Post by drs305 on 2008-12-21
Did you look at the 'details' inside the error message?

If you use "sudo mount -a" does the partition mount?

Please post the results of the following (with it mounted if possible):
```

mount

```

---

### Post by KaoDome on 2008-12-21
I forgot to mention, there are no details shown in the error message.

If you a root you can mount it (or using *sudo*), so *sudo mount -a* mounts it.

Here is the output if mount having it mounted using the above command:
```
/dev/sda5 on / type ext3 (rw)
/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/sda2 on /boot type ext2 (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
gvfs-fuse-daemon on /home/Aphanic/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kaodome)
/dev/sda1 on /media/Data type fuseblk (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8 on /media/PORT9 type vfat (rw,noexec,nosuid,nodev)
```

Thank you for the quickness and for your time.

---

### Post by vanadium on 2008-12-21
To know why it will not unmount, try mounting and unmounting on the command line and post commands and output here

```

mkdir test
mount /dev/sda1 test
umount /dev/sda1

```

Perhaps also try the option "user" rather than "users" in fstab.

---

### Post by KaoDome on 2008-12-21
In order to use *mount* you must be *root* or you need to have *root* privileges so you won't be able to run *mount* in a terminal or tty as far as I know. I've tried right now but as I though:
```
mount: only root can do that
```

Using the option *user* instead of *users* doesn't allow me even to unmount the partition. With *users* I can unmount them using the mounter applet. What I can't do is mount it.

Thanks for you help anyway!

---

### Post by drs305 on 2008-12-21
I spent some time researching this today. It appears to be an issue (perhaps this [bug]("https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/205081")) caused by an ubuntu update a while back which won't allow a user to manually mount an ntfs partition with ntfs-3g via the command line. 

You can go the ntfs-3g.org web site and they will recommend two commands dealing with setuid-root but these apparently will not work in ubuntu. The reason has to do with a security issue and FUSE. The ubuntu devs decided to fix this security issue but it also eliminates the ability of a normal user to mount an ntfs device.

There are solutions to mitigate the problem. *Note that nothing discussed below will allow you mount ntfs as a normal user from the command line.*

First, if you have the correct entry in fstab, the partition will be mounted automatically at boot and you will have full access to it, depending on your fstab options.

Secondly, you can restore the ability to manually mount the device in nautilus by removing or commenting out the device in fstab. If you click on the ntfs device icon in nautilus, you will be given the option, if you have administrative powers, of allowing the user to mount the device. There is an option to make it permanent, so you will no longer be asked for root permission. 

As usual, devices mounted in this manner will show they are owned by root but you will be able to r/w on the contents. This authorization can also be invoked/rescinded via System > Administration > Authorizations > freedesktop > hal > storage > mount filesystems from...

---

### Post by vanadium on 2008-12-22
> In order to use mount you must be root or you need to have root privileges so you won't be able to run mount in a terminal or tty as far as I know.
The user and users options are there to allow users to mount from the command line. With the users option, you can also unmount. However, as drs305 indicated, this might be an ntfs-3g issue.

---

### Post by mgol on 2009-01-10
Check this:
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)
There's a chance it'll help.

---

