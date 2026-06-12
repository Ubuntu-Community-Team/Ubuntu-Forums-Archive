---
title: "Amarok Ipod Xfter Problem"
date: 2005-11-23
forum: Desktop Environments
---

### Post by anders.ostling on 2005-11-23
I have problems to transfer music from my Breezy workstation to my IPod mini. Here is what happens when I insert the USB cable

1. The device is detected properly
[4389181.058000] scsi4 : SCSI emulation for USB Mass Storage devices
[4389181.059000] usb-storage: device found at 9
[4389181.059000] usb-storage: waiting for device to settle before scanning
[4389186.059000]   Vendor: Apple     Model: iPod              Rev: 1.62
[4389186.059000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4389186.065000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[4389186.066000] sda: Write Protect is off
[4389186.066000] sda: Mode Sense: 64 00 00 08
[4389186.066000] sda: assuming drive cache: write through
[4389186.068000] SCSI device sda: 7999487 512-byte hdwr sectors (4096 MB)
[4389186.069000] sda: Write Protect is off
[4389186.069000] sda: Mode Sense: 64 00 00 08
[4389186.069000] sda: assuming drive cache: write through
[4389186.069000]  /dev/scsi/host4/bus0/target0/lun0: p1 p2
[4389186.489000] Attached scsi removable disk sda at scsi4, channel 0, id 0, lun 0
[4389186.489000] Attached scsi generic sg1 at scsi4, channel 0, id 0, lun 0,  type 0
[4389186.490000] usb-storage: device scan complete
[4389188.005000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

2. It get mounted properly
/dev/sda2 on /media/ipod type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)

3. Amarok starts (I have configured gnome to automatically start amarok when the gizmo is connected)

4. I can click on the tab "Media device", and all my music is seen.

5. I drag tracks from my active playlist to the Media "transfer queue". No problems so far

6. When I click on the Transfer button, the queue is emptied and the track list on the Media device is updated with the songs. But after removing the USB cable and browsing the ipod, the songs are not there. If I re-attach the ipod and look at the track list, the songs are not there any more. What gives?

I have the backported 1.3.5 version from Kubuntu. Everything else seems to work fine. Transfering songs using gtkpod works just fine.

Help .-)

Anders

---

### Post by 23meg on 2005-11-23
This is very likely not an Amarok problem; many have reported that USB transfers are left incomplete in Breezy even though applications state otherwise. I did observe this same behavior with USB devices in the development release of Breezy, but it seemed to be fixed in final. 

Do you cleanly unmount and eject your ipod after the track transfer? After ejecting, watch the transfer icon on your ipod screen and wait for it to go off, and then remove your ipod.

---

### Post by anders.ostling on 2005-11-23
well, I did as you suggested. I transfered  the songs again, pressed the Connect button (which did an "unconnect...") and then umounted the device. Still could not find any songs on the ipod.

Now I started gtpkod and did a Sync, Check Ipod Files and re-synced. And voila, there they were. Seems like one of my earlier amarok sync's hosed the directory structure in some way, and that gtpkod were able to repair the indexes. 

Good for me, but maybe not any help for the amarok developers. Sigh

Anders

---

### Post by 23meg on 2005-11-23
So I take it you can transfer with Amarok now? 

It's not a good idea to use gtkpod and amarok together. I suggest you do a full restore (format) with the ipod updater util and use amarok only from now on.

---

### Post by anders.ostling on 2005-11-23
[QUOTE=23meg]So I take it you can transfer with Amarok now? 

It's not a good idea to use gtkpod and amarok together. I suggest you do a full restore (format) with the ipod updater util and use amarok only from now on.[/QUOTE]

So, I took your advice, downloaded the newest ipod updater (1.4) and did a full restore. After this, transfers seems to work fine (so far :-). I guess that fact that I used iTunes, gtkpod and amarok in a wild mix created more trouble than the poor gizmo box could take.

Thanks for the advice

Anders

---

### Post by 23meg on 2005-11-23
I told you it wasn't an Amarok problem way before ;) Happy you got it solved. Take care to use one single app with your ipod.

---

