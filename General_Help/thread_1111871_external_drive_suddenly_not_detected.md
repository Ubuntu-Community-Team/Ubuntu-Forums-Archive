---
title: "external drive suddenly not detected"
date: 2009-03-31
forum: General Help
---

### Post by turvyc on 2009-03-31
Hi all,

So my trusy 230gb usb drive, GEOFF, has for some reason decided to stop appearing when I turn it on. Not even two hours have passed since I turned it off for it to take a rest, and now it turns on fine, but nothing appears.

It's not in its usual spot, /media/GEOFF, nor is /dev/sdc1 there.

I tried lsusb:
```

turvyc@mothership:/media$ sudo lsusb
Bus 004 Device 003: ID 04b8:0005 Seiko Epson Corp. Stylus D88+
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 04b4:6830 Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 to ATA/ATAPI
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I think the Cypress Semiconductor Corp. CY7C68300A EZ-USB AT2 USB 2.0 is my drive . . .

I also tried fdisk:

```

turvyc@mothership:/media$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9539    76621986   83  Linux
/dev/sda2            9540        9726     1502077+   5  Extended
/dev/sda5            9540        9726     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32bbbdc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29611   237850326   83  Linux
/dev/sdb2           29612       30401     6345675    b  W95 FAT32

```

And I tried ls -l /dev/sd*:

```

turvyc@mothership:/media$ ls -l /dev/sd*
brw-rw---- 1 root disk 8,  0 2009-03-31 00:22 /dev/sda
brw-rw---- 1 root disk 8,  1 2009-03-31 00:22 /dev/sda1
brw-rw---- 1 root disk 8,  2 2009-03-31 00:22 /dev/sda2
brw-rw---- 1 root disk 8,  5 2009-03-31 00:22 /dev/sda5
brw-rw---- 1 root disk 8, 16 2009-03-31 00:29 /dev/sdb
brw-rw---- 1 root disk 8, 17 2009-03-31 00:29 /dev/sdb1
brw-rw---- 1 root disk 8, 18 2009-03-31 00:29 /dev/sdb2

```

And then finally I got the output of the kernel log:
```

turvyc@mothership:/media$ dmesg | tail -n 30
[  433.794032] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  433.795404] sd 6:0:0:0: [sdb] Write Protect is off
[  433.795412] sd 6:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  433.795416] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  433.836354] sd 6:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  433.838279] sd 6:0:0:0: [sdb] Write Protect is off
[  433.838288] sd 6:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  433.838291] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  433.838865]  sdb: sdb1 sdb2
[  433.843161] sd 6:0:0:0: [sdb] Attached SCSI disk
[  433.843545] sd 6:0:0:0: Attached scsi generic sg3 type 0
[  652.287958] usb 1-7: USB disconnect, address 9
[  663.052042] usb 1-7: new high speed USB device using ehci_hcd and address 10
[  663.209872] usb 1-7: configuration #1 chosen from 1 choice
[  663.240076] scsi7 : SCSI emulation for USB Mass Storage devices
[  663.243505] usb-storage: device found at 10
[  663.243515] usb-storage: waiting for device to settle before scanning
[  668.240257] usb-storage: device scan complete
[  668.245250] scsi 7:0:0:0: Direct-Access     ST325082 0A               0000 PQ: 0 ANSI: 0
[  668.284264] sd 7:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  668.286069] sd 7:0:0:0: [sdb] Write Protect is off
[  668.286077] sd 7:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  668.286080] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  668.288433] sd 7:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[  668.296093] sd 7:0:0:0: [sdb] Write Protect is off
[  668.296102] sd 7:0:0:0: [sdb] Mode Sense: 27 00 00 00
[  668.296106] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  668.296722]  sdb: sdb1 sdb2
[  668.304100] sd 7:0:0:0: [sdb] Attached SCSI disk
[  668.304482] sd 7:0:0:0: Attached scsi generic sg3 type 0

```

You can see in the log that the drive was detected at 663.052042, but something I don't understand then happened. Any ideas??? Or did my drive just bite the dust? 

Thanks!

EDIT: Oh yes, there are two partitions on the drive: GEOFF, the main ext3 partition, and GEOFFfat32, a small fat32 partition.

---

### Post by klemes on 2009-03-31
Maybe you should just reboot and see if it gets recognised.
Alternatively you can try to disconnect it and reconnect it back on and see if there is any strange output in dmesg.

---

### Post by Spaarkplug on 2009-03-31
Friend I want to comment to this.
First of all,.. please check your persistent udev rules.
Meaning check the files under /etc/udev/rules.d
and somewhere in there among the files, maybe its the 60-persistent-storage.rules( assuming its a usb external drive) there should be an entry for your drive.
I would first make a backup of this file here and then open the file and delete the entry for your drive. study the file before you delete the entry, its written in a certain format. and then connect your drive again.
The reason, I said this is because,.. each time a new usb device is connected to Ubuntu, it makes a persistent entry of the hardware type and info to the udev rules.
Hence, when you do an 'lsusb', most often the info is fetched from here.
So, I would delete the entry in the udev rules for your usb drive and then reconnect your drive, so that way, its a fresh device again, which according to ubuntu never connected before to the machine.
I hope this helps.

Alternatively, you can also connect this drive to a different PC and check if it is functioning.
Thirdly, install memtest on your machine and do a memtest for couple of hours, but wont solve your problem.
I hope the usb subsystem of your kernel is not corrupted by an update or something.
If none of the above works, and the drive detects on other machines, the only possible explanation, though it may seem wild is that the PCI bus chip on your laptop maybe broken/going haywire/flipping a bit (which is known to happen to Dell laptops)

-Spaark

---

### Post by netwarriorwy on 2009-03-31
Nice advices your giving folks. Just for the record, a year ago I had a 160 GB Western Digital external HD, and I had a similar problem. But after doing a thousand things I decided to open up my HD and I realized it was a hardware problem in the circuit that has the sata connection to the portable HD in one side and the mini usb port in the other. Something just stop working at the mini usb port...now Im using that sata portable HD as a regular HD inside one of my desktops.
Good Luck!:guitar:

---

### Post by turvyc on 2009-03-31
> **klemes said:**
> Maybe you should just reboot and see if it gets recognised.
Alternatively you can try to disconnect it and reconnect it back on and see if there is any strange output in dmesg.

I've tried the magic reboot trick a few times to no avail . . . I did, however, get a warning message at the login screen that my $HOME/.dmrc should have 644 permission . . . did that and lost all my icons and desktop stuff . . . changed to 755 and it was OK.

---

### Post by turvyc on 2009-03-31
For the record, I'm running a desktop . . . Dell Dimension 3000, Intel Pentium 2.79Ghz, i686, 512MB, Crappy Intel chipset graphics controller :)

Couldn't find anything in the rules files . . . maybe I just can't decipher the code well enough. In 40-basic-permissions.rules I did change drive permissions from 644 to 755 . . . didn't work . . . bad idea?

It's not the drive itself, because both GEOFF and my 2Gb USB stick work on the upstairs computer, but not here. 

Also, Ubuntu must be detecting the drives, because when neither drive is connected, lsusb doesn't show them, then when one or the other is attached and lsusb is run again, they are there. Is it maybe a mounting problem?

Anyways, I've attached a copy of my 60-persistent-storage.rules file, if anybody is down for a little code-crawling :)

---

### Post by turvyc on 2009-03-31
Okay, I think I got it. Somehow my fstab got all messed up. So I added a new entry:

```

/dev/sdb1	/media/GEOFF		ext3	auto,user,rw,sync	0	0

```

And now it works. Weirdly enough, for a while it kept jumping around from sdb1 to sdc1 . . . any thoughts?

Also, I never knew you are supposed to unmount the drives before disconnecting them . . . #-o

Could this have caused my problem?

EDIT: Here is [the fstab tutorial]("http://www.tuxfiles.org/linuxhelp/fstab.html") I used. VERY helpful.

ANOTHER EDIT: Talking to guy I learned that I shouldn't have to edit the fstab to get the drive to automount . . . HAL should be able to do it for me. Maybe it's a problem with HAL?

FINAL EDIT I SWEAR: I've given up. I'm stuck at manually mounting the drives through bash. The question now is why HAL isn't autodetecting for me.

---

