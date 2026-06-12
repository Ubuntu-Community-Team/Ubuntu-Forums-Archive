---
title: "Intrepid: SATA SError: { Handshk } / hard resetting link Errors  with GDM running"
date: 2009-01-12
forum: General Help
---

### Post by ozra on 2009-01-12
Good day everybody.

Any help with the following would be appreciated:

I noticed "hard resetting link" and SError: { Handshk } SATA errors in dmesg on my Intrepid 8.10 2.6.27-11-generic up to date on 12 Jan 2009 Ubuntu box. (Desktop i386)

It is a Nvidia 8200 Gigabyte GA-M78SM-S2H motherboard (latest Bios installed today). 4 gig Ram. AMD x2 3000 MHz CPU. 1 x 300GB SATA HD + 2 x 750GB SATA HD's. Pioneer SATA DVD writer.

I have apt-get install bonnie to test my HD's

I have the latest NVIDIA binary 180.22 driver installed.

Running bonnie via terminal window in GDM to exercise my HD's I will see dmesg running lots of the following errors ONLY for the two 750 GB HD's (/dev/sdb and /dev/sdc )(no errors get logged for /dev/sda):

[  247.123447] ata2.00: exception Emask 0x10 SAct 0x201 SErr 0x400000 action 0x6 frozen
[  247.123452] ata2.00: irq_stat 0x08000000, interface fatal error
[  247.123455] ata2: SError: { Handshk }
[  247.123459] ata2.00: cmd 61/00:00:cf:ff:2e/04:00:05:00:00/40 tag 0 ncq 524288 out
[  247.123460]          res 40/00:04:cf:ff:2e/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[  247.123462] ata2.00: status: { DRDY }
[  247.123466] ata2.00: cmd 61/40:48:e7:05:2f/02:00:05:00:00/40 tag 9 ncq 294912 out
[  247.123467]          res 40/00:04:cf:ff:2e/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[  247.123469] ata2.00: status: { DRDY }
[  247.123473] ata2: hard resetting link
[  247.604021] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  247.605562] ata2.00: configured for UDMA/133
[  247.605575] ata2: EH complete
[  247.605828] sd 1:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[  247.605842] sd 1:0:0:0: [sdb] Write Protect is off
[  247.605845] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  247.605863] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


The above is an example but gets logged for both sdb and sdc.

I bought a new PSU: Thermaltake 550W (TR2-550) to replace the 300W PSU but the above continues regardless of which PSU I use.

If I kill GDM (/etc/init.d/gdm stop) and run bonnie on either sdb or sdc or on all 3 drives (multiple terminals (f1/F2/F3 and F4 to watch dmesg / messages) simultaneously, no errors get logged. start GDM and the errors multiply continuously. (Except for no errors on sda as stated previously)

Please note: sda is my boot. sdb is not in use but mounted /media/storage1 and sdc is mounted /media/storage2. sdc is used as myth data drive.


If I boot off the Ubuntu 8.10 i386 desktop live CD into GDM: Apt-get install bonnie etc and then run tests, no errors get logged for ANY drives.

Errors only get logged when booting off sda (sda1) and with GDM running (NVIDIA driver 180.22)

The same behaviour is seen with Nvidia 180.11 / 180.18 drivers

Any suggestions on what I can do to stop the SATA reset errors? 

It has now started to cause file corruption on my myth data drive (sdc) fsck fixes it and it is ok for a couple of days after that until it gets too much. ONLY the 750GB drives are affected. Disabling NCQ ( $ echo 1 > /sys/block/sdb/device/queue_depth) and Write caching (hdparm -W0 /dev/sdb)on these two drives does not stop the errors either.

Edit: Using the VESA driver stops the errors from occurring.

Thank You kindly.

Here is some more info:

myth@myth:~$ uname -r
2.6.27-11-generic
myth@myth:~$ sudo hdparm -i /dev/sda
[sudo] password for myth: 

/dev/sda:

 Model=Maxtor 6L300S0                          , FwRev=BANC1G10, SerialNo=L60DMQWG            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=586114704
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

myth@myth:~$ sudo hdparm -i /dev/sdb

/dev/sdb:

 Model=WDC WD7500AACS-00D6B0                   , FwRev=01.01A01, SerialNo=     WD-WCAU41064087
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1465149168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

myth@myth:~$ sudo hdparm -i /dev/sdc

/dev/sdc:

 Model=WDC WD7500AACS-00D6B0                   , FwRev=01.01A01, SerialNo=     WD-WCAU40908795
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=50
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=?0?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=1465149168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode

myth@myth:~$ 
myth@myth:~$ 

dmesg excerpt:

[  247.123447] ata2.00: exception Emask 0x10 SAct 0x201 SErr 0x400000 action 0x6 frozen
[  247.123452] ata2.00: irq_stat 0x08000000, interface fatal error
[  247.123455] ata2: SError: { Handshk }
[  247.123459] ata2.00: cmd 61/00:00:cf:ff:2e/04:00:05:00:00/40 tag 0 ncq 524288 out
[  247.123460]          res 40/00:04:cf:ff:2e/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[  247.123462] ata2.00: status: { DRDY }
[  247.123466] ata2.00: cmd 61/40:48:e7:05:2f/02:00:05:00:00/40 tag 9 ncq 294912 out
[  247.123467]          res 40/00:04:cf:ff:2e/00:00:05:00:00/40 Emask 0x10 (ATA bus error)
[  247.123469] ata2.00: status: { DRDY }
[  247.123473] ata2: hard resetting link
[  247.604021] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  247.605562] ata2.00: configured for UDMA/133
[  247.605575] ata2: EH complete
[  247.605828] sd 1:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[  247.605842] sd 1:0:0:0: [sdb] Write Protect is off
[  247.605845] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[  247.605863] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  247.743411] ata2.00: exception Emask 0x10 SAct 0x7ffef SErr 0x400000 action 0x6 frozen

---

### Post by ozra on 2009-01-12
Follow up to further testing:

For the Nvidia 8200 video card:

Using the VESA driver stops the SATA errors.

Installing Proprietary driver 173 or 177 causes the errors to re-appear.

Installing the binary 180.11 / 180.18 / 180.22 driver causes the errors to re-appear.

Reverting back to the VESA driver causes the errors to stop.

Any help appreciated as I need the proprietary or binary drivers for functionality and 2D acceleration.



Thank You

---

### Post by HwyXingFrog on 2009-08-13
I'm also having the exact same issue, SATA errors on any non OS drive when using NVidia drivers, No problems when running with Vesa Drivers.

Motherboard: Gigabyte GA-M78SM-S2H GF8200

Hard Drives:
 - 1xSeagate 80GB SATA drive running Ubuntu 9.04 on ext3
 - 3xWestern Digital Green Power 1TB trying to run software Raid5 ext3 with mdadm
 - The Raid5 is using Sata ports 4,5, and 6 on the Motherboard (Also tried 2 and 3 and still had errors)

I've tried 3 versions of NVidia GLX Drivers
 - Version 173.14.16 (In Ubuntu apt directory)
 - Version 180.44 (Also in Ubuntu apt directory)
 - Version 190.18 (Beta driver downloaded from NVidia)

I also tried both available Bios versions for the Gigabyte Motherbaord (Version F3l(new) and F1(old)) and both versions have the errors.

All 3 of these drivers caused the following errors when writing to my Raid5 array, I never see any errors on the 80GB hard drive.

The only way I can avoid the Sata errors is to use the default Vesa video drivers that come with Ubuntu, or run the pc without a GUI.

Now, the funny thing, I DO NOT have any Sata errors on a different GF8200 Motherboard, the Asus M3N78-VM, running a Raid5 and LVM with 8 different hard drives and running Nvidia driver 190.16.

```
Aug 13 10:11:54 raidserver kernel: [  284.902332] ata5.00: exception Emask 0x10 SAct 0x3e SErr 0x1800000 action 0x6 frozen
Aug 13 10:11:54 raidserver kernel: [  284.902345] ata5.00: irq_stat 0x08000000, interface fatal error
Aug 13 10:11:54 raidserver kernel: [  284.902353] ata5: SError: { LinkSeq TrStaTrns }
Aug 13 10:11:54 raidserver kernel: [  284.902366] ata5.00: cmd 61/00:08:3f:2c:56/02:00:30:00:00/40 tag 1 ncq 262144 out
Aug 13 10:11:54 raidserver kernel: [  284.902369]          res 40/00:2c:c7:57:56/00:00:30:00:00/40 Emask 0x10 (ATA bus error)
Aug 13 10:11:54 raidserver kernel: [  284.902375] ata5.00: status: { DRDY }
Aug 13 10:11:54 raidserver kernel: [  284.902383] ata5.00: cmd 61/20:10:3f:36:56/00:00:30:00:00/40 tag 2 ncq 16384 out
Aug 13 10:11:54 raidserver kernel: [  284.902386]          res 40/00:2c:c7:57:56/00:00:30:00:00/40 Emask 0x10 (ATA bus error)
Aug 13 10:11:54 raidserver kernel: [  284.902391] ata5.00: status: { DRDY }
Aug 13 10:11:54 raidserver kernel: [  284.902400] ata5.00: cmd 61/30:18:3f:38:56/00:00:30:00:00/40 tag 3 ncq 24576 out
Aug 13 10:11:54 raidserver kernel: [  284.902402]          res 40/00:2c:c7:57:56/00:00:30:00:00/40 Emask 0x10 (ATA bus error)
Aug 13 10:11:54 raidserver kernel: [  284.902526] ata5.00: status: { DRDY }
Aug 13 10:11:54 raidserver kernel: [  284.902547] ata5.00: cmd 61/70:20:cf:45:56/00:00:30:00:00/40 tag 4 ncq 57344 out
Aug 13 10:11:54 raidserver kernel: [  284.902550]          res 40/00:2c:c7:57:56/00:00:30:00:00/40 Emask 0x10 (ATA bus error)
Aug 13 10:11:54 raidserver kernel: [  284.902555] ata5.00: status: { DRDY }
Aug 13 10:11:54 raidserver kernel: [  284.902563] ata5.00: cmd 61/40:28:c7:57:56/00:00:30:00:00/40 tag 5 ncq 32768 out
Aug 13 10:11:54 raidserver kernel: [  284.902566]          res 40/00:2c:c7:57:56/00:00:30:00:00/40 Emask 0x10 (ATA bus error)
Aug 13 10:11:54 raidserver kernel: [  284.902571] ata5.00: status: { DRDY }
Aug 13 10:11:54 raidserver kernel: [  284.902581] ata5: hard resetting link
Aug 13 10:11:55 raidserver kernel: [  285.380573] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 13 10:11:55 raidserver kernel: [  285.385316] ata5.00: configured for UDMA/133
Aug 13 10:11:55 raidserver kernel: [  285.385398] ata5: EH complete
Aug 13 10:11:55 raidserver kernel: [  285.385575] sd 4:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Aug 13 10:11:55 raidserver kernel: [  285.385610] sd 4:0:0:0: [sdc] Write Protect is off
Aug 13 10:11:55 raidserver kernel: [  285.385615] sd 4:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Aug 13 10:11:55 raidserver kernel: [  285.385662] sd 4:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 13 10:11:55 raidserver kernel: [  285.478600] ata5.00: exception Emask 0x10 SAct 0x3 SErr 0x400000 action 0x6 frozen
Aug 13 10:11:55 raidserver kernel: [  285.478611] ata5.00: irq_stat 0x08000000, interface fatal error
Aug 13 10:11:55 raidserver kernel: [  285.478619] ata5: SError: { Handshk }
Aug 13 10:11:55 raidserver kernel: [  285.478631] ata5.00: cmd 61/00:00:3f:e2:55/04:00:30:00:00/40 tag 0 ncq 524288 out
Aug 13 10:11:55 raidserver kernel: [  285.478633]          res 40/00:0c:f7:1c:56/00:00:30:00:00/40 Emask 0x10 (ATA bus error)
Aug 13 10:11:55 raidserver kernel: [  285.478639] ata5.00: status: { DRDY }
Aug 13 10:11:55 raidserver kernel: [  285.478648] ata5.00: cmd 60/d8:08:f7:1c:56/00:00:30:00:00/40 tag 1 ncq 110592 in
Aug 13 10:11:55 raidserver kernel: [  285.478651]          res 40/00:0c:f7:1c:56/00:00:30:00:00/40 Emask 0x10 (ATA bus error)
Aug 13 10:11:55 raidserver kernel: [  285.478661] ata5.00: status: { DRDY }
Aug 13 10:11:55 raidserver kernel: [  285.478673] ata5: hard resetting link
Aug 13 10:11:55 raidserver kernel: [  285.478690] ata4.00: exception Emask 0x10 SAct 0x1 SErr 0x400000 action 0x6 frozen
Aug 13 10:11:55 raidserver kernel: [  285.478694] ata4.00: irq_stat 0x08000000, interface fatal error
Aug 13 10:11:55 raidserver kernel: [  285.478699] ata4: SError: { Handshk }
Aug 13 10:11:55 raidserver kernel: [  285.478708] ata4.00: cmd 61/00:00:3f:e2:55/04:00:30:00:00/40 tag 0 ncq 524288 out
Aug 13 10:11:55 raidserver kernel: [  285.478710]          res 40/00:04:3f:e2:55/00:00:30:00:00/40 Emask 0x10 (ATA bus error)
Aug 13 10:11:55 raidserver kernel: [  285.478715] ata4.00: status: { DRDY }
Aug 13 10:11:55 raidserver kernel: [  285.478721] ata4: hard resetting link
Aug 13 10:11:55 raidserver kernel: [  285.478733] ata6.00: exception Emask 0x10 SAct 0x1 SErr 0x1800000 action 0x6 frozen
Aug 13 10:11:55 raidserver kernel: [  285.478738] ata6.00: irq_stat 0x08000000, interface fatal error
Aug 13 10:11:55 raidserver kernel: [  285.478743] ata6: SError: { LinkSeq TrStaTrns }
Aug 13 10:11:55 raidserver kernel: [  285.478752] ata6.00: cmd 61/00:00:3f:e2:55/04:00:30:00:00/40 tag 0 ncq 524288 out
Aug 13 10:11:55 raidserver kernel: [  285.478754]          res 40/00:04:3f:e2:55/00:00:30:00:00/40 Emask 0x10 (ATA bus error)
Aug 13 10:11:55 raidserver kernel: [  285.478759] ata6.00: status: { DRDY }
Aug 13 10:11:55 raidserver kernel: [  285.478765] ata6: hard resetting link
Aug 13 10:11:55 raidserver kernel: [  285.960557] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Aug 13 10:11:55 raidserver kernel: [  285.962651] ata5.00: configured for UDMA/133
Aug 13 10:11:55 raidserver kernel: [  285.962677] ata5: EH complete
```

---

### Post by specvwillis on 2009-09-21
Any progress with this?  I have the same board and I'm experiencing the same issues, it's getting very frustrating.

---

