---
title: "usb hard drive mount"
date: 2005-12-22
forum: General Help
---

### Post by emenny81 on 2005-12-22
hey guys I've been searching through out the forums on how to mount an usb drive, now so far I've been succesfull mounting other drives but this one I cant, let me explain, when I plug the usb drive into the computer it assigns either sdc or sda, but for some reason it disconects the drive, let me show you the log

[4295186.456000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4295190.813000]   Vendor: Maxtor 6  Model: L200S0            Rev: BANC
[4295190.813000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4295190.831000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295190.831000] sdc: assuming drive cache: write through
[4295190.834000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295190.834000] sdc: assuming drive cache: write through
[4295190.834000]  /dev/scsi/host23/bus0/target0/lun0: p1
[4295190.842000] Attached scsi disk sdc at scsi23, channel 0, id 0, lun 0
[4295190.845000] usb-storage: device scan complete
[4295191.049000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.049000] end_request: I/O error, dev sdc, sector 0
[4295191.049000] printk: 66 messages suppressed.
[4295191.049000] Buffer I/O error on device sdc, logical block 0
[4295191.050000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.050000] end_request: I/O error, dev sdc, sector 8
[4295191.051000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.051000] end_request: I/O error, dev sdc, sector 16
[4295191.051000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.052000] end_request: I/O error, dev sdc, sector 24
[4295191.052000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.052000] end_request: I/O error, dev sdc, sector 32
[4295191.053000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.053000] end_request: I/O error, dev sdc, sector 40
[4295191.053000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.053000] end_request: I/O error, dev sdc, sector 48
[4295191.057000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.057000] end_request: I/O error, dev sdc, sector 56
[4295191.059000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.059000] end_request: I/O error, dev sdc, sector 0
[4295191.061000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.061000] end_request: I/O error, dev sdc, sector 512
[4295191.063000] SCSI error : <23 0 0 0> return code = 0x70000
[4295191.063000] end_request: I/O error, dev sdc, sector 512
[4295191.263000] usb 4-5: USB disconnect, address 26
[4295191.514000] usb 4-5: new high speed USB device using ehci_hcd and address 27
[4295191.605000] scsi24 : SCSI emulation for USB Mass Storage devices
[4295191.611000] usb-storage: device found at 27
[4295191.611000] usb-storage: waiting for device to settle before scanning
[4295196.611000]   Vendor: Maxtor 6  Model: L200S0            Rev: BANC
[4295196.611000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4295196.628000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295196.628000] sdc: assuming drive cache: write through
[4295196.630000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295196.630000] sdc: assuming drive cache: write through
[4295196.630000]  /dev/scsi/host24/bus0/target0/lun0: p1
[4295196.637000] Attached scsi disk sdc at scsi24, channel 0, id 0, lun 0
[4295196.639000] usb-storage: device scan complete
[4295196.734000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.734000] end_request: I/O error, dev sdc, sector 0
[4295196.734000] printk: 10 messages suppressed.
[4295196.734000] Buffer I/O error on device sdc, logical block 0
[4295196.735000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.735000] end_request: I/O error, dev sdc, sector 8
[4295196.735000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.735000] end_request: I/O error, dev sdc, sector 16
[4295196.736000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.736000] end_request: I/O error, dev sdc, sector 24
[4295196.736000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.736000] end_request: I/O error, dev sdc, sector 32
[4295196.737000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.737000] end_request: I/O error, dev sdc, sector 40
[4295196.737000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.737000] end_request: I/O error, dev sdc, sector 48
[4295196.738000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.738000] end_request: I/O error, dev sdc, sector 56
[4295196.750000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.750000] end_request: I/O error, dev sdc, sector 0
[4295196.753000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.753000] end_request: I/O error, dev sdc, sector 512
[4295196.755000] SCSI error : <24 0 0 0> return code = 0x70000
[4295196.755000] end_request: I/O error, dev sdc, sector 512
[4295196.763000] usb 4-5: USB disconnect, address 27
[4295196.779000] scsi24 (0:0): rejecting I/O to dead device
[4295196.996000] usb 4-5: new high speed USB device using ehci_hcd and address 28
[4295197.077000] scsi25 : SCSI emulation for USB Mass Storage devices
[4295197.078000] usb-storage: device found at 28
[4295197.078000] usb-storage: waiting for device to settle before scanning
[4295202.078000]   Vendor: Maxtor 6  Model: L200S0            Rev: BANC
[4295202.078000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[4295202.096000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295202.096000] sdc: assuming drive cache: write through
[4295202.099000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295202.099000] sdc: assuming drive cache: write through
[4295202.099000]  /dev/scsi/host25/bus0/target0/lun0: p1
[4295202.108000] Attached scsi disk sdc at scsi25, channel 0, id 0, lun 0
[4295202.111000] usb-storage: device scan complete
[4295202.284000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.284000] end_request: I/O error, dev sdc, sector 0
[4295202.284000] printk: 11 messages suppressed.
[4295202.284000] Buffer I/O error on device sdc, logical block 0
[4295202.285000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.285000] end_request: I/O error, dev sdc, sector 8
[4295202.285000] Buffer I/O error on device sdc, logical block 1
[4295202.286000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.286000] end_request: I/O error, dev sdc, sector 16
[4295202.286000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.286000] end_request: I/O error, dev sdc, sector 24
[4295202.287000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.287000] end_request: I/O error, dev sdc, sector 32
[4295202.287000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.287000] end_request: I/O error, dev sdc, sector 40
[4295202.288000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.288000] end_request: I/O error, dev sdc, sector 48
[4295202.288000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.288000] end_request: I/O error, dev sdc, sector 56
[4295202.328000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.328000] end_request: I/O error, dev sdc, sector 0
[4295202.330000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.330000] end_request: I/O error, dev sdc, sector 512
[4295202.332000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.332000] end_request: I/O error, dev sdc, sector 512
[4295202.499000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.499000] end_request: I/O error, dev sdc, sector 398283327
[4295202.500000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.500000] end_request: I/O error, dev sdc, sector 398283328
[4295202.501000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.501000] end_request: I/O error, dev sdc, sector 398283329
[4295202.501000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.501000] end_request: I/O error, dev sdc, sector 398283330
[4295202.502000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.502000] end_request: I/O error, dev sdc, sector 398283331
[4295202.503000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.503000] end_request: I/O error, dev sdc, sector 398283332
[4295202.503000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.503000] end_request: I/O error, dev sdc, sector 398283333
[4295202.503000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.503000] end_request: I/O error, dev sdc, sector 398283334
[4295202.507000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.507000] end_request: I/O error, dev sdc, sector 398283327
[4295202.507000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.507000] end_request: I/O error, dev sdc, sector 398283328
[4295202.508000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.508000] end_request: I/O error, dev sdc, sector 398283329
[4295202.508000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.508000] end_request: I/O error, dev sdc, sector 398283330
[4295202.509000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.509000] end_request: I/O error, dev sdc, sector 398283331
[4295202.509000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.509000] end_request: I/O error, dev sdc, sector 398283332
[4295202.510000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.510000] end_request: I/O error, dev sdc, sector 398283333
[4295202.510000] SCSI error : <25 0 0 0> return code = 0x70000
[4295202.510000] end_request: I/O error, dev sdc, sector 398283334
[4295202.513000] usb 4-5: USB disconnect, address 28
[4295202.550000] scsi25 (0:0): rejecting I/O to dead device
[4295202.550000] scsi25 (0:0): rejecting I/O to dead device
[4295202.550000] scsi25 (0:0): rejecting I/O to dead device
[4295202.551000] scsi25 (0:0): rejecting I/O to dead device
[4295202.551000] scsi25 (0:0): rejecting I/O to dead device
[4295202.552000] scsi25 (0:0): rejecting I/O to dead device
[4295202.716000] usb 4-5: new high speed USB device using ehci_hcd and address 29
[4295202.798000] scsi26 : SCSI emulation for USB Mass Storage devices
[4295202.800000] usb-storage: device found at 29
[4295202.800000] usb-storage: waiting for device to settle before scanning
meny@ubuntu:/dev$ 

as you can see here it detects the drive but for some reason its giving out all these i/o errors I know this drive works because I've been using it in my other windows machine just fine, any ideas, I'll show you how I have it in the fstab, see below

/dev/sda1      /media/usbdrive  ntfs    rw,user,noauto,umask=000 0 0

but I check the /dev folder and there's no sd anymore and I have hda(which is my hard drive) and hdc (which is my cd rom), any ideas guys ????

thanks in advance for your help

---

### Post by localzuk on 2005-12-22
First thing I notice is that your fstab line states 'rw'. Have you enabled rw in the kernel (as write access is disabled by default for NTFS as it is 'Experimental' and can mess up an entire disk).

---

