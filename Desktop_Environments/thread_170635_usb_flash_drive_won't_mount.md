---
title: "usb flash drive won't mount"
date: 2006-05-05
forum: Desktop Environments
---

### Post by seatea on 2006-05-05
I have a 128 MB usb flash drive that use to mount when plugged in. Now it won't mount automatically or manually. The  drive shows up in Computer as LEXAR JUMPDRIVE. When I try to mount  it it gives the message: 

"mount: wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

mount: wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Eror: could not execute pmount"

dmesg | tail states:

"[ 2844.242777] ReiserFS: sdb: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb
[ 2844.267204] XFS: bad magic number
[ 2844.267222] XFS: SB validate failed
[ 2844.292790] XFS: bad magic number
[ 2844.292807] XFS: SB validate failed
[ 2852.890927] Inbound IN=eth0 OUT= MAC=00:30:65:c8:fa:f0:00:0b:23:5f:14:b9:08:00 SRC=192.168.0.1 DST=70.143.34.193 LEN=92 TOS=0x00 PREC=0x00 TTL=64 ID=2442 PROTO=ICMP TYPE=8 CODE=0 ID=0 SEQ=1
[ 2906.783222] Inbound IN=eth0 OUT= MAC=00:30:65:c8:fa:f0:00:0b:23:5f:14:b9:08:00 SRC=194.150.129.28 DST=70.143.34.193 LEN=78 TOS=0x00 PREC=0x00 TTL=105 ID=4552 PROTO=UDP SPT=1028 DPT=137 LEN=58
[ 2913.599609] Inbound IN=eth0 OUT= MAC=00:30:65:c8:fa:f0:00:0b:23:5f:14:b9:08:00 SRC=192.168.0.1 DST=70.143.34.193 LEN=92 TOS=0x00 PREC=0x00 TTL=64 ID=2444 PROTO=ICMP TYPE=8 CODE=0 ID=0 SEQ=1
[ 2974.308304] Inbound IN=eth0 OUT= MAC=00:30:65:c8:fa:f0:00:0b:23:5f:14:b9:08:00 SRC=192.168.0.1 DST=70.143.34.193 LEN=92 TOS=0x00 PREC=0x00 TTL=64 ID=2445 PROTO=ICMP TYPE=8 CODE=0 ID=0 SEQ=1
[ 3035.061654] Inbound IN=eth0 OUT= MAC=00:30:65:c8:fa:f0:00:0b:23:5f:14:b9:08:00 SRC=192.168.0.1 DST=70.143.34.193 LEN=92 TOS=0x00 PREC=0x00 TTL=64 ID=2446 PROTO=ICMP TYPE=8 CODE=0 ID=0 SEQ=1"

I have not done  any formatting to  the drive. I use it to transfer files between Ubuntu and  Mac OS 9. It works fine on the Macintosh system. 

Can someone help me out with this problem?

Thanks.

---

### Post by kzutter on 2006-05-05
I wonder if you have a borked entry for sdb in your fstab.
I am also curious what your mtab looks like before  you try to mount it.

---

### Post by seatea on 2006-05-05
Thanks for the input. There is no entry referencing  sdb on my fstab. Here's a copy of my /etc/fstab:

"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda12      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda13      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/sda1       /mnt/ipod       vfat    rw,user,noauto  0       0".

The ipod entry is for an iPodShuffle.

Here's a copy of /etc/mtab:

"/dev/hda12 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
usbfs /proc/bus/usb usbfs rw 0 0
tmpfs /lib/modules/2.6.12-10-powerpc/volatile tmpfs rw,mode=0755 0 0
tmpfs /dev tmpfs rw,size=10M,mode=0755 0 0
none /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0".

Should  I add an entry for the flash drive to fstab? What is puzzling is that it formerly mounted without problem.

---

### Post by ozanmert on 2006-05-05
I have exactly the same problem. My Kingston flash disk used to be mounted automatically, but after I upgraded my system today, I cannot mount it! It is very annoying really. There is a "Kingston DataTraveler 2.0" icon in my Computer folder, but when I click on it, I see: "Unable to mount the selected volume. The volume is probably in a format that cannot be mounted." By the way, I can mount it on my Macintosh.

If this is an ugrade problem, we should be in doubt with Ubuntu's stability.

---

### Post by yyagol on 2006-05-05
i would try commant the line in fstab
/dev/sda1 /mnt/ipod vfat rw,user,noauto 0 0
and then connect the usb key
or to format the usb key and try again.

---

### Post by seatea on 2006-05-05
I commented the line and even rebooted my computer, but nothing happened. I had hoped it might  be something as easy to fix as that. Still trying.

---

### Post by seatea on 2006-05-05
I share your concerns about the updates yesterday. Now when I start my computer into Ubuntu, it flashes a blue Kubuntu logo as the system loads then goes to the gnome display manager. Before, it was the orange Ubuntu logo. I really don't care what color or which logo shows up, but something seems wrong.

---

### Post by kzutter on 2006-05-05
Wow - sounds like some are having problems with an update - I am glad I held off on updating.

Here is my fstab relating to my memory stick(s). Of course, I have the mount points already created. I do not  like kubuntu's automounting, so I usually ignore that and access the mount points instead. Lately however, I have noticed that I must unmount the stick before I pull it out or the files are just 0 byte entries. I used to be able to just pull it out. Maybe this too happened from an update. (Or maybe its just me :-)

# idea for multiuser usb stick mounting from
#[http://www.togaware.com/linux/survivor/Using_Gnome_Volume_Manager.shtml](http://www.togaware.com/linux/survivor/Using_Gnome_Volume_Manager.shtml)

/dev/sda1 /media/usbdisk1 auto users,gid=plugdev,umask=0002,defaults
/dev/sdb1 /media/usbdisk2 auto users,gid=plugdev,umask=0002,defaults
/dev/sdc1 /media/usbdisk3 auto users,gid=plugdev,umask=0002,defaults
/dev/sdd1 /media/usbdisk4 auto users,gid=plugdev,umask=0002,defaults

---

### Post by seatea on 2006-05-06
Ok, after searching this forum I found an answer. Using synaptic, I _completely_ removed gnome-volume-manager and hal along with its various subsets. I had not been aware of hal previously. I then installed them again and the usb drive now mounts. Strangely, Ubuntu now doesn't recognize files from my flash drive that it had previously recognized without problem  unless the file type is appended to the  name, but I can do that for Linux if need be. My Macintosh system doesn't use the file type in the name.

It is disconcerting that something so basic as mounting an usb drive could  get  so involved and take so much time to sort out. I don't know why removing and  installing  the gnome-volume-manager and hal worked or why it became necessary. As I  stated previously, I wasn't even aware of the existence of hal. I think sometimes that Linux  is too complicated a system for me to learn and be able to ever use as my primary desktop os. If these updates wreak havoc on my system, I don't see how I will ever be able to manage to keep things running  smoothly.

---

