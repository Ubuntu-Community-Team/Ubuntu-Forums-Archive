---
title: "Mount audio cd with quicktime files"
date: 2005-06-14
forum: Desktop Environments
---

### Post by geist3 on 2005-06-14
I have a multimedia cd, i insert it and i can play the music. However i cant access the quicktime video extras files on there (checked on another computer). I type (in /dev)
sudo mount hdc
sudo mount cdrom0 -l
sudo mount cdrom0 /mnt/dvd
sudo mount cdrom0 /mnt/dvd -o unhide
sudo mount cdrom0 -t iso9
sudo mount /dev/cdrom /mnt/dvd -t iso9660

and all i get back is
[i]
mount: block device /dev/cdrom is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/i]

How do i get it to mount so i can see the video and pdf files as opposed to the audio tracks?

---

### Post by Alexander Kirillov on 2005-06-14
[QUOTE=geist3]I have a multimedia cd, i insert it and i can play the music. However i cant access the quicktime video extras files on there (checked on another computer). I type (in /dev)
sudo mount hdc
sudo mount cdrom0 -l
sudo mount cdrom0 /mnt/dvd
sudo mount cdrom0 /mnt/dvd -o unhide
sudo mount cdrom0 -t iso9
sudo mount /dev/cdrom /mnt/dvd -t iso9660

and all i get back is
[i]
mount: block device /dev/cdrom is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/i]

How do i get it to mount so i can see the video and pdf files as opposed to the audio tracks?[/QUOTE]
 Correct syntax is 
sudo mount -t iso9660 /dev/cdrom /mnt/dvd
(assuming, of course, that /mnt/dvd directory already exists). By the way: ubuntu usually uses /media rather than /mnt for mounting - but this is not important.

---

### Post by geist3 on 2005-06-14
Same error, i put in the cd, it starts playing, I cant unmount it while its playing (says cdrom is not mounted, i only have 1 cdrom drive).

mount output
> 
/dev/hdb2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/sdc1 on /media/usbdisk type vfat (rw,nosuid,nodev,sync,noatime,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8)
/dev/hdb5 on /mnt/w95 type vfat (rw)


sudo mount -t iso9660 /dev/cdrom /mnt/dvd
> 
user@ubuntu:/media$ sudo mount -t iso9660 /dev/cdrom /mnt/dvd
mount: block device /dev/cdrom is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


dmesg content
> 
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x54
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 64
isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16


Is it something to do with ubuntu being able (but even if not) to play the cd? Even though it seems to be not mounted? If so how do i tell ubuntu to let it go so i can mount it properly?

---

