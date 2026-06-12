---
title: "usb reset after upgrade to 8.10"
date: 2008-10-31
forum: Desktop Environments
---

### Post by rolandbreedveld on 2008-10-31
After upgrade to Ubuntu 8.10 I'm not possible to burn DVD's on my external USB 2.0 device
Hardware: Lenovo T61 with Lite-On USB 2.0 DVD-burner
kernel: 2.6.27-7-generic
when burning a DVD with (example) :
 wodim -v dev=/dev/sr2 DVD.iso
get the error:
Track 01:    4 of 4322 MB written (fifo 100%)   3.8x.Errno: 5   (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 08 1D 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 2C 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x00 (command sequence error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 1.455s timeout 40s
write track data: error after 4253696 bytes
wodim: A write error occured.

in syslog/messages:
kernel: [ 7614.344164] usb 7-2: reset high speed USB device using ehci_hcd and address 4
kernel: [ 7622.040061] usb 7-2: reset high speed USB device using ehci_hcd and address 4
kernel: [ 7624.368121] usb 7-2: reset high speed USB device using ehci_hcd and address 4

tried a lot of stuff, like fill all autosuspend's in /sys with "-1"
and other things I googled, nothing helped
In Ubuntu 8.04 I didn't have these problems, strange while it seems an "old" problem.

hope someone will have a solution for this :( problem.

regards, Roland

Fenestras morituri erant, liber origo causidicus te salutant.

---

### Post by TheCompWIz on 2008-11-14
I'm running into the exact same problem... something new with 8.10 :(  in addition, randomly, alsa locks up randomly...   I wonder if there's a problem with the forcedeth driver in 8.10.

*edit* ... just noticed tho... mine is ohci... and it's a low-speed device... 

[ 1210.221821] usb 1-3: reset low speed USB device using ohci_hcd and address 3

in this case... it's my mouse.... which really sucks when it causes the usb stack to die.

---

### Post by batistuta on 2008-11-25
I'm having same issue with a Lenovo T61 and with my external hard drive. Have also tried changing max_sectors to no avail.

Have also tried with a different distro (system rescueCD using 2.6.25-r4) and even with a pcmcia USB adaptor. Same issue, USB hardware reset.

However, this problem doesn't happen in Windows. It seems to be a Linux problem. Will try with an older kernel to see if it makes a difference.

---

### Post by ronniet on 2008-12-30
Same here, I get:

*reset high speed USB device using ehci_hcd*

when I'm trying to transfer songs to my iPod Classic  :(

---

### Post by bsmith1051 on 2008-12-31
> **TheCompWIz said:**
> usb 1-3: reset low speed USB device using ohci_hcd and address 3
it's my mouse.... which really sucks when it causes the usb stack to die.
Are you saying that everything works properly if you unplug the mouse?

---

