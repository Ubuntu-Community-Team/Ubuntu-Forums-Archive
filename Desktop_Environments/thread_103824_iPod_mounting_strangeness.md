---
title: "iPod mounting strangeness"
date: 2005-12-14
forum: Desktop Environments
---

### Post by flosofl on 2005-12-14
I searched the forum and couldn't find this exact issue.

When I plug my iPod mini in a USB 2.0 port, it will not mount on the desktop or the filesystem.  Ubuntu *does* see the device as evidenced by the output of 'dmesg'
> [4614211.798000] usb 4-1.2: new high speed USB device using ehci_hcd and address 31
[4614211.837000] scsi12 : SCSI emulation for USB Mass Storage devices
[4614211.841000] usb-storage: device found at 31
[4614211.841000] usb-storage: waiting for device to settle before scanning
[4614216.841000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4614216.841000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4614216.846000] SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
[4614216.848000] sdb: Write Protect is off
[4614216.848000] sdb: Mode Sense: 64 00 00 08
[4614216.848000] sdb: assuming drive cache: write through
[4614216.852000] SCSI device sdb: 7999487 512-byte hdwr sectors (4096 MB)
[4614216.853000] sdb: Write Protect is off
[4614216.853000] sdb: Mode Sense: 64 00 00 08
[4614216.853000] sdb: assuming drive cache: write through
[4614216.853000]  /dev/scsi/host12/bus0/target0/lun0: p1 p2
[4614217.270000] Attached scsi removable disk sdb at scsi12, channel 0, id 0, lun 0
[4614217.272000] usb-storage: device scan complete
However, nothing appears on my desktop nor under /media
> philf@weasel-main:~$ ls /media
cdrom  cdrom0  floppy  floppy0  usb  usb0  usbdisk


Now, to add to the strangeness, when I log out and log back in... lo and behold!  There's my iPod on the desktop and also mounted correctly under /media.  Everything sees and interacts with it fine (Rhythmbox, GTKPod, etc...).  If I unmount it I get a weird "Couldn't eject media" message, but 'mount' no longer lists it and the mount point is gone under /media and the icon removed from my desktop.  At this point I cannot mount it again unless I log out and back in.

Anyone have any ideas?:confused:

---

### Post by aysiu on 2005-12-14
I don't know about the first problem (having to log out and log back in again for it to automount), but I know about the second one. If it mounts at /media/IPOD, then open a terminal and type the command ```
sudo eject /media/IPOD
``` You can create a launcher for this as well.

---

### Post by flosofl on 2005-12-14
[QUOTE=aysiu]I don't know about the first problem (having to log out and log back in again for it to automount), but I know about the second one. If it mounts at /media/IPOD, then open a terminal and type the command ```
sudo eject /media/IPOD
``` You can create a launcher for this as well.[/QUOTE]
Thanks.  I'll give that a shot.

I just tested my other devices.  Same issue.  Mounting IDE CD/DVDs.  My USB thumb drive.  All exhibit the same behavior...  Very irritating.

---

### Post by aysiu on 2005-12-14
[QUOTE=flosofl]
I just tested my other devices.  Same issue.  Mounting IDE CD/DVDs.  My USB thumb drive.  All exhibit the same behavior...  Very irritating.[/QUOTE] Maybe you can try going to System > Preferences > Sessions and making *gnome-volume-manager* a startup program. It should already be one, but clearly it isn't for you.

---

### Post by flosofl on 2005-12-14
[QUOTE=aysiu]Maybe you can try going to System > Preferences > Sessions and making *gnome-volume-manager* a startup program. It should already be one, but clearly it isn't for you.[/QUOTE]

Thanks!  That did it.  :smile: 

Hmm... that seems strange, though (not that I'm looking a gift horse in the mouth!).  I would think gnome-volume-manager would load as part of the general GNOME startup.  In addition it was listed as running in the session manager before I added it to "startup".

There are now 2 gnome-volume-managers running one has order=40 and gear icon next to it.  The other (the one I added) has order=50 and life-preserver icon.   Both are of the Style "Settings" (screwdriver/wrench icon)  What do the state icons indicate?

---

### Post by aysiu on 2005-12-14
[QUOTE=flosofl]What do the state icons indicate?[/QUOTE] No idea. But everything's working now?

---

### Post by flosofl on 2005-12-14
[QUOTE=aysiu]No idea. But everything's working now?[/QUOTE]

So far, so good.  Thanks again.

---

