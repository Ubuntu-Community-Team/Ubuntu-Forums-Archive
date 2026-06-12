---
title: "Can't mount external usb cd/rw drive"
date: 2005-08-05
forum: Desktop Environments
---

### Post by spencer on 2005-08-05
Hi,

I've tried editing /etc/fstab by adding '/dev/sr0 /media/cdrom1 udf,iso9660 ro,user,noauto 0 0' to it. I then unplug the drive and reconnect and with an audio cd in the drive the cd player program opens but will not play cd. Here is my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sr0        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
``` 

I also ran 'dmesg' and get the following:

```
t: I/O error, dev sr0, sector 1024
UDF-fs: No partition found (1)
end_request: I/O error, dev sr0, sector 64
isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
end_request: I/O error, dev sr0, sector 64
isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
usb 1-1: USB disconnect, address 2
usb 1-1: new full speed USB device using uhci_hcd and address 3
scsi1 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 3
usb-storage: waiting for device to settle before scanning
  Vendor: AOPEN     Model: CD-RW CRW4048     Rev: 1.07
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr0: scsi-1 drive
Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi1, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete
sg_write: data in/out 56/56 bytes for SCSI command 0x12--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 26/26 bytes for SCSI command 0x5a--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
usb 1-1: USB disconnect, address 3
usb 1-1: new full speed USB device using uhci_hcd and address 4
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: AOPEN     Model: CD-RW CRW4048     Rev: 1.07
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr1 at scsi2, channel 0, id 0, lun 0
Attached scsi generic sg1 at scsi2, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete
printk: 8 messages suppressed.
sg_write: data in/out 56/56 bytes for SCSI command 0x12--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 26/26 bytes for SCSI command 0x5a--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
scsi1 (0:0): rejecting I/O to dead device
SCSI error: host 1 id 0 lun 0 return code = 4000000
        Sense class 0, sense error 0, extended sense 0
scsi1 (0:0): rejecting I/O to dead device
sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 00 00 00 00 00 00 00 02 00
sr: old sense key No Sense
Non-extended sense class 0 code 0x0
usb 1-1: USB disconnect, address 4
usb 1-1: new full speed USB device using uhci_hcd and address 5
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 5
usb-storage: waiting for device to settle before scanning
  Vendor: AOPEN     Model: CD-RW CRW4048     Rev: 1.07
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi3, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi3, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete
printk: 8 messages suppressed.
sg_write: data in/out 56/56 bytes for SCSI command 0x12--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 26/26 bytes for SCSI command 0x5a--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
usb 1-1: USB disconnect, address 5
usb 1-1: new full speed USB device using uhci_hcd and address 6
scsi4 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 6
usb-storage: waiting for device to settle before scanning
  Vendor: AOPEN     Model: CD-RW CRW4048     Rev: 1.07
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr1: scsi-1 drive
Attached scsi CD-ROM sr1 at scsi4, channel 0, id 0, lun 0
Attached scsi generic sg1 at scsi4, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete
printk: 8 messages suppressed.
sg_write: data in/out 56/56 bytes for SCSI command 0x12--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 26/26 bytes for SCSI command 0x5a--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
usb 1-1: USB disconnect, address 6
usb 1-1: new full speed USB device using uhci_hcd and address 7
scsi5 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 7
usb-storage: waiting for device to settle before scanning
  Vendor: AOPEN     Model: CD-RW CRW4048     Rev: 1.07
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr1: scsi-1 drive
Attached scsi CD-ROM sr1 at scsi5, channel 0, id 0, lun 0
Attached scsi generic sg1 at scsi5, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete
printk: 8 messages suppressed.
sg_write: data in/out 56/56 bytes for SCSI command 0x12--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 26/26 bytes for SCSI command 0x5a--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
scsi3 (0:0): rejecting I/O to dead device
SCSI error: host 3 id 0 lun 0 return code = 4000000
        Sense class 0, sense error 0, extended sense 0
scsi3 (0:0): rejecting I/O to dead device
sr0: CDROM (ioctl) error, command: Xpwrite, Read disk info 00 00 00 00 00 00 00 02 00
sr: old sense key No Sense
Non-extended sense class 0 code 0x0
usb 1-1: USB disconnect, address 7
usb 1-1: new full speed USB device using uhci_hcd and address 8
scsi6 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 8
usb-storage: waiting for device to settle before scanning
  Vendor: AOPEN     Model: CD-RW CRW4048     Rev: 1.07
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi6, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi6, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete
printk: 8 messages suppressed.
sg_write: data in/out 56/56 bytes for SCSI command 0x12--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 26/26 bytes for SCSI command 0x5a--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
usb 1-1: USB disconnect, address 8
usb 1-1: new full speed USB device using uhci_hcd and address 9
scsi7 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 9
usb-storage: waiting for device to settle before scanning
  Vendor: AOPEN     Model: CD-RW CRW4048     Rev: 1.07
  Type:   CD-ROM                             ANSI SCSI revision: 00
sr0: scsi-1 drive
Attached scsi CD-ROM sr0 at scsi7, channel 0, id 0, lun 0
Attached scsi generic sg0 at scsi7, channel 0, id 0, lun 0,  type 5
usb-storage: device scan complete
printk: 8 messages suppressed.
sg_write: data in/out 56/56 bytes for SCSI command 0x12--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 26/26 bytes for SCSI command 0x5a--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
printk: 8 messages suppressed.
sg_write: data in/out 56/56 bytes for SCSI command 0x12--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 26/26 bytes for SCSI command 0x5a--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
sg_write: data in/out 12/12 bytes for SCSI command 0x43--guessing data in;
   program gnome-cd not setting count and/or reply_len properly
end_request: I/O error, dev sr0, sector 64
isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
``` 

I would appreciate any help. 

Thank you,

-spencer

---

### Post by mike998 on 2005-08-05
Is this powered?
Are you plugging into a non-powered USB port - I had a similar problem with a USB Hard Drive and had to plug it into one of my powered USB ports on my laptop.  When I plugged it into one of the ports of my pocket USB hub, it wouldn't work.

---

### Post by spencer on 2005-08-05
Thanks for the reply.

If you are talking about whether the computer has usb power to it. I assume  it is powered by computer. 

It's an older Gateway E 3400. I have fedora on another hard drive and it automatically detects it. This gives me an idea I just thought of and that is to check my fstab in Fedora. Didn't think to do this. I'll check it out.

---

### Post by spencer on 2005-08-05
Just checked Fedora and this is what I have in fstab:

'/dev/scdO /media/cdrecorder auto'

I tried '/dev/scdO /media/cdrecorder auto' in Ubuntu's fstab and it's apparent that Ubuntu's fstab is not the same format as Fedora.

The computer detects cd/rw, it just won't mount so that I can use it.  :-x 

-spencer

---

### Post by spencer on 2005-08-05
I got the recorder to play an audio cd, so I know it is detected I just can't mount the the cd to view its content. I added '/dev/scdO /media/cdrecorder auto' to fstab again and unplugged recorder and this time for some reason it was able to play the audio cd.

I tried 'sudo mount /dev/scdO media/cdrecorder auto' and that didn't work either. So, what other options do I have to mount the recorder?

-spencer

---

### Post by spencer on 2005-08-08
"bump"

What else can I check?

Thanks,

-spencer

---

### Post by spencer on 2005-08-09
I solved the problem.  \\:D/  

I added '/dev/scdO	/media/cdrecorder auto iso9660 ro,noauto0	0' to /etc/fstab again and played around with the spacing and finally got it right. I must have had some spaces in the wrong place because I previouly entered the same as the above to /etc/fstab and it didn't work. It's working now though and I'm happy again.  :smile:   

-spencer

---

### Post by phenix on 2006-03-24
hello spencer I am having the same problem with my Plextor 504UF and was wandering if you could help me out.. I was looking at the line you put in on the /etc/fstab file " /dev/scdO /media/cdrecorder auto iso9660 ro,noauto0 0", but I cant figure out where to find the info to type in the fstab file 

Im running ubunt on a G3 Pismo Power Book 500mhz

thanks

---

### Post by spencer on 2006-04-11
Hello phenix,

You may have fixed this by now but I'll try anyhow. My original post was when I was using a Gateway 3400 PC desktop, so I'm not sure how it will work for your Pismo. Here is what I have in my /etc/fstab taken from one of my Pismo's:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda11      /               ext3    defaults,errors=remount-ro 0       1
/dev/hda12      none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```



The "/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0" line is where my cd/rw is located. Maybe you can simply change yours to that. 

I hope this helps you and you get it fixed.

-spencer

---

### Post by janesmate on 2006-09-21
Hi

Very much a newbie - so apologies if i seem a bit dense

I seem to be having the same problem as other users trying to "mount" my CDRW USB drive. USB drive works fine for other USB devices (camera, pendrive, mouse), but no response when I plug in my new CDRW. It doesn't even pop up to read audio or data CDs

I gather you need to run dmesg to get some info, so here's what I get plugging and unplugging (these seem to be the relevant lines):

[17179800.388000] usb 1-1.3: new full speed USB device using uhci_hcd and address 4
[17179803.460000] usb 1-1.3: device descriptor read/64, error -110


As I say, I'm a very low-skill user, so am a little bit scared of getting my hands dirty in code. Any plain-English help would be massively appreciated


Cheers!

:)

---

