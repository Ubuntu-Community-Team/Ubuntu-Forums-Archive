---
title: "USB key won't mount"
date: 2007-01-16
forum: Desktop Environments
---

### Post by dirtside on 2007-01-16
I've got a USB thumb drive (SanDisk 2GB), and when I plug it in, the only way the computer seems to notice is by appending a single line to the end of /var/log/messages:
> 
Jan 16 10:31:11 argo kernel: [20284801.556000] usb 5-8: new high speed USB device using ehci_hcd and address 13

("address 13" started at "address 3" the first time I plugged in the USB key, and has incremented once each time I plugged it back in.)

lsusb returns the following whether or not the device is plugged in:
> 
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 004: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

lsusb -v isn't any more helpful, none of the other devices seem to think there's anything plugged in.

However, if I cat /proc/bus/usb/devices then I get the following (relevant section bolded):

> T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-27-386 ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.7
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=256ms

[B]T:  Bus=05 Lev=01 Prnt=01 Port=07 Cnt=01 Dev#= 13 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0781 ProdID=5406 Rev= 0.10
S:  Manufacturer=SanDisk Corporation
S:  Product=U3 Cruzer Micro
S:  SerialNumber=0000060502057578
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
[/B]
T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-27-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.3
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-27-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-27-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.1
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc= 93/900 us (10%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.15-27-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=046d ProdID=c00c Rev= 6.20
S:  Manufacturer=Logitech
S:  Product=USB Mouse
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=10ms


It knows the key is there, knows what kind of device it is, etc. Notice that it's on USB bus 5, device #13. If I do "ls /proc/bus/usb/005", there's two files: 001 and 013. cat'ing these just produces gibberish data.

Another confounding factor is that I have two SATA hard drives, sda and sdb; sda has Windows XP on it, but I don't use that drive; sdb has Ubuntu on it. Here's the output of fdisk -l:

> Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        9725    78059835    7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          65      522081   82  Linux swap / Solaris
/dev/sdb2              66        9726    77601982+  83  Linux

I've been trying for an hour to figure out how to mount this thing. There's no other sd devices in /dev:

> @@ [root@argo - ~]$ cd /dev
@@ [root@argo - dev]$ ls sd*
brw-rw---- 1 root disk 8,  0 Dec 11 03:55 sda
brw-rw---- 1 root disk 8,  1 Dec 11 03:55 sda1
brw-rw---- 1 root disk 8,  2 Dec 11 03:55 sda2
brw-rw---- 1 root disk 8, 16 Dec 11 03:55 sdb
brw-rw---- 1 root disk 8, 17 Dec 11 03:55 sdb1
brw-rw---- 1 root disk 8, 18 Dec 11 03:55 sdb2
@@ [root@argo - dev]$

And no other devices in /dev that could be the USB key.

Other info:

1. The USB key works perfectly fine in two separate Windows boxes with totally different hardware and software (one XP, one Win2K).
2. The USB key has some kind of bizarre SanDisk software on it that tries to do Happy Fun Things when you plug it into Windows machines -- it's just a pain in the *** and gets in the way in Windows, and presumably would have no effect in Linux.
3. The USB key worked perfectly fine in a DIFFERENT Ubuntu install on another computer; was detected instantly, showed up in Konqueror, etc. That computer has only one hard drive.
4. If I plug in an iPod to a USB port on this computer, it shows the following, but still doesn't seem to mount it (/var/log/messages output):

> Jan 16 10:49:49 argo kernel: [20285919.428000] usb 5-7: new high speed USB device using ehci_hcd and address 14
Jan 16 10:49:50 argo kernel: [20285919.560000] usb 5-7: configuration #1 chosen from 2 choices

5. In the past, a different iPod DID connect to this computer just fine, and was auto-mounted and I was able to copy files to/from it. It's been a month+ since that happened, though, and it's entirely possible that I may have done something bizarrely wonky in the interim.

Thanks in advance for any help anyone can give!

---

### Post by tpg on 2007-01-16
I've also got a SanDisk Cruzer Micro, but it works fine:-k. When I plug it in, "sda" and "sda1" appear in /dev, and the device is automatically mounted (from sda1). /var/log/messages clearly shows a SCSI device being recognised and mounted. I don't have a SATA hard drive, however, and I think this could be causing the problem (especially seeing as it worked on your other computer with only one hard drive). Could you check to see if /dev/sdc or /dev/sdd exist, and if they do see if they refer to the memory stick?

---

### Post by dirtside on 2007-01-16
No other sd devices exist (sdc, sdd, anything). I can look in /dev/bus/usb/ and it's more or less got the same stuff that /proc/bus/usb does, except when there's a file in the proc tree for the new device (the file "013" I mentioned before), there's nothing in /dev/bus/usb to match it:

```
@@ [root@argo - /]$ tree /dev/bus/usb/
/dev/bus/usb/
|-- 001
|   |-- 001
|   `-- 004
|-- 002
|   `-- 001
|-- 003
|   `-- 001
|-- 004
|   `-- 001
`-- 005
    `-- 001

5 directories, 6 files
@@ [root@argo - /]$ tree /proc/bus/usb/
/proc/bus/usb/
|-- 001
|   |-- 001
|   `-- 005
|-- 002
|   `-- 001
|-- 003
|   `-- 001
|-- 004
|   `-- 001
|-- 005
|   |-- 001
|   `-- 015
`-- devices

5 directories, 8 files
```

Is there a way to manually create a device? What piece of software is responsible for creating the device in /dev when a USB key is plugged in?

And as I mentioned before, this very computer HAS in the past successfully recognized and mounted USB mass storage devices (an iPod, at least). But I borrowed a friend's iPod a few minutes ago and plugged it in. Same non-response by the computer, this time; it just won't mount the devices.

Oh, I should also mention that the OTHER Ubuntu computer that this USB drive worked fine on -- the computer with only 1 hard drive -- the HD is also an SATA drive, /dev/sda.

---

### Post by tpg on 2007-01-16
I think the Linux hotplug system (built into the kernel, or a kernel module) is responsible for creating the devices for removeable USB keys. As far as I know, there is no simple way to create a device manually.

Do you have a recent Ubuntu/Kubuntu live CD handy? If you do, you could try booting into that and seeing if your USB key mounts. Also, try creating folders in /mnt on which to mount your hard drives, mount both of them, and then try the USB stick again. If possible, you could also try your friend's iPod.

---

### Post by Pobega on 2007-01-16
Try running a partitioning program (Like gparted) and see if they recognize your device; And if that fails, you can always try from a LiveCD.

---

### Post by tpg on 2007-01-16
I'm pretty sure it won't turn up in any partitioning tool, as it will look for the device in /dev, and it seems like the problem is that it isn't there (i.e. there is no device for the USB stick in /dev). Might as well give it a go though!

---

### Post by Pobega on 2007-01-16
> **tpg said:**
> I'm pretty sure it won't turn up in any partitioning tool, as it will look for the device in /dev, and it seems like the problem is that it isn't there (i.e. there is no device for the USB stick in /dev). Might as well give it a go though!

Well obviously, but computers have been known to do some crazy things.

---

