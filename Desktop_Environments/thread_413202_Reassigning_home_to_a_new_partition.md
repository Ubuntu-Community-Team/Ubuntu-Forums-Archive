---
title: "Reassigning home to a new partition"
date: 2007-04-18
forum: Desktop Environments
---

### Post by eeefresh on 2007-04-18
I have a dual boot system with XP and Feisty installed.  My current setup is:

sda1 - XP (40 GB, NTFS)
sda2 - Feisty (30 GB, ext3)
sda3 - swap (1 GB)
sda4 - Shared (250 GB, ext3)

I have the XP driver installed that lets you read and write to ext3 (can't remember the name at the moment.)  I have a LOT of stuff in the Shared partition, but I want to make it my home folder in Ubuntu without losing all those files.  Is there a way to reassign home so that it points to that partition after I have already installed Feisty?

---

### Post by JLB on 2007-04-18
something like this ought to work by adding it to your /etc/fstab and then rebooting.
```
# /dev/sda4        /home           ext3    defaults        0       2
```

make a backup copy of your fstab file just in case and you need to copy the old one back.

```
sudo cp /etc/fstab /etc/fstab.backup
```

---

### Post by eeefresh on 2007-04-19
Thanks, but that that didn't seem to work.  It still took me to the default home folder, which only contains Desktop and Examples.


Also, I need to clarifiy:  Rather than point to the whole partition, I want home to be a specific folder on the sda4 partition.  So I guess in my example, I want home to be sda4/doug.

---

### Post by mlind on 2007-04-19
add /etc/fstab entry
```

/dev/sda4       /home           ext3    defaults        0       2

```

copy your /home folder contents to /dev/sda4
```

# do in single user mode
sudo init 1
umount /dev/sda4
mount /dev/sda4 /mnt

cp -a  /home/* /mnt
umount /mnt
mount /home
init 2

```

You probably want to copy files from share partition in to a single folder before doing this. Makes it easier to move shared partition stuff back to your $HOME folder.

---

### Post by lolocaust on 2007-04-19
Try making a symbolic link, I just did the same thing myself: sudo ln -s (folder you want to link to) (where you want to link from) so for myself i did sudo ln -s /media/files/home /home/lolocaust where media/files is another drive with a /home subfolder.

---

### Post by eeefresh on 2007-04-19
> **mlind said:**
> add /etc/fstab entry
```

/dev/sda4       /home           ext3    defaults        0       2

```

copy your /home folder contents to /dev/sda4
```

# do in single user mode
sudo init 1
umount /dev/sda4
mount /dev/sda4 /mnt

cp -a  /home/* /mnt
umount /mnt
mount /home
init 2

```

You probably want to copy files from share partition in to a single folder before doing this. Makes it easier to move shared partition stuff back to your $HOME folder.

This worked!  Thanks.  The first suggestion didn't work because of that extra pound sign in the fstab entry.

---

