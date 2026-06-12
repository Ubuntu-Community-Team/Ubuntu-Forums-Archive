---
title: "Strange issues mounting USB"
date: 2009-02-18
forum: General Help
---

### Post by mschersten on 2009-02-18
I just got a new mp3 player, a Cowon iAudio U2.  At my desktop, I get cryptic messages, but it doesn't want to mount.  I have no other usb problems; keyboard, mouse, printer, camera, usb storage all work fine.  Here's the output of dmesg after plugging it in:

```
[74118.472044] usb 2-2: new full speed USB device using uhci_hcd and address 7
[74118.676673] usb 2-2: configuration #1 chosen from 1 choice
[74118.712131] scsi7 : SCSI emulation for USB Mass Storage devices
[74118.713809] usb-storage: device found at 7
[74118.713821] usb-storage: waiting for device to settle before scanning
[74123.713296] usb-storage: device scan complete
[74123.717270] scsi 7:0:0:0: Direct-Access     COWON    iAUDIO U2        0100 PQ: 0 ANSI: 4
[74123.736216] sd 7:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[74123.740206] sd 7:0:0:0: [sdb] Write Protect is off
[74123.740223] sd 7:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[74123.740230] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[74123.794273] sd 7:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[74123.797620] sd 7:0:0:0: [sdb] Write Protect is off
[74123.797640] sd 7:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[74123.797647] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[74123.798915]  sdb: sdb1
[74123.812659] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[74123.813732] sd 7:0:0:0: Attached scsi generic sg2 type 0
[74124.420033] usb 2-2: reset full speed USB device using uhci_hcd and address 7
[74124.692034] usb 2-2: reset full speed USB device using uhci_hcd and address 7
[74124.960031] usb 2-2: reset full speed USB device using uhci_hcd and address 7
[74125.228044] usb 2-2: reset full speed USB device using uhci_hcd and address 7
[74125.504048] usb 2-2: reset full speed USB device using uhci_hcd and address 7
[74125.768029] usb 2-2: reset full speed USB device using uhci_hcd and address 7
[74125.917864] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[74125.917888] end_request: I/O error, dev sdb, sector 4100596
[74125.917903] Buffer I/O error on device sdb, logical block 512574
[74126.036046] usb 2-2: reset full speed USB device using uhci_hcd and address 7
[74126.312065] usb 2-2: reset full speed USB device using uhci_hcd and address 7

etc...
```

I can see it recognizes it, and wants to mount it at sdb.  But it does work with my laptop.  I plug it in, it mounts automatically, everything happens like it should.  Here's dmesg from the laptop:

```
[  673.144000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[  673.308000] usb 1-1: configuration #1 chosen from 1 choice
[  673.528000] usbcore: registered new interface driver libusual
[  673.640000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  673.640000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  673.696000] Initializing USB Mass Storage driver...
[  673.696000] scsi2 : SCSI emulation for USB Mass Storage devices
[  673.700000] usb-storage: device found at 2
[  673.700000] usb-storage: waiting for device to settle before scanning
[  673.700000] usbcore: registered new interface driver usb-storage
[  673.700000] USB Mass Storage support registered.
[  678.700000] usb-storage: device scan complete
[  678.704000] scsi 2:0:0:0: Direct-Access     COWON    iAUDIO U2        0100 PQ: 0 ANSI: 4
[  678.708000] sd 2:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[  678.712000] sd 2:0:0:0: [sdb] Write Protect is off
[  678.712000] sd 2:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[  678.712000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  678.720000] sd 2:0:0:0: [sdb] 1025152 2048-byte hardware sectors (2100 MB)
[  678.724000] sd 2:0:0:0: [sdb] Write Protect is off
[  678.724000] sd 2:0:0:0: [sdb] Mode Sense: 3e 00 00 00
[  678.724000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  678.724000]  sdb: sdb1
[  678.732000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  678.732000] sd 2:0:0:0: Attached scsi generic sg2 type 0

```

and I think that these are the lines that I should learn something from:

```
[  673.528000] usbcore: registered new interface driver libusual
[  673.640000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[  673.640000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[  673.696000] Initializing USB Mass Storage driver...
```

Here's lsusb:

```
michael@michael-desktop:~$ lsusb
Bus 002 Device 010: ID 0e21:0600 Cowon Systems, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 001 Device 002: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

I created a directory in /media:

```
michael@michael-desktop:~$ ls /media/
cdrom  cdrom0  mp3

```

Here are my attempts at mounting it:

```
michael@michael-desktop:~$ sudo mount /dev/sdb /media/mp3
mount: /dev/sdb is not a valid block device
michael@michael-desktop:~$ sudo mount /dev/sdb1 /media/mp3
mount: special device /dev/sdb1 does not exist

```

It also doesn't show up on fdisk or in ```
ls -l /dev/disk/by-uuid/
```

Here's some other stuff:
```
michael@michael-desktop:~$ modprobe usbcore
michael@michael-desktop:~$ modprobe -r usbcore
FATAL: Module usbcore is in use.

michael@michael-desktop:~$ lsmod | grep usb
usb_storage            82752  0 
usblp                  20480  0 
libusual               30356  1 usb_storage
usbhid                 35840  0 
hid                    50560  1 usbhid
usbcore               149360  6 usb_storage,usblp,libusual,usbhid,uhci_hcd
scsi_mod              155212  5 usb_storage,sr_mod,sd_mod,sg,libata

```
Any ideas?

---

### Post by Meow27 on 2009-02-18
ok this isnt not muc hhelp but can you asnwer these questions

1. have you updated gvfs (if you havent, good)
2. can you auto-maount usb flash drives?
3. in the menu, do you get an error when trying to open menu ->places -> computer

you make have a problem if 2. or 3. are bad (gvfs should be fixed, but it supposedly stopped usbs from automounting)

---

### Post by mschersten on 2009-02-18
1. I have not (manually) updated gvfs.  Synaptic tells me I'm running 1.0.2-0ubuntu1, and that the latest available version is 1.0.2-0ubuntu2
2. I can automount usb flash drives.
3. I have no errors in menu -> places -> computer.

I guess I'm not clear on what you're saying.  Is it good that I haven't updated gvfs, because that will probably fix it?  Or because updating is a bad idea and will make it worse?

Thanks

---

### Post by mschersten on 2009-02-18
Oh, and I do get to see it in "Computer," but I can't mount it in the GUI, either.  See screenshots below.

---

### Post by Meow27 on 2009-02-18
i only asked, because i thought it was related to a bug which you dont have.

so carry on. i cant be much of help here anymore :<

edit--- by the way, are you sure you are using the right command for mounting it?
last time i tried, i think the name of the usb device was required. 

and you dont have to mount it in /media, you can mount it in /home/username as well

---

### Post by mschersten on 2009-02-18
I'm really not sure that I am using the right mount command.  I was hoping someone could correct me on that.  I think it should be sdb or sdb1, but I'm really not sure.

---

### Post by mschersten on 2009-02-19
OK, so I tried with Knoppix, and I'm having the same problem.  Can anyone tell if this is a hardware problem with my computer?

---

### Post by BrentNewland on 2009-02-19
Could be USB2 related, I see some messages about resetting the "full speed USB device"

see [http://obsidianlake.wordpress.com/2007/09/30/reset-high-speed-usb-device/](http://obsidianlake.wordpress.com/2007/09/30/reset-high-speed-usb-device/)

You might solve it by trying "sudo rmmod uhci-hcd" in the terminal (with no quotes, of course). Or it could be a bad cable.

---

### Post by mschersten on 2009-02-20
Someone over at Linux Forums asked me for this, so it goes here too:

```
michael@michael-desktop:~$ sudo fdisk -l

Disk /dev/sda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39f539f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1        2491    20008926    5  Extended
/dev/sda5            2387        2491      843412+  82  Linux swap / Solaris
/dev/sda6             602        2386    14337981   83  Linux
/dev/sda7               1         600     4819405+  83  Linux

Partition table entries are not in disk order

```

No sign of it.

---

### Post by mschersten on 2009-02-20
Oh, and sudo rmmod uhci_hcd killed my usb keyboard and mouse as soon as I put the command through (but at least it lets me remove it, maybe, unlike modprobe).  When I restarted, uhci_hcd was showing back up in lsmod:

```
michael@michael-desktop:~$ lsmod | grep uhci_hcd
uhci_hcd               30736  0 
usbcore               149360  5 usb_storage,libusual,usbhid,uhci_hcd

```

---

