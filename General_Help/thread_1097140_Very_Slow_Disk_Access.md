---
title: "Very Slow Disk Access"
date: 2009-03-15
forum: General Help
---

### Post by e30power on 2009-03-15
I was running an IDE HD on my NForce2 motherboard, but wanted to upgrade to a SATA HD. I used gParted to copy the partitions (same size HD), and then setup grub to use the new HD. I can boot into it just fine, but the hard drive speed is killing me. Here is the output of hdparm:
```
sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:     2 MB in  9.14 seconds = 224.02 kB/sec
 Timing buffered disk reads:    2 MB in  9.25 seconds = 221.43 kB/sec 
```

```
 sudo hdparm -I /dev/sda

/dev/sda:

ATA device, with non-removable media
	Model Number:       WDC WD400BD-75JMA0                      
	Serial Number:      WD-WMAMA2981315
	Firmware Revision:  05.01C05
Standards:
	Supported: 6 5 4 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:   78125000
	device size with M = 1024*1024:       38146 MBytes
	device size with M = 1000*1000:       40000 MBytes (40 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	DOWNLOAD_MICROCODE
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	SMART error logging
	   *	SMART self-test
	   *	SATA-I signaling speed (1.5Gb/s)
	   *	Host-initiated interface power management
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
Checksum: correct

```

```
lsmod | grep sata
sata_sil               15752  1 
libata                178208  4 pata_acpi,pata_amd,sata_sil,ata_generic
```

Is there something that I need to do to speed up this HD access? Is there a sudo dpkg-reconfigure for HD controllers?

Thanks,
Rob

---

### Post by fatbotgw on 2009-03-15
I don't know how to speed up drive read speeds...not that much knowledge...

However, if you still have the old drive with a copy of your current install why don't you try a fresh install on the new drive.  If it speeds everything up then just copy all your personal files from the old install.

---

