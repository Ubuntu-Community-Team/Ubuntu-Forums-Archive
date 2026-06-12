---
title: "[SOLVED] Linux confused"
date: 2008-12-11
forum: General Help
---

### Post by osurshaney on 2008-12-11
I have two drives. One CD-RW and one DVD-RW. In the properties for the drives they are reversed. The CD has the properties for the DVD, and there are no drive properties for the DVD-RW. The CD will accept and mount and burn CD's but when I try the DVD I get no error until I manually try to mount the volume. Then I get the 'unable to mount volume' error. Any ideas?

---

### Post by taurus on 2008-12-11
How many entries do you have in /etc/fstab for your CD/DVD drives?

```
cat /etc/fstab
```

---

### Post by osurshaney on 2008-12-11
This is what I show in terminal.  I'm a lil' new to this. Please bear with me

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fc6ef9e3-0c78-4dcc-9c63-618207f93b8a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b14b98da-1b35-410d-839b-0649bafaa7c8 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by osurshaney on 2008-12-11
This is what I show in terminal.  I'm a lil' new to this. Please bear with me

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fc6ef9e3-0c78-4dcc-9c63-618207f93b8a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b14b98da-1b35-410d-839b-0649bafaa7c8 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by taurus on 2008-12-11
Your DVD drive is probably /dev/scd0.  

Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
```
Save it and close down gedit window.  Then, create a new mount point for it.

```
sudo mkdir /media/cdrom1
```
Reboot and see if both drives work now.

---

### Post by LowSky on 2008-12-11
Mkae sure you connected the drives correctly to the motherboard.

Make sure that one drive is Master and the Other is SLave Cable select seems to never work properly, and that you using the correct cable connection (master uses the middle IDE cable connecter, the slave the one on the end), also make sure its a 80 PIN cable, opposed to a 40 Pin cable, this may cause some issues with media being read, like music CDs)

---

### Post by osurshaney on 2008-12-11
should it look something like this
 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=fc6ef9e3-0c78-4dcc-9c63-618207f93b8a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b14b98da-1b35-410d-839b-0649bafaa7c8 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/scd0 	/media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0 	  0



because after I input the information I get this response in terminal-

mkdir: cannot create directory `/media/cdrom1': File exists

---

### Post by osurshaney on 2008-12-11
yes it is all connected properly  I have a sneaky suspicion it is just not recognizing it.

---

### Post by taurus on 2008-12-11
You can also look in /var/log/messages to see if the kernel detects both drives during boot up.

```
sudo more /var/log/messages
```
Hit Space key for the next 24 lines.

---

### Post by osurshaney on 2008-12-11
the answer is very long

---

### Post by taurus on 2008-12-11
Hit the Space bar for the next 24 lines until you see some lines about your CD/DVD drives.

---

### Post by osurshaney on 2008-12-11
It's there

Dec  8 10:27:33 home-desktop kernel: [    3.263597] ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 20
Dec  8 10:27:33 home-desktop kernel: [    3.552017] usb 1-2: new low speed USB device using ohci_hcd and address 3
Dec  8 10:27:33 home-desktop kernel: [    3.728041] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec  8 10:27:33 home-desktop kernel: [    3.765202] usb 1-2: configuration #1 chosen from 1 choice
Dec  8 10:27:33 home-desktop kernel: [    3.777657] ata1.00: ATA-7: MAXTOR STM3320620AS, 3.AAE, max UDMA/133
Dec  8 10:27:33 home-desktop kernel: [    3.777660] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec  8 10:27:33 home-desktop kernel: [    3.844303] ata1.00: configured for UDMA/133
Dec  8 10:27:33 home-desktop kernel: [    4.072020] usb 1-4: new full speed USB device using ohci_hcd and address 4
Dec  8 10:27:33 home-desktop kernel: [    4.156120] scsi 0:0:0:0: Direct-Access     ATA      MAXTOR STM332062 3.AA PQ: 0 ANSI: 5
Dec  8 10:27:33 home-desktop kernel: [    4.159189] scsi2 : pata_amd
Dec  8 10:27:33 home-desktop kernel: [    4.159968] scsi3 : pata_amd
Dec  8 10:27:33 home-desktop kernel: [    4.161543] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Dec  8 10:27:33 home-desktop kernel: [    4.161546] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15Dec  8 10:27:33 home-desktop kernel: [    4.533178] scsi 2:0:0:0: CD-ROM            SONY     DVD RW AW-G170A  1.71 PQ: 0 ANSI: 5
Dec  8 10:27:33 home-desktop kernel: [    4.533649] scsi 2:0:1:0: CD-ROM            LITE-ON  LTR-48246S       SPS1 PQ: 0 ANSI: 5
Dec  8 10:27:33 home-desktop kernel: [    4.284197] usb 1-4: configuration #1 chosen from 1 choice
Dec  8 10:27:33 home-desktop kernel: [    4.290103] hub 1-4:1.0: USB hub found
Dec  8 10:27:33 home-desktop kernel: [    4.293078] hub 1-4:1.0: 3 ports detected
Dec  8 10:27:33 home-desktop kernel: [    4.500314] ata3.00: ATAPI: SONY    DVD RW AW-G170A, 1.71, max UDMA/66
Dec  8 10:27:33 home-desktop kernel: [    4.500329] ata3.01: ATAPI: LITE-ON LTR-48246S, SPS1, max UDMA/33
Dec  8 10:27:33 home-desktop kernel: [    4.516250] ata3.00: configured for UDMA/33
Dec  8 10:27:33 home-desktop kernel: [    4.532219] ata3.01: configured for UDMA/33
[B]Dec  8 10:27:33 home-desktop kernel: [    4.533178] scsi 2:0:0:0: CD-ROM            SONY     DVD RW AW-G170A  1.71 PQ: 0 ANSI: 5
Dec  8 10:27:33 home-desktop kernel: [    4.533649] scsi 2:0:1:0: CD-ROM            LITE-ON  LTR-48246S       SPS1 PQ: 0 ANSI: 5[/B]
Dec  8 10:27:33 home-desktop kernel: [    4.540722] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Dec  8 10:27:33 home-desktop kernel: [    4.540759] scsi 2:0:0:0: Attached scsi generic sg1 type 5
Dec  8 10:27:33 home-desktop kernel: [    4.540791] scsi 2:0:1:0: Attached scsi generic sg2 type 5
Dec  8 10:27:33 home-desktop kernel: [    4.556526] Driver 'sd' needs updating - please use bus_type methods
Dec  8 10:27:33 home-desktop kernel: [    4.557215] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec  8 10:27:33 home-desktop kernel: [    4.557232] sd 0:0:0:0: [sda] Write Protect is off
Dec  8 10:27:33 home-desktop kernel: [    4.557258] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  8 10:27:33 home-desktop kernel: [    4.557327] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
Dec  8 10:27:33 home-desktop kernel: [    4.557341] sd 0:0:0:0: [sda] Write Protect is off
Dec  8 10:27:33 home-desktop kernel: [    4.557367] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec  8 10:27:33 home-desktop kernel: [    4.557371]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Dec  8 10:27:33 home-desktop kernel: [    4.575392]  sda1 sda2 < sda5 > sda3

---

### Post by osurshaney on 2008-12-11
I'm guessing this means the kernel is seeing the two drives?

---

### Post by osurshaney on 2008-12-11
In the properties of the drive it says the permissions could not be determined.

---

