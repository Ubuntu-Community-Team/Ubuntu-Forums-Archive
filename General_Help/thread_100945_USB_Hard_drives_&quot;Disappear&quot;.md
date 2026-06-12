---
title: "USB Hard drives &quot;Disappear&quot;"
date: 2005-12-08
forum: General Help
---

### Post by damonkohler on 2005-12-08
I have two USB hard drives that I have mounted to /mnt/usbdisk0 and /mnt/usbdisk1 in my fstab... Here's the entry:

/dev/sde1 /mnt/usbdisk0 vfat defaults,user,umask=022 0 2
/dev/sdf1 /mnt/usbdisk1 vfat defaults,user,umask=022 0 2

I'm having two problems with this. It seems that when I reboot, these drives don't actually get mounted. Secondly, after I do mount them manually, sometimes the drives kind of disappear. That is, ls /mnt/usbdisk0 will turn up nothing. Issuing another mount command (or mount -o remount) doesn't work and I am unable to unmount them becuase they're busy.

I'm wondering if there's some pmount interference going on maybe? Icons show up on the desktop, but they also fail to show any files once the drives have disappeared. The same goes for /media/usbdisk and /media/usbdisk-1.

Any suggestions?

---

### Post by kzutter on 2005-12-08
There is no guarantee that the drives will have the same device names at the next reboot.

What you want to look at is udev rules.

[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

Good Luck,
Ken

---

### Post by Grey on 2005-12-08
My USB drive is mounted automatically by pmount when I insert it into the computer...  I had to add myself to the group that controls that though.  I did it from the users and groups control panel though, so I'm not sure what specific group it is.

---

### Post by damonkohler on 2005-12-08
I don't think these responses answer my question. The udev thing may be part of the answer, but I'm not sure.

The reason I'm not using pmount, is because I wanted to change the umask. So, I added the lines to fstab. Unfortunately, the drives do not mount at start up, as I said, and instead I have to do it manually. Maybe the udev rules could help fix this, I'm not sure... But it doesn't look like it to me.

The main problem is that after the drives have been mounted for awhile, everything on them disappears. So if I do an ls after mounting them manually (on a fresh restart) then I see all the directories, files, etc. But, after they have been mounted for awhile, all of that disappears. I can do an ls and see nothing. Not in /mnt/usbdisk. Not in /media/usbdisk. For some reason, the mount seems to go away. Then when I try to unmount it, I get an error saying that the device is busy.

---

### Post by angrykeyboarder on 2005-12-11
[QUOTE=Grey]My USB drive is mounted automatically by pmount when I insert it into the computer...  I had to add myself to the group that controls that though.  I did it from the users and groups control panel though, so I'm not sure what specific group it is.[/QUOTE]

Damn...

I was hoping you'd have ended this with that information. lol

I figured that would be the cure but I have no idea what group I'm supposed to be in for pmount.  I'm already in cdrom and it does me no good.

pmount is suddenly screwed up. I have no idea why. But right now I've got a ton of data that I need and can't get to on my 250 GB external hard drive.

---

### Post by Sutekh on 2005-12-11
[QUOTE=angrykeyboarder]Damn...

I was hoping you'd have ended this with that information. lol

I figured that would be the cure but I have no idea what group I'm supposed to be in for pmount.  I'm already in cdrom and it does me no good.

pmount is suddenly screwed up. I have no idea why. But right now I've got a ton of data that I need and can't get to on my 250 GB external hard drive.[/QUOTE]

Try the group **plugdev**

Else, check out the User privileges for your user in System -> Administration -> Users and Groups

---

### Post by chinocracy on 2007-01-31
This also happens to USB thumb drives I plug into my computer. After a while, they just disappear, and I don't know how to remount them without rebooting. Even unplugging and plugging the drives doesn't work. This needs a certain solution. Anyone know?

---

### Post by dcstar on 2007-02-01
> **chinocracy said:**
> This also happens to USB thumb drives I plug into my computer. After a while, they just disappear, and I don't know how to remount them without rebooting. Even unplugging and plugging the drives doesn't work. This needs a certain solution. Anyone know?

Check that **gnome-volume-manager** is running (assuming you use Gnome......)

---

### Post by chinocracy on 2007-02-04
Dcstar:
Sorry for getting back only now. Yes, I'm on gnome. How do I check if gnome-volume-manager is still working? What I've tried is to go to terminal and run (or try to rerun) gnome-volume-manager there, but I guess I'm not doing it right. Thanks.

---

### Post by dcstar on 2007-02-04
> **chinocracy said:**
> Dcstar:
Sorry for getting back only now. Yes, I'm on gnome. How do I check if gnome-volume-manager is still working? What I've tried is to go to terminal and run (or try to rerun) gnome-volume-manager there, but I guess I'm not doing it right. Thanks.

```
ps -ef | fgrep gnome-volume-manager
```
or System-Administration-System Monitor (I think....) and you should see the process.

---

### Post by chinocracy on 2007-02-06
> **dcstar said:**
> ```
ps -ef | fgrep gnome-volume-manager
```
or System-Administration-System Monitor (I think....) and you should see the process.

Oh yeah... just re-discovered the system monitor... will check and get back if I notice something, just hadn't lately, thanks.

---

### Post by chinocracy on 2007-02-09
OK, the usbdisk disappeared again, and I checked in Sytem Monitor that Gnome Volume Manager is still working. So it must be something else. It usually happens when I install several packages, or leave it for a long time while I'm doing something, like gaming. Anyway, a method for manual mounting will not hurt. Thanks.

---

### Post by dcstar on 2007-02-10
> **chinocracy said:**
> OK, the usbdisk disappeared again, and I checked in Sytem Monitor that Gnome Volume Manager is still working. So it must be something else. It usually happens when I install several packages, or leave it for a long time while I'm doing something, like gaming. Anyway, a method for manual mounting will not hurt. Thanks.

Possibly there is a power management setting that is putting the USB ports to sleep, try disabling any power settings.

---

### Post by chinocracy on 2007-02-13
Would that be related to ACPI? I'll check that out, thanks.

---

### Post by chinocracy on 2007-02-22
Yep, it's the power manager all right. It was set to let the display sleep after an amount of time, I think an hour on my system. Although it's about display power, it affected the USB controller. I set it to never sleep and the USB flash drive stayed on.  Thanks.

---

### Post by chinocracy on 2007-08-11
Bringing this issue back up again. I installed Kubuntu along with Ubuntu on this computer and the USB disappearing act is happening again. How is power management manipulated for Kubuntu? Thanks.

---

### Post by chinocracy on 2007-08-16
Workaround of installing these two packages:
usbview
usbutils

Seems to be working so far...

---

### Post by chinocracy on 2007-08-19
Nope, installing the two above it doesn't work. I've decided to look at the "Dmesg" output

```

[17179794.536000] usb 1-2: new full speed USB device using uhci_hcd and address 2
[17179794.964000] SCSI subsystem initialized
[17179795.020000] Initializing USB Mass Storage driver...
[17179795.020000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179795.020000] usb-storage: device found at 2
[17179795.020000] usb-storage: waiting for device to settle before scanning
[17179795.020000] usbcore: registered new driver usb-storage
[17179795.020000] USB Mass Storage support registered.
[17179800.024000]   Vendor: Generic   Model: USB Flash Disk    Rev: 0.00
[17179800.024000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17179800.036000] usb-storage: device scan complete
[17179800.108000] Driver 'sd' needs updating - please use bus_type methods
[17179800.120000] SCSI device sda: 2015231 512-byte hdwr sectors (1032 MB)
[17179800.128000] sda: Write Protect is off
[17179800.128000] sda: Mode Sense: 00 00 00 00
[17179800.128000] sda: assuming drive cache: write through
[17179800.148000] SCSI device sda: 2015231 512-byte hdwr sectors (1032 MB)
[17179800.152000] sda: Write Protect is off
[17179800.152000] sda: Mode Sense: 00 00 00 00
[17179800.152000] sda: assuming drive cache: write through
[17179800.152000]  sda: sda1
[17179800.268000] sd 0:0:0:0: Attached scsi removable disk sda
[17179800.308000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179807.704000] UDF-fs: No partition found (1)
[17179807.900000] UDF-fs: No partition found (1)
[17179808.492000] Unable to identify CD-ROM format.
[17179808.980000] Unable to identify CD-ROM format.
[17179809.004000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180036.268000] ibm_acpi: ec object not found
[17183126.600000] uhci_hcd 0000:00:07.2: host system error, PCI problems?
[17183126.600000] uhci_hcd 0000:00:07.2: host controller halted, very bad!
[17183126.600000] uhci_hcd 0000:00:07.2: HC died; cleaning up
[17183126.600000] usb 1-2: USB disconnect, address 2

```

It seems the USB host controller is getting shut down automatically. How do I stop it or how do I restart? Can't find the darned process that's putting my USB ports to sleep. Thanks.

---

