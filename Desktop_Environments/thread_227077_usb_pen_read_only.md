---
title: "usb pen read only"
date: 2006-08-01
forum: Desktop Environments
---

### Post by GeorgeAD on 2006-08-01
My USB pen drive gets mounted okay, but I can't write to it - comes up with "filesystem is read-only". It was fine with breezy, any other distribution, and windows. The problem appears also in the new (dapper?) Xubuntu. I guess there's some setting I need to change somewhere, but I have no idea what. Can anyone tell me please? 

cheers, 
George

---

### Post by jordilin on 2006-08-01
What's the filesystem format of your usb pen drive? Fat, ntfs,...?

---

### Post by GeorgeAD on 2006-08-01
Fat

---

### Post by jordilin on 2006-08-01
Unplug the drive, plug it in again and take a look at the last lines of /var/log/messages. Tell us what they say.

---

### Post by GeorgeAD on 2006-08-01
Thanks for your help jordilin. I think this is the relevant section: 

Aug  1 12:34:58 george-laptop kernel: [  287.345184] usb 1-2: new full speed USB device using uhci_hcd and address 2

Aug  1 12:34:59 george-laptop kernel: [  288.072393] SCSI subsystem initialized

Aug  1 12:34:59 george-laptop kernel: [  288.183903] Initializing USB Mass Storage driver...

Aug  1 12:34:59 george-laptop kernel: [  288.185328] scsi0 : SCSI emulation for USB Mass Storage devices

Aug  1 12:34:59 george-laptop kernel: [  288.186584] usbcore: registered new driver usb-storage

Aug  1 12:34:59 george-laptop kernel: [  288.186765] USB Mass Storage support registered.

Aug  1 12:35:04 george-laptop kernel: [  293.186532]   Vendor:           Model: USB DISK Pro      Rev: 1.21

Aug  1 12:35:04 george-laptop kernel: [  293.186567]   Type:   Direct-Access                      ANSI SCSI revision: 00

Aug  1 12:35:04 george-laptop kernel: [  293.190021]   Vendor:           Model: USB DISK Pro      Rev: 1.21

Aug  1 12:35:04 george-laptop kernel: [  293.190060]   Type:   Direct-Access                      ANSI SCSI revision: 00

Aug  1 12:35:04 george-laptop kernel: [  293.332084] Driver 'sd' needs updating - please use bus_type methods

Aug  1 12:35:05 george-laptop kernel: [  293.714082] SCSI device sda: 250880 512-byte hdwr sectors (128 MB)

Aug  1 12:35:05 george-laptop kernel: [  293.717076] sda: Write Protect is off

Aug  1 12:35:05 george-laptop kernel: [  293.730543] SCSI device sda: 250880 512-byte hdwr sectors (128 MB)

Aug  1 12:35:05 george-laptop kernel: [  293.733570] sda: Write Protect is off

Aug  1 12:35:05 george-laptop kernel: [  293.733752]  sda: sda1

Aug  1 12:35:05 george-laptop kernel: [  293.741554] sd 0:0:0:0: Attached scsi removable disk sda

Aug  1 12:35:05 george-laptop kernel: [  293.746556] SCSI device sdb: 2880 512-byte hdwr sectors (1 MB)

Aug  1 12:35:05 george-laptop kernel: [  293.749523] sdb: Write Protect is off

Aug  1 12:35:05 george-laptop kernel: [  293.764558] SCSI device sdb: 2880 512-byte hdwr sectors (1 MB)

Aug  1 12:35:05 george-laptop kernel: [  293.767511] sdb: Write Protect is off

Aug  1 12:35:05 george-laptop kernel: [  293.767693]  sdb: unknown partition table

Aug  1 12:35:05 george-laptop kernel: [  293.789196] sd 0:0:0:1: Attached scsi removable disk sdb

Aug  1 12:35:05 george-laptop kernel: [  293.850792] sd 0:0:0:0: Attached scsi generic sg0 type 0

Aug  1 12:35:05 george-laptop kernel: [  293.852198] sd 0:0:0:1: Attached scsi generic sg1 type 0

---

### Post by jordilin on 2006-08-01
> 
Aug 1 12:35:05 george-laptop kernel: [ 293.733570] sda: Write Protect is off

Well, it seems that write protect is off, so you should be able to write on it. In the first post you say that you are using xubuntu. Have you tried it in Ubuntu/Gnome? When I plug my usb, I get nearly the same messages like you and I'm able to write in my usb, but I use Gnome. Perhaps is something related to the Xfce window manager.

---

### Post by GeorgeAD on 2006-08-01
yes, I had Xubuntu installed, and have just installed Ubuntu standard to see if it would solve the problem, but it doesn't. The pen drive works with previous Ubuntu releases, with Windows and with other Linux distros. Also I've tried a different pen drive which seems to write fine...

---

### Post by jordilin on 2006-08-01
I would consider reformatting the pendrive in fat32. Make a backup of the pen drive, reformat it and see if it solves your problem :D

---

### Post by GeorgeAD on 2006-08-02
> **jordilin said:**
> I would consider reformatting the pendrive in fat32. Make a backup of the pen drive, reformat it and see if it solves your problem :D

I can't! The windows computer I'm on at the moment says I don't have sufficient rights; I'm assuming ubuntu won't let me format the drive when it won't let me write to it.

---

### Post by jordilin on 2006-08-02
install the program gparted or use the gparted live cd ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)) and try to format it. I would use the gparted live cd, boot from it, plug your pen drive and format. Then, tell us sth.

---

### Post by GeorgeAD on 2006-08-02
Reformatting fixed it. Thanks jordilin!

---

