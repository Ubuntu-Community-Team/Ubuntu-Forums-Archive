---
title: "how mount qemu img?"
date: 2006-02-27
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-02-27
**please scroll down to the end of this post** if you would like to help me with another qemu problem (?). This mounting problem is solved for now (bc. I was stupid enough to miss the part where it says "it does not mount qcow images" grr)

---------------------------------------
i created the image with qemu-img and partitioned (ntfs, 1 partition, 500MB) and mounted under the emulated Windows using its own partitioning utility. Everything is fine under windows. it sees it, mounts it, reads & write to it...

but the host linux cannot mount it. so far I tried: 
```
sudo mount homewinxp.img /mnt/qemu/ -t ntfs -o loop=/dev/loop5,blocksize=1024
```
and variations
and
```
sudo mount -o loop,blocksize=1024 homewinxp.img /mnt/qemu/
```
```
sudo mount -o loop,offset=32256 homewinxp.img /mnt/qemu/
```

none of these 3 worked... 

for the first one, it says: 
> mount: wrong fs type, bad option, bad superblock on /dev/loop5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

for the other 2, it says:
> ioctl: LOOP_CLR_FD: Device or resource busy
mount: you must specify the filesystem type

or (when I tell it it is ntfs or msdos)
> 
mount: wrong fs type, bad option, bad superblock on /dev/loop5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail complains about img not being filesystem x (x = whatever I set)

fdisk xxxx.img says:
> 
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.

what am I doing wrong????
----------------------------------------------------

Oh, and I have this problem with qemu:
[http://ubuntuforums.org/showthread.php?t=136636](http://ubuntuforums.org/showthread.php?t=136636) (qemu too slow? or wrong computer configuration?)
Can you also check out that one? 

thanks so much!

---

### Post by towsonu2003 on 2006-02-27
oh crap... I missed the section where it says "it doesn't mount qcow". crap...

---

### Post by towsonu2003 on 2006-03-04
/path/to/windows.raw  /media/qemu  vfat  rw,user,loop,noauto,offset=32256  0  0

in case someone else needs, this is my fstab entry. works, but have to mount with sudo bc ubuntu doesn't let regular users play with loop (I think).

---

### Post by miltont on 2007-02-26
Hi, I've tried adding your line to my fstab, and changed it to point to my windows.img file which is a raw file.  Then I sudo mount /home/milton/windows.img in terminal and I get: "can't find /home/milton/windows.img in /etc/fstab or /etc/mtab" I'm a bit new at this, so any help you can give me would be great.  I've gotten qemu to run perfectly, but I want to be able to access the windows img while i'm in ubuntu.  Thanks.

---

### Post by miltont on 2007-02-26
Ok, ignore my last post, I had to restart my system and now it finds the img.  But I still get your first error when I type sudo mount /home/milton/windows.img

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

This is the line I have in my fstab:
/home/milton/windows.img /media/qemu ntfs rw,user,loop,noauto,offset=32256 0 0

I've even tried chaning ntfs to vfat but still get the same message.  Did you convert your raw image?  I know the FAQ we've both looked at said it can't mount qcow images...

---

### Post by towsonu2003 on 2007-02-26
after trying to mount it, what does ```
dmesg| tail
``` shows?

---

### Post by miltont on 2007-02-26
Ok,
first I tried to mount my image using:

sudo mount /home/milton/windows.img

which gives me:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Then using what you said, 

dmesg| tail

I get:

[17444048.440000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17444048.440000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17444048.440000] NTFS-fs error (device loop0): ntfs_fill_super(): Not an NTFS volume.
[17451843.324000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17451843.324000] NTFS-fs error (device loop0): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17451843.324000] NTFS-fs error (device loop0): ntfs_fill_super(): Not an NTFS volume.
[17451918.572000] FAT: bogus number of reserved sectors
[17451918.572000] VFS: Can't find a valid FAT filesystem on dev loop0.
[17452026.204000] FAT: bogus number of reserved sectors
[17452026.204000] VFS: Can't find a valid FAT filesystem on dev loop0.

And this is what I have in my fstab:

/home/milton/windows.img /media/qemu vfat rw,user,loop,noauto,offset=32256 0 0

I guess just to give you more background...I created my windows.img file from the community doc using the line:

qemu-img create -f qcow windows.img 10G

Thanks for trying to help me out.  If I can get my img to mount...then I'd be in great shape.

---

### Post by towsonu2003 on 2007-02-26
> **miltont said:**
> I created my windows.img file from the community doc using the line:

qemu-img create -f qcow windows.img 10G

Thanks for trying to help me out.  If I can get my img to mount...then I'd be in great shape.

good thing you provided the command. you created the image file as qcow, which is not mountable. you could either convert it to raw
```
qemu-img convert -f qcow <file_to_convert> -O raw <rawformat_filename>
```
-f means the format of the input image file; -O means format of output file...

or you could use the networking features of Qemu to use ftp to share files between a running guest and a host.

---

### Post by Dragonshadow on 2007-06-20
I need help, It tells me I need to specify a file system, so I told it RAW (same as the image file) and it says raw isn't a valid file system.

Help me please.

**EDIT:** Nevermind, you reall do have to change it to a .raw instead of leaving it a .img XD

---

### Post by earizon on 2008-04-28
(looks it's too late to answer, but Search Engines are fond on ubuntuforums.org and redirects here whenever someones search for qemu + raw + loop devices or related stuff, so I will answer in case someone else lands here via Google or Yahoo)

Accessing raw images with partitions "inside" is a bit tricky. Still this links explains it:
  [http://equivocation.org/node/107](http://equivocation.org/node/107)

 Basically you "simulate" a block device /dev/loop0 for your file with the command:

 # losetup /dev/loop0 /var/vms/image.raw

 Then all than needed is to use kpartx to map partitions to devices you can finally mount:

 # kpartx -av /dev/loop0 

 # ls -alF /dev/mapper
 brw-rw---- 1 root disk 253, 4 2007-11-24 14:56 loop0p1
 brw-rw---- 1 root disk 253, 5 2007-11-24 14:56 loop0p5 

 # mount /dev/mapper/loop0p1 /mnt/MyFileSystem

---

