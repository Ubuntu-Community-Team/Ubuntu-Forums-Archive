---
title: "Can't mount 32gb SSD"
date: 2011-03-05
forum: Desktop Environments
---

### Post by rabiabidabi on 2011-03-05
Hi,
I recently switched from 9:10 to Lubuntu 10:10. I love the speed and look of this distro, and it works great on my Asus eeepc1000.

However, I cannot get the 32gb SSD to mount as my HOME folder. I had the same problem when I first upgraded from 9:04 to 9:10 and received great help here on this thread: [http://ubuntuforums.org/showthread.php?t=1408875](http://ubuntuforums.org/showthread.php?t=1408875)

I have repeated all the steps with no luck.

Thanks in advance for any advice.

Have a great day,
Rob

---

### Post by vanadium on 2011-03-05
Provide the output of following commands:
```

mount
sudo fdisk -l
sudo blkid
cat /etc/fstab

```

---

### Post by rabiabidabi on 2011-03-05
Hi and thanks,


robert@robert-1000:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/robert/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=robert)
robert@robert-1000:~$ sudo fdisk -l
[sudo] password for robert: 

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00005d7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         933     7490560   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             933         981      387073    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             933         981      387072   82  Linux swap / Solaris

Disk /dev/sdb: 32.3 GB, 32279224320 bytes
255 heads, 63 sectors/track, 3924 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7743

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3316    26635738+  83  Linux
/dev/sdb2            3317        3924     4883760    5  Extended
/dev/sdb5            3317        3924     4883728+  82  Linux swap / Solaris
robert@robert-1000:~$ sudo blkid
/dev/sdb1: LABEL="HOME" UUID="14091da3-055d-401b-b93f-16dcd4d90360" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda1: UUID="60254af8-e4a0-4c05-9e62-c522222d8ca3" TYPE="ext4" 
/dev/sda5: UUID="ff35d144-01ce-4117-a23d-f5759fba9f96" TYPE="swap" 
/dev/sdb5: UUID="7bd43b42-3fff-43d7-82eb-1e638a377c3e" TYPE="swap" 
robert@robert-1000:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=60254af8-e4a0-4c05-9e62-c522222d8ca3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ff35d144-01ce-4117-a23d-f5759fba9f96 none            swap    sw              0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
robert@robert-1000:~$

---

### Post by vanadium on 2011-03-06
Your system seems to be up and running well. Your /home is on the oartition mounted as /. It is during installation of Ubuntu that you can choose to mount your SSD as /home. Alternatively, you could attempt moving /home to a separate partition, which is a somewhat technical procedure.

Your best bet, in my opinion, is to mount your SSD as a data partition, then link all your storage folders (e.g. Documents, Pictures, ...) over there.

You first need to add your SSD to the config file /etc/fstab in order to mount it automatically during startup. 
- First make a mount point:
```

sudo mkdir /mnt/ssd

```
- Then add this line to /etc/fstab
```

UUID=14091da3-055d-401b-b93f-16dcd4d90360  /mnt/ssd  ext3  defaults 0  2

```
Mount the partition (and check whether all is good)
```

sudo mount -a

```
All is good if you do not have any error messages from the last command. Now, your SSD is accessible in /mnt/ssd, but in order to easily access the storage, you will use symbolic links.

- Create storage directories for your data
```

sudo mkdir /mnt/Documents /mnt/Music /mnt/Pictures

```
- Change ownership of these new directories to you as user.
```

sudo chown $USER:$USER /mnt/Documents /mnt/Music /mnt/Pictures

```
- Copy your existing Documents, Music, etc over to the new location
```

rsync -av ~/Documents/ /mnt/Documents/
rsync -av ~/Music/ /mnt/Music/
...

```
- Replace original Documents, Music by links pointing to new location. For safety, I am renaming the old ones. They can be deleted if all prooves to be well.
```

mv ~/Documents ~/Documents_old
mv ~/Music ~/Music_old
ln -s /mnt/Documents ~/Documents
ln -s /mnt/Music ~/Music
...

```

and now you should find your Documents, Music in your home folder as before. However, they are now on the SSD disk.

---

### Post by rabiabidabi on 2011-03-06
Good morning Vanadium, and thanks,

after the command sudo mount -a, I received this warning:
[mntent]: warning: no final newline at the end of /etc/fstab
mount

I rebooted, and the SSD appears in my filesystem. However, in the File Manager, it is listed as "floppy O" and clicking on it reveals this message:
[mntent]: warning: no final newline at the end of /etc/fstab
mount: special device /dev/scd0 does not exist

Maybe in /etc/fstab, I have to add #32GB SSD before the UUID...?

You're a great help, Vanadium. I do appreciate your time and effort.

Rob

---

### Post by vanadium on 2011-03-06
The warning message states there is no final newline in /etc/fstab.

---

### Post by rabiabidabi on 2011-03-06
Aah..I neglected to hit "enter" after I added the UUID to /etc/fstab.

I am now going to proceed with the other steps.

Thanks,
Rob

---

### Post by rabiabidabi on 2011-03-06
Done and done. My file manager shows 2 Music, one marked "old"  Same for the other folders.

The Filesystems shows the 32gb SSd as /mnt/ssd

Is there a way to check if everything was moved to the 32gb ssd?

Again, thank you very much,
Rob

---

### Post by rabiabidabi on 2011-03-06
Ignore my last post...duh...everything is fine.

Everything is great...thanks

---

