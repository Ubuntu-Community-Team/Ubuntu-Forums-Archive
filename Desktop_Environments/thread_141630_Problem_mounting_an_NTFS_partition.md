---
title: "Problem mounting an NTFS partition"
date: 2006-03-08
forum: Desktop Environments
---

### Post by stufff11 on 2006-03-08
Was using a guide at the wiki, URL as follows: [https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29](https://wiki.ubuntu.com/MountNtfsOnBoot?highlight=%28ntfs%29)

It directed me here if instructions did not work. **Here is my activity in the command line:**

stufff@shade:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7651    61455208+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2            7652        9640    15976642+  83  Linux
/dev/hda3            9641        9729      714892+   5  Extended
/dev/hda5            9641        9729      714861   82  Linux swap / Solaris
stufff@shade:~$ sudo mkdir /mnt/ntfs1
stufff@shade:~$ sudo cp /etc/stab /etc/fstab_backup1
cp: cannot stat `/etc/stab': No such file or directory
stufff@shade:~$ sudo gedit /etc/fstab
stufff@shade:~$ sudo gedit /etc/fstab
stufff@shade:~$ sudo umount -a
umount: /dev: device is busy
umount: /: device is busy
stufff@shade:~$ mount
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
stufff@shade:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/ntfs1      ntfs    ro,nls=utf8,umask=0222  0       0
stufff@shade:~$ mount | sort
/dev/hda2 on / type ext3 (rw,errors=remount-ro)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
proc on /proc type proc (rw)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
[B]
Here are the contents of my /etc/fstab file:[/B]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/mnt/ntfs1 	ntfs 	ro,nls=utf8,umask=0222 	0 	0

Needless to say, my NTFS partition (Windows XP Pro, SP2, if that helps) is not mounted.

---

### Post by taurus on 2006-03-08
What happens if you try to mount it by hand,
```

sudo mount -t ntfs /dev/hda1 /mnt/ntfs1

```
And check your spelling because there is no such thing as /etc/stab!  Also, don't run "umount -a" because you don't want to unmount all the partitions since you need /, /home, and swap to be mounted so you can use them!!!

---

### Post by Sutekh on 2006-03-08
It looks like you've set it up correctly, just run
```
sudo mount -a
``` to automatically mount your fstab again, including the newly setup NTFS partition.

(Don't know why the instructions suggest umount though)

---

### Post by AndrewCaul on 2006-03-08
[QUOTE=Sutekh]It looks like you've set it up correctly, just run
```
sudo mount -a
``` to automatically mount your fstab again, including the newly setup NTFS partition.

(Don't know why the instructions suggest umount though)[/QUOTE]
according to that page it mounts unmounted partitions. But it actually unmounts mounted partitions, so someone should change that explanation. (Not me. I'm not logged into the wiki right now)

---

### Post by Sutekh on 2006-03-08
[QUOTE=Wiki]Finish the process with:

  sudo umount -a
  

which will **mount every unmounted entry in the fstab**. You can check which partitions are mounted after this with: [/QUOTE]
Actually it a typo, the author did mean to mount the unmounted partitions, but gave the command to unmount them instead.

Edit: Oh Andrew spotted it too

---

