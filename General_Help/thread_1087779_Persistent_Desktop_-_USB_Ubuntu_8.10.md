---
title: "Persistent Desktop - USB Ubuntu 8.10"
date: 2009-03-05
forum: General Help
---

### Post by essoid on 2009-03-05
Hi guys,

I need some help .. when I boot from Usb stick It goes to BusyBox ..

My machine: FUTRO S400 (FujitsuSiemens) 

I've attached casper.log file ..

I have installed GRUB loader, and this is my menu.lst:

title           Persistent Desktop
root            (hd0,0)
kernel          /casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper debug --
#kernel          /casper/vmlinuz boot=casper persistent ramdisk_size=1048576 root=/dev/ram rw quiet splash --
initrd          /casper/initrd.gz
boot

Please help, I'm stuck with this problem.

Thank you

---

### Post by ju2wheels on 2009-03-05
Those pictures are way too big, can you edit them out and just link them or upload them to an external service like tinypic.com .

Lets start off by how did you make this bootable/persistent USB drive (what process or tutorial) to make sure that is correct and there arent problems with your persistent setup. Ive also run into instances where USB isntallation refused to work on a desktop (so also double checking if you can boot to a LiveCD if possible is a good idea as well).

---

### Post by essoid on 2009-03-05
Hi again,

I did this here on my 8gb usbstick

sudo parted -s /dev/sdb mkpart primary fat32 100%

sudo parted -s /dev/sdb set 1 boot on

sudo mkfs.vfat -F 32 -n ubuntu8 /dev/sdb1

sudo mount /dev/sdb1 /media/ubuntu8

cd /media/ubuntu8

dd if=/dev/zero of=casper-rw bs=1M count=4096 

sudo mkfs.ext2 -F casper-rw 

sudo mount -o loop ubuntu810-desktop.sio /media/cdrom

cd /media/cdrom

cp -rf casper dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines install/mt86plus /media/ubuntu8

grub-install --root-directory=/media/ubuntu8 --no-floppy /dev/sdb

cd /media/ubuntu8/boot/grub

changed device.map -> (hd0) /dev/sdb

created menu.lst:

title Persistent Desktop
root (hd0,0)
kernel /casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper debug --
#kernel /casper/vmlinuz boot=casper persistent ramdisk_size=1048576 root=/dev/ram rw quiet splash --
initrd /casper/initrd.gz
boot

thats it .. I hope that can help you ..

thanks for answearing mate :)

edit:

this is from casper.log:

+ sysdev=/block/sda
+ /sbin/udevadm info -q name -p /block/sda
+ echo sda
+ echo /dev/sda
+ devname=/dev/sda
+ get_fstype /dev/sda
+ local FSTYPE
+ local FSSIZE
/init: line 1: cannot open /dev/sda: no such file
+ fstype
+ eval
+ [  != unknown ]
+ echo
+ return 0
+ fstype=
.
.
.
+ get_fstype /dev/sda1
+ local FSTYPE
+ local FSSIZE
+ fstype
+ eval FSTYPE=ext2 FSSIZE=512999424
+ FSTYPE=ext2 FSSIZE=512999424
+ [ ext2 != unknown ]
+ echo ext2
+ return 0
+ fstype=ext2
+ is_supported_fs ext2
+ fstype=ext2
+ return 0
+ mount -t ext2 -o ro,noatime /dev/sda1 /cdrom
mount: mounting /dev/sda1 on /cdrom failed: Invalid argument
+ continue
+ check_dev /sys/block/sda/sda2
+ sysdev=/sys/block/sda/sda2
+ devname=
+ skip_uuid_check=
.
.
.
+ fstype
+ eval FSTYPE=ext2 FSSIZE=512999424
+ FSTYPE=ext2 FSSIZE=512999424
+ [ ext2 != unknown ]
+ echo ext2
+ return 0
+ mount -t ext2 -o ro /dev/sda1 /snap-backing
mount: mounting /dev/sda1 on /snap-backing failed: Invalid argument
+ panic Cannot mount /dev/sda1 on /snap-backing
+ [ -x /sbin/usplash_write ]
+ /sbin/usplash_write QUIT
+ chvt 1
+ [ -n  ]
+ modprobe i8042
+ modprobe atkbd
+ echo Cannot mount /dev/sda1 on /snap-backing
+ PS1=(initramfs)  /bin/sh -i

this is the end of casper.log

---

### Post by ju2wheels on 2009-03-05
Alright well if im following that correctly, you make the entire stick FAT32 then grew out an ext2 casper-rw file sys for the persistence, but I think whats happening is since /dev/sdb1 is FAT32 you are losing all the file permissions when you copy the files from the CD. Linux needs those permissions set correctly in order for it to work at all, therefore I would try not making the partition FAT32 (or NTFS).

Theres a program out there similar to Unetbootin that does this automatically for you though I dont remember the name, Ill have to look it up.

---

### Post by essoid on 2009-03-05
Hi mate,

that can be the solustion .. to pack it with tar and then extract it into usbstick? and not to copy it direct to usbstick? right? so the filepermission will be there after extracting it direct to usbstick?

I think it breaks because of this here:

/init: line 1: cannot open /dev/sda: no such file

+ mount -t ext2 -o ro /dev/sda1 /snap-backing
mount: mounting /dev/sda1 on /snap-backing failed: Invalid argument

+ echo Cannot mount /dev/sda1 on /snap-backing
+ PS1=(initramfs) /bin/sh -i

what is /dev/sda? why is he searching for it? I dont get it .. and this SNAP-BACKING? Could some1 please explain it to me ..

Thanks in advanced

edit:

do I need to extract initrd.gz and to edit casper script?

does someone has nice HOWTO (step-by-step on linux console) make persistent ubuntu 8.10 on 8gb usbstick?

thanks

---

### Post by ju2wheels on 2009-03-05
/dev/sda is typically the first hard drive on your pc and /dev/sda1 the first partition on that hard drive.

I think you may have actually meant to create two partitions but ended up only creating one.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) Method 3 seems like what you want.

Alternatively theres also pendrive's tutorial. Hope one of these helps.. [http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

---

### Post by essoid on 2009-03-05
I followed so many howto's but that did not helped me a lot .. i tried tools from Ubuntu like CREATE BOOTABLE USB STICK, installed tool like PORTABLELINUX and in the end nothing .. same **** landing into BusyBox :(

on my first harddrive is [http://www.nexterminal.com/english/products/elux_ng]("http://www.nexterminal.com/english/products/elux_ng") eLUX OS .. its some kind of TERMINAL .. but I dont know why is he trying to mount /dev/sda .. 

and what is snap-backing?

---

### Post by essoid on 2009-03-06
Hi again,

I did it from start again .. 

- gparted my 8gb usbstick with FAT32

- connected my external cdrom, loaded ubuntu cd, turned my PC on (FS400 Terminal client from FujitsuSiemens with eLUX OS) and ubuntu 8.10 booted normaly up

- Created a USB startup disk with UBUNTU CREATE A USB STARTUP DISK successfully

when I try to boot with usbstick it goes to Busybox .. 

and here is my screenshot .. maybe someone know how to fix this .. I think somethings wrong with initrd.gz .. maybe I'm wrong?

[IMG]http://i40.tinypic.com/25q3u44.jpg[/IMG]

and this is my Terminal FS400 .. check it out .. 

[IMG]http://i41.tinypic.com/25zle7a.jpg[/IMG]

and here we go ... one more .. cat /proc/mounts

[IMG]http://i42.tinypic.com/213hflu.jpg[/IMG]

any ubuntu guru around? :)

please help me :( 

:)

edit: I attached dmesg.txt .. maybe someone can find out why this message with cant mount /dev/sda1 etc appears ..

---

### Post by dstempfley on 2009-06-05
It's been a couple of months.  Did you get this resolved?  

I had the same problem and discovered that the problem is likely in the casper script.  It seems to be related to udev not creating the /dev/sda device before the get_fstype function is called from find_livefs().

Sorry I don't have direct access to my changes right now, so I can't send you a diff or copy of my casper.  But, when I add "/sbin/udevadm settle" in find_livefs() before the loop "for sysblock in $(echo /sys/block/* ... " the error goes away. 

I don't know enough about udev to know I this is a real fix or just masked the problem temporarily.

/Dion

---

