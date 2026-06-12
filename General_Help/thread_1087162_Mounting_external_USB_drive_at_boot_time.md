---
title: "Mounting external USB drive at boot time"
date: 2009-03-04
forum: General Help
---

### Post by Ali_B on 2009-03-04
Hi there,

I wonder if anybody can help me here.

I have an external USB drive which works perfectly fine if i have my machine booted up and running when i plug it in.  However, if i reboot with the drive still connected, it does not appear.  If i try to manually mount it using 'sudo mount -a' i get the error 

mount: special device /dev/disk/by-uuid/4904-C763 does not exist

If the machine has been booted with it connected, i need to remove it and reconnect (or power it off and back on) to see the drive.  I've tried using pysdm once i've reconnected the device and configuring it, but still no luck.

I've looked in lsusb and the device is listed okay.
I've looked in fdisk -l and the device doesn't show.

Dmesg shows a lot of this...

[ 1360.596057] usb 3-2: device descriptor read/64, error -71
[ 1360.812031] usb 3-2: new full speed USB device using uhci_hcd and address 86
[ 1360.936040] usb 3-2: device descriptor read/64, error -71
[ 1361.160063] usb 3-2: device descriptor read/64, error -71
[ 1361.376018] usb 3-2: new full speed USB device using uhci_hcd and address 87
[ 1361.614887] usb 3-2: not running at top speed; connect to a high speed hub
[ 1361.677197] usb 3-2: configuration #1 chosen from 1 choice
[ 1361.708094] scsi100 : SCSI emulation for USB Mass Storage devices
[ 1361.708988] usb-storage: device found at 87
[ 1361.708994] usb-storage: waiting for device to settle before scanning

I'm using Ubuntu 8.10

I really would like the hard drive to be seen at boot time, as i have some services (ccxstream, mt-daapd) which use this drive.

Any ideas folks?

---

### Post by taurus on 2009-03-04
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Ali_B on 2009-03-04
fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c082b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4681    37600101   83  Linux
/dev/sda2            4682        4865     1477980    5  Extended
/dev/sda5            4682        4865     1477948+  82  Linux swap / Solaris


sudo blkid

/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="05598ee6-28a7-49d0-99d5-0993146d2ba3" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="286b8430-fce0-4e51-a510-7c61408e271f" 
/dev/sdb1: LABEL="LOCAL DISK" UUID="4904-C763" TYPE="vfat" 


cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc             proc         defaults                    0  0  
#Entry for /dev/sda1 :
UUID=05598ee6-28a7-49d0-99d5-0993146d2ba3  /                 ext3         relatime,errors=remount-ro  0  1  

#Entry for /dev/sda5 :
UUID=286b8430-fce0-4e51-a510-7c61408e271f  none              swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8       0  0  

UUID=4904-C763                             /media/external1  vfat         auto,defaults    0  0  



df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G   17G   18G  49% /
tmpfs                 374M     0  374M   0% /lib/init/rw
varrun                374M  232K  374M   1% /var/run
varlock               374M     0  374M   0% /var/lock
udev                  374M  2.8M  372M   1% /dev
tmpfs                 374M  428K  374M   1% /dev/shm
lrm                   374M  2.0M  372M   1% /lib/modules/2.6.27-11-generic/volatile


Thanks for your response!

---

### Post by taurus on 2009-03-04
Run this command first.

```
lsusb
```
Then, see if your external drive appears on the list again.  It could take a little time for it to appear so keep checking it.

```
sudo fdisk -l
```

---

### Post by Ali_B on 2009-03-04
lsusb shows me the device

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 003 Device 114: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0d3d:0001 Tangtop Technology Co., Ltd HID Keyboard
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

sudo fdisk -l even after several hours still doesn't show it

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c082b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4681    37600101   83  Linux
/dev/sda2            4682        4865     1477980    5  Extended
/dev/sda5            4682        4865     1477948+  82  Linux swap / Solaris

---

### Post by mempman on 2009-03-04
> **Ali_B said:**
> Hi there,

If i try to manually mount it using 'sudo mount -a' i get the error 

mount: special device /dev/disk/by-uuid/4904-C763 does not exist


Try the following after bootup:

sudo umount /USB-stick
sudo mount /USB-stick

---

### Post by Ali_B on 2009-03-04
alister@hp1:~$ sudo umount /USB-stick
umount: /USB-stick: not found
alister@hp1:~$ sudo mount /USB-stick
mount: can't find /USB-stick in /etc/fstab or /etc/mtab

---

### Post by taurus on 2009-03-04
Can you unplug it?  Then, plug it in and I assume it would automount to /media/disk.  Now, unmount it with

```
sudo umount /media/disk
```
Reboot and see if your external drive appears on the list again after you've logged back in?

```
sudo fdisk -l
```

---

### Post by mempman on 2009-03-04
You might wanna try editing your /etc/fstab so that it references your usb stick with /dev/sdbxx rather than a UUID.  I think UUID are funny on vfat systems, which I'm assuming your usb stick is--vfat.


/dev/sdb1 /media/external1 vfat auto,defaults 0 0


Good Luck.

---

### Post by Ali_B on 2009-03-04
Okay, i had to mess around with my fstab to get things back to where i originally had them where it worked when i plugged it in after the machine was booted.

My fstab entry is now 

UUID=4904-C763   /media/external1  vfat uid=root,owner,gid=users,users,user  0  0 

When i plug the device in, it is automatically picked up and mounts as /media/external1.  I then unmount it and reboot the PC.  It is not shown when the machine boots up.  Strangely it doesn't immediately appear in lsusb, however it does after a short while.  Even after it shows in lsusb it does not show in fdisk -l

Heading for bed now, but will be back tomorrow.  Thanks for your help so far, it's much appreciated!

---

### Post by Ali_B on 2009-03-05
Anybody able to help?

Thanks

---

### Post by Ali_B on 2009-03-06
Bump

---

### Post by persept on 2013-03-21
I have this same problem.  If I plug in the drive after the computer has booted, the drive mounts fine.  If I then reboot, then drive doesn't show up until I unplug and then plug it back in.  It is a USB3 drive, plugged into a USB3 port.  After rebooting with the drive plugged in, the output from lsusb doesn't show the drive at all.  Not sure what to do about this.

---

