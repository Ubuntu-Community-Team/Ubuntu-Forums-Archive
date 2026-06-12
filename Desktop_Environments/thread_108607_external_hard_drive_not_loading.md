---
title: "external hard drive not loading"
date: 2005-12-26
forum: Desktop Environments
---

### Post by jasongrieves on 2005-12-26
Background:
A Venus DS3 Sata to USB 2.0 enclosure with a WD 250 SATA HD.

A post on the web quoted
"Works great with ohci_hcd module, hotplug will pick this up perfectly too."
So I plug this in and my sys log starts going crazy
Dec 25 09:31:55 localhost kernel: [4409554.195000] usb 4-6: new high speed USB device using ehci_hcd and address 5
Dec 25 09:31:55 localhost kernel: [4409554.278000] scsi4 : SCSI emulation for USB Mass Storage devices
Dec 25 09:31:55 localhost kernel: [4409554.279000] usb-storage: device found at
5
Dec 25 09:31:55 localhost kernel: [4409554.279000] usb-storage: waiting for device to settle before scanning
Dec 25 09:31:55 localhost usb.agent[11482]:      usb-storage: already loaded
Dec 25 09:32:00 localhost kernel: [4409559.279000]   Vendor: WDC WD25  Model: 00KS-00MJB0       Rev: 02.0
Dec 25 09:32:00 localhost kernel: [4409559.279000]   Type:   Direct-Access
                ANSI SCSI revision: 04
Dec 25 09:32:00 localhost kernel: [4409559.285000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
Dec 25 09:32:00 localhost kernel: [4409559.285000] sdb: assuming drive cache: write through
Dec 25 09:32:00 localhost kernel: [4409559.287000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
Dec 25 09:32:00 localhost kernel: [4409559.287000] sdb: assuming drive cache: write through
Dec 25 09:32:00 localhost kernel: [4409559.287000]  /dev/scsi/host4/bus0/target0/lun0: unknown partition table
Dec 25 09:32:00 localhost kernel: [4409559.290000] Attached scsi disk sdb at scsi4, channel 0, id 0, lun 0
Dec 25 09:32:00 localhost kernel: [4409559.293000] usb-storage: device scan complete
Dec 25 09:32:00 localhost scsi.agent[11528]:      sd_mod: loaded sucessfully (for disk)
Dec 25 09:32:01 localhost kernel: [4409559.444000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.444000] end_request: I/O error, dev sdb, sector 0
Dec 25 09:32:01 localhost kernel: [4409559.444000] printk: 1 messages suppressed.
Dec 25 09:32:01 localhost kernel: [4409559.444000] Buffer I/O error on device sdb, logical block 0
Dec 25 09:32:01 localhost kernel: [4409559.445000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.445000] end_request: I/O error, dev sdb, sector 8
Dec 25 09:32:01 localhost kernel: [4409559.447000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.447000] end_request: I/O error, dev sdb, sector 0
Dec 25 09:32:01 localhost kernel: [4409559.447000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.447000] end_request: I/O error, dev sdb, sector 16
Dec 25 09:32:01 localhost kernel: [4409559.448000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.448000] end_request: I/O error, dev sdb, sector 24
Dec 25 09:32:01 localhost kernel: [4409559.448000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.448000] end_request: I/O error, dev sdb, sector 32
Dec 25 09:32:01 localhost kernel: [4409559.448000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.448000] end_request: I/O error, dev sdb, sector 40
Dec 25 09:32:01 localhost kernel: [4409559.449000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.449000] end_request: I/O error, dev sdb, sector 48
Dec 25 09:32:01 localhost kernel: [4409559.449000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.449000] end_request: I/O error, dev sdb, sector 56
Dec 25 09:32:01 localhost kernel: [4409559.453000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.453000] end_request: I/O error, dev sdb, sector 512
Dec 25 09:32:01 localhost kernel: [4409559.454000] SCSI error : <4 0 0 0> return code = 0x70000
Dec 25 09:32:01 localhost kernel: [4409559.454000] end_request: I/O error, dev sdb, sector 512
Dec 25 09:32:01 localhost kernel: [4409559.495000] usb 4-6: USB disconnect, address 5

It looks like it is using ehci_hcd and not ohci_hcd.  I don't want to throw ehci_hcd into blacklist as I want to keep all of my other usb devices/hard drives working.  I tried adding ohci_hcd to the usb.rc goofing around with the usb hotplug scripts, but I am afraid I am just scratching the surface.  Internet articles are a bit scant in this area.  

Should I be able to just load with the ohci_hcd module instead of ehci_hcd module?

Thanks!

---

### Post by sciurus on 2005-12-26
Are you sure there aren't physical problems with the device?

---

### Post by jasongrieves on 2005-12-26
[QUOTE=sciurus]Are you sure there aren't physical problems with the device?[/QUOTE]

works fine in Windows.  Did a full format on the disk to be sure.

Perhaps the driver isn't the problem.  Further investigation revealed ehci is the "newer" 2.0 driver, and I would expect it to work with this HD.  Googling the errors on the internet is not much help.  Can't seem to get anywhere with it.

---

### Post by emenny81 on 2005-12-27
I had the same problems with an enclosure, its just like that one you said SATA to USB 2.0, I bought it at pc club, anyways I think its the hardware that is not loading up correctly in linux probably its to rare im getting the same error messages as you, tomorrow im gonna try with one of those maxtor enclosures to see if that works better, I'll post the results here.

---

### Post by jasongrieves on 2005-12-27
[QUOTE=emenny81]I had the same problems with an enclosure, its just like that one you said SATA to USB 2.0, I bought it at pc club, anyways I think its the hardware that is not loading up correctly in linux probably its to rare im getting the same error messages as you, tomorrow im gonna try with one of those maxtor enclosures to see if that works better, I'll post the results here.[/QUOTE]
thanks,

its funny in device manager everything appears to be setting up correctly.  the syslog even shows the correct size, vendor, and product.  its just not able to read/write...

---

### Post by emenny81 on 2005-12-27
in my case its a little different, see if you could check it out to see if the same thing happens in your case.  when I plug the drive in it detects it and it assings a /dev/sda1 but after it finds all the errors and what not it disconects the enclosure and im not able to mount it because its not conected let me post my error messages so you can see.

from the looks of this its either that its not taking the SATA or like I said the hardware of the enclosure, to be honest I just want to make this work jeje

check it out I made a post on this earlier if you want to check it out

[http://www.ubuntuforums.org/showthread.php?t=107026&highlight=usb+hard+drives](http://www.ubuntuforums.org/showthread.php?t=107026&highlight=usb+hard+drives)

[4295186.456000] NTFS driver 2.1.22 [Flags: R/O MODULE].
[4295190.813000] Vendor: Maxtor 6 Model: L200S0 Rev: BANC
[4295190.813000] Type: Direct-Access ANSI SCSI revision: 04
[4295190.831000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295190.831000] sdc: assuming drive cache: write through
[4295190.834000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295190.834000] sdc: assuming drive cache: write through
[4295190.834000] /dev/scsi/host23/bus0/target0/lun0: p1
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
[4295196.611000] Vendor: Maxtor 6 Model: L200S0 Rev: BANC
[4295196.611000] Type: Direct-Access ANSI SCSI revision: 04
[4295196.628000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295196.628000] sdc: assuming drive cache: write through
[4295196.630000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295196.630000] sdc: assuming drive cache: write through
[4295196.630000] /dev/scsi/host24/bus0/target0/lun0: p1
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
[4295202.078000] Vendor: Maxtor 6 Model: L200S0 Rev: BANC
[4295202.078000] Type: Direct-Access ANSI SCSI revision: 04
[4295202.096000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295202.096000] sdc: assuming drive cache: write through
[4295202.099000] SCSI device sdc: 398297088 512-byte hdwr sectors (203928 MB)
[4295202.099000] sdc: assuming drive cache: write through
[4295202.099000] /dev/scsi/host25/bus0/target0/lun0: p1
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

---

### Post by jasongrieves on 2005-12-27
my guess is the enclsure.  my WD is a pretty common drive, i am sure its been used in linux before.  It is going to SCSI and not sata, not sure if this is a problem or not?  I haven't done much research on how linux is handling hard drives...

---

### Post by beameup on 2005-12-27
And my external USB hard drive issue is just a little bit different.

My external USB drive isn't detected during boot up if it's already on. If I switch it on(ByteCC type) after Ubuntu is loaded it detects it and it works just fine. 

Actually I was having a problem with Windows recognizing it. It would take forever to detect it and then it was slow as hell. It was Fat32, I reformatted it to ReiserFS and it's fine.

---

### Post by jasongrieves on 2006-01-11
Good news, Dapper kernel + newest modules seems to correct this problem.  I am building latest kernel in Breezy to determine if .14 kernel fixes this or not.  If nothing posted, just wait until Dapper.

---

