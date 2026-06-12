---
title: "USB flash drive not showing on Desktop or media:/"
date: 2005-12-14
forum: General Help
---

### Post by knowerrors on 2005-12-14
Hi all,

Im using kubuntu 5.10 with kde 3.4.3, when I plugin a usb drive, it gets mounted and shows up in /media/usbdisk, and I can browse it there.  However, it does not show on the desktop as an icon, or in media:/ Because of this, I can only unmount it and the command line.  CDs and DVDs show on the desktop and in media:/ just fine.  Anybody have ideas of how to fix this?  I already tried kde 3.5, which also didn't work.

Thanks
KE

---

### Post by korkow on 2005-12-14
try taking it out, then simply putting it back in. If that doesn't work, take it out, shut down, put the usb in while the computer is off, then boot up!

---

### Post by GoldBuggie on 2005-12-14
Also...have you checked the (right-click on desktop)->configure desktop->behavior->device icons->Mounted Removable Medium

You can check unmounted if you want as well depending if you have mounting on plugin correctly working or not

---

### Post by knowerrors on 2005-12-15
GoldBuggie:
Yes, the option to show all mounted everything (except hard drives) on the desktop is selected.

korkow:
Tried all that, no difference.

Any other ideas?  Some hidden config area or icon link that has the wrong address?  Alot has happened since I did the initial clean install of Breezy, including installing then uninstalling kde 3.5.  And no, doing a fresh Breezy install is not worth it to me.

---

### Post by GoldBuggie on 2005-12-15
You sure it gets mounted on insertion(sorry for asking just want to make sure that when you plug it in it gets mounted and not only shows up unmounted)

Not sure if this will help but you can try...it will give hal root privilages.
```
kdesu kate /etc/default/hal
```
then uncomment the last line making it
```
DAEMON_OPTS=--retain-privileges
```
If this doesn't work you can change it back.

And another thing...if you have "removable medium unmounted" checked. Will it show up when you unmount the usb?

---

### Post by knowerrors on 2005-12-17
usb drive does not show up when the option for showing unmounted media is checked.  Also, the option in hal you mentioned doesn't seem to have changed anything... 

btw, here is what I get in /var/log/messages:

Turning on usb printer with flash memory card in slot-

Dec 17 15:21:03 localhost kernel: usb 1-2: new full speed USB device using uhci_hcd and address 7
Dec 17 15:21:04 localhost kernel: hub 1-2:1.0: USB hub found
Dec 17 15:21:04 localhost kernel: hub 1-2:1.0: 2 ports detected
Dec 17 15:21:04 localhost usb.agent[11260]:      usbcore: already loaded
Dec 17 15:21:04 localhost kernel: usb 1-2.1: new full speed USB device using uhci_hcd and address 8
Dec 17 15:21:04 localhost kernel: drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 8 if 0 alt 0 proto 2 vid 0x04B8 pid 0x0005
Dec 17 15:21:04 localhost usb.agent[11324]:      usblp: already loaded
Dec 17 15:21:04 localhost kernel: usb 1-2.2: new full speed USB device using uhci_hcd and address 9
Dec 17 15:21:04 localhost kernel: scsi1 : SCSI emulation for USB Mass Storage devices
Dec 17 15:21:04 localhost usb.agent[11398]:      usb-storage: already loaded
Dec 17 15:21:09 localhost kernel:   Vendor: EPSON     Model: SP 785EPX Storag  Rev: 1.10
Dec 17 15:21:09 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Dec 17 15:21:09 localhost kernel: SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
Dec 17 15:21:09 localhost kernel: sda: Write Protect is off
Dec 17 15:21:09 localhost kernel: SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
Dec 17 15:21:09 localhost kernel: sda: Write Protect is off
Dec 17 15:21:09 localhost kernel:  sda: sda1
Dec 17 15:21:09 localhost kernel: Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
Dec 17 15:21:09 localhost scsi.agent[11465]:      sd_mod: loaded sucessfully (for disk)
Dec 17 15:42:31 localhost kernel: usb 1-2: USB disconnect, address 7
Dec 17 15:42:31 localhost kernel: usb 1-2.1: USB disconnect, address 8
Dec 17 15:42:31 localhost kernel: drivers/usb/class/usblp.c: usblp0: removed
Dec 17 15:42:31 localhost kernel: usb 1-2.2: USB disconnect, address 9

Plugging in usb camera with memory card-
 
Dec 17 15:53:12 localhost kernel: usb 2-1: new full speed USB device using uhci_hcd and address 2
Dec 17 15:53:12 localhost kernel: scsi2 : SCSI emulation for USB Mass Storage devices
Dec 17 15:53:13 localhost usb.agent[15409]:      usb-storage: already loaded
Dec 17 15:53:13 localhost usb.agent[15409]:      libgphoto2: loaded successfully
Dec 17 15:53:17 localhost kernel:   Vendor: OLYMPUS   Model: C4100Z/C4000Z     Rev: 1.00
Dec 17 15:53:17 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Dec 17 15:53:17 localhost kernel: SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
Dec 17 15:53:18 localhost kernel: sda: Write Protect is off
Dec 17 15:53:18 localhost kernel: SCSI device sda: 32000 512-byte hdwr sectors (16 MB)
Dec 17 15:53:18 localhost kernel: sda: Write Protect is off
Dec 17 15:53:18 localhost kernel:  sda: sda1
Dec 17 15:53:18 localhost kernel: Attached scsi removable disk sda at scsi2, channel 0, id 0, lun 0
Dec 17 15:53:18 localhost scsi.agent[15508]:      sd_mod: loaded sucessfully (for disk)

Both auto mount in /media/usbdisk , but neither show in media:/ or on the desktop

---

### Post by ~sparkles~ on 2007-06-14
I'm getting the same problem...except with an external harddrive formatted with nstf... seems ok with FAT and reading nstf partitions on the laptop... changing the desktop behaviour hasn't changed anything....

---

