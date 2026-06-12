---
title: "Possible Bug?  Qlogic Firmware on Ubuntu Server 08.10"
date: 2009-04-06
forum: General Help
---

### Post by rednerd on 2009-04-06
I tried to post this in the server section but I don't have permissions.  

A couple of weekends ago I migrated my primary file server from a Debian 3.1 box running a custom kernel (Fibre Channel, BigMem, and RID support) to Ubuntu 8.10.  My only issue was that the driver for my Qlogic QLA2310 fibre channel card wouldn't boot out of the box.   Once the machine was booted I could run modprobe qla2xxx and the driver would come up but that isn't a good thing on a semi-mission-critical file server.

I received this hint from the qla2xxx driver in the dmesg:
Firmware image unavailable.
Firmware images can be retrieved from: [ftp://ftp.qlogic.com/outgoing/linux/firmware/](ftp://ftp.qlogic.com/outgoing/linux/firmware/).
Failed to initialize adapter.


It turns out the firmware (ql2300_fw.bin) is installed in /lib/firmware by default from the linux-firmware package.  However, a link needs to  be made from /lib/firmware/ql2300.bin to /lib/firmware/<KERNEL VERSION>/ in order for it to be included with initrd using `update-initramfs`.

Once I made the symbolic link and ran update-initramfs the firmware loaded on boot.  Unfortunately, this will only last so long as the kernel doesn't get updated automatically and the server subsequently rebooted.

Please let me know if this is a known issue or if I should file a bug report.

---

### Post by LinuxPhotographer on 2009-04-18
I just encountered the identical issue when installing on a Dell Qlogic machine.

Any updates on how to correct this issue would be appreciated.

---

### Post by herroy on 2009-05-07
Hey, I get this error in my dmesg
```
[   63.120060] qla2xxx 0000:03:0d.0: Firmware image unavailable.
[   63.120110] qla2xxx 0000:03:0d.0: Firmware images can be retrieved from: ftp://ftp.qlogic.com/outgoing/linux/firmware/.
[   63.120162] qla2xxx 0000:03:0d.0: Failed to initialize adapter
[   63.120236] qla2xxx 0000:03:0d.0: PCI INT A disabled
[   63.120270] qla2xxx 0000:06:0d.0: PCI INT A -> GSI 48 (level, low) -> IRQ 48
[   63.120299] e1000 0000:03:0e.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24
[   63.121283] qla2xxx 0000:06:0d.0: Found an ISP2200, irq 48, iobase 0xf8012000
[   63.121563] qla2xxx 0000:06:0d.0: Configuring PCI space...
[   63.121770] qla2xxx 0000:06:0d.0: Configure NVRAM parameters...
[   63.215382] qla2xxx 0000:06:0d.0: Verifying loaded RISC code...
[   63.478057] e1000: 0000:03:0e.0: e1000_probe: (PCI:66MHz:64-bit) 00:0d:56:fa:ac:34
[   63.478150] qla2xxx 0000:06:0d.0: firmware: requesting ql2200_fw.bin
[   63.520229] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[  123.470059] qla2xxx 0000:06:0d.0: Firmware image unavailable.
[  123.470109] qla2xxx 0000:06:0d.0: Firmware images can be retrieved from: ftp://ftp.qlogic.com/outgoing/linux/firmware/.
[  123.470161] qla2xxx 0000:06:0d.0: Failed to initialize adapter
[  123.470227] qla2xxx 0000:06:0d.0: PCI INT A disabled

```

I did the symbolic link as sugested above with all of ql firmware bins and then an ```
update-initramfs -u
```

Rebooted and the issue still arises. Anyone else have any suggestions?

---

### Post by herroy on 2009-05-07
I looked around google and came across somone suggesting to rmmod qla2xxx and then modprobe qla2xxx to get the device working for the time being but I get the error:
```
ERROR: Module qla2xxx does not exist in /proc/modules
```

Where do I get the module? And is this why the Firmware fails to load on startup?

---

### Post by herroy on 2009-05-08
After more digging I found this [post]("http://solutions.qlogic.com/KanisaSupportSite/search.do?cmd=viewThread&docType=tkc&kcId=Post-15044126&sliceId=Post-15170027&dialogID=96186523&stateId=1%200%2096128451") and followed the instructions at the bottom but with a few edits to get it to work (namely the driver download address). The script didn't completely work, but it worked up to the point where now I can go
```
rmmod qla2xxx
modprobe qla2xxx
```

and have the module load and then have the fiber channel working and recognizing the power vault connected to it. I just need to figure out now how to have the mod and firmware load on boot up so as to not have an entire 160 second boot up (from the firmware not loading) and then im halfway to where I need to be.

ANy tips?

---

