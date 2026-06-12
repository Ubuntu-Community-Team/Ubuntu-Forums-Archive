---
title: "HDD Partition Inaccessible - can't enable"
date: 2006-05-21
forum: Desktop Environments
---

### Post by yeahright on 2006-05-21
I have a second hard drive which I used for media. It's a hangover from when I used XP so I had three partitions all in NTFS.

In an effort to migrate fully over to Linux, I binned off the third and smallest partition by reformatting it to ext3. However now it's formatted and with a mount path, but the status is descibed as inaccessible and the partition cannot be enabled.

How can I get it functioning again? Did I miss something obvious?

Any help greatly appreciated - thanks!

NB MORE INFORMATION

I am trying to get the third partition enabled and running.

I would like to mount it to media/extra

In DISK MANAGER I've changed the FS to EXT3, and then in gparted I unmounted all three drives in order to properly format the third. When going back into DISK MANAGER it remains inaccessible and cannot be enabled, but also says it's still NTFS.

However, when checking with fdisk below, it clearly labels it as Linux.

```
hbl@*******:~$ sudo fdisk -l

Disk /dev/hda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650       15298    61440592+   7  HPFS/NTFS
/dev/hda3           15299       20023    37953562+  83  Linux
```

---

### Post by aysiu on 2006-05-21
Let's assume this third partition is Ext3 and /dev/hda3 and mounted at /extra_media

If you want to be sure, fire up GParted and check: ```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
``` Of course, you can also check with this command: ```
sudo fdisk -l
```

To make it accessible, paste these two commands in: ```
sudo chown -R yeahright:yeahright /extra_media
sudo chmod -R 755 /extra_media
```

---

### Post by yeahright on 2006-05-22
Thanks for the help. I've appended my original post with some more information.

I'm yet to resolve the issue, as using your suggested code for the terminal (taking my own settings into account) netted no result.

---

### Post by aysiu on 2006-05-22
Can you post the output (including errors) of these commands? ```
sudo mkdir /media/extra
sudo umount /dev/hda3
sudo mount -t ext3 /dev/hda3 /media/extra
```

---

### Post by jdriessen on 2006-08-02
excuse me if its a little rude to ask for help for mounting on someone else's thread, but...

I cannont mount my drive after a crash, my output is:

mount: /dev/hdb2 already mounted or /mnt/storage busy


but it remains inaccessible... I did an fchk on it which repaired my ext3 partition it just wont mount...


any help much appreciated

---

### Post by jdriessen on 2006-08-03
I fixed my problem by reinstalling my system (formatting my primary HD).

My secondary drive mounted as normal again, have you considered doing the same?

---

