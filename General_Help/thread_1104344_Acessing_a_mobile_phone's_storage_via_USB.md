---
title: "Acessing a mobile phone's storage via USB?"
date: 2009-03-23
forum: General Help
---

### Post by Miaxi on 2009-03-23
I am trying to access the micro-sd card in my Nokia 5320 per USB cable. The phone is supposed to get recognised as a mass storage device, which I think it does _but it does not get shown in Nautilus_. 

From dmesg:
> [ 8556.964229] usb 1-4: new full speed USB device using ohci_hcd and address 20
[ 8557.222296] usb 1-4: configuration #1 chosen from 1 choice
[ 8557.272201] scsi11 : SCSI emulation for USB Mass Storage devices
[ 8557.276560] usb-storage: device found at 20
[ 8557.276567] usb-storage: waiting for device to settle before scanning
[ 8562.276604] usb-storage: device scan complete
[ 8562.282603] scsi 11:0:0:0: Direct-Access     Nokia    Nokia 5310 Xpres 0000 PQ: 0 ANSI: 4
[ 8562.308052] sd 11:0:0:0: [sdf] 3842049 512-byte hardware sectors (1967 MB)
[ 8562.315050] sd 11:0:0:0: [sdf] Write Protect is off
[ 8562.315059] sd 11:0:0:0: [sdf] Mode Sense: 04 00 00 00
[ 8562.315064] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 8562.401002] sd 11:0:0:0: [sdf] 3842049 512-byte hardware sectors (1967 MB)
[ 8562.406570] sd 11:0:0:0: [sdf] Write Protect is off
[ 8562.406580] sd 11:0:0:0: [sdf] Mode Sense: 04 00 00 00
[ 8562.406586] sd 11:0:0:0: [sdf] Assuming drive cache: write through
[ 8562.407368]  sdf:
[ 8562.416737] sd 11:0:0:0: [sdf] Attached SCSI removable disk
[ 8562.417233] sd 11:0:0:0: Attached scsi generic sg6 type 0


lsusb:
> Bus 001 Device 020: ID 0421:006a Nokia Mobile Phones 

What am I missing here?

---

### Post by Miaxi on 2009-03-23
bump

---

### Post by Miaxi on 2009-03-23
bump2

---

### Post by kanikilu on 2009-03-23
It looks like it's seeing it (/dev/sdf), but not mounting it :?:

When the phone is attached, can you post the output of the following commands: 
```
sudo fdisk -l
mount
```

Also, do you know what size (in MB or GB) the SD card is?

---

### Post by Miaxi on 2009-03-23
It's a 2GB card. I can edit it if I take it out of the phone and put into the card reader, but it's bothersome.

> **sudo fdisk -l**
[sudo] password for swetlana: 

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x1549f232

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1       29456   236605288+  83  Linux
/dev/sda2           29457       30401     7590712+   5  Erweiterte
/dev/sda5           29457       30401     7590681   82  Linux Swap / Solaris

> **mount**
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/swetlana/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=swetlana)


---

### Post by Miaxi on 2009-03-23
bump

---

### Post by John_T on 2009-03-23
FWIW, I have a Nokia 6230 which connects happily via USB. 

Mine uses the CA-53 cable IIRC.

When you plug it in, does the phone ask you which mode to connect with?  The choices I get are storage (which I use), printing, and default.

Sometimes I have to disconnect and reconnect, and make the phone menu selection, a few times to get it to mount properly, but I'm almost certain that this is because of a dodgy connection to the phone itself, and nothing to do with ubuntu.

---

### Post by Miaxi on 2009-03-23
I tried all those menu options and setting storage as default. One time I could see the phone in Nautilus but not write on it. 

I am not saying it's a bug. It might be a setting that I messed with and forgot about. Just need a pointer in the right direction, really.

---

### Post by Miaxi on 2009-03-24
bump

---

### Post by Miaxi on 2009-03-24
It works on a windows PC, so its not a hardware issue.

---

### Post by John_T on 2009-03-24
> **Miaxi said:**
> It works on a windows PC, so its not a hardware issue.

This made me think of something I've seen on portable hard disks and flash drives, but not on my phone, but it's essentially the same thing.

If the disk is inserted on a windows machine, and removed without the "safely remove hardware" shortcut, linux may see it it as unsafe to mount the device, and refuse to do so for read/write.  

Putting the drive back into a windows machine, using the remove option from the system tray, and waiting for the "It is now safe to remove the device" message did the trick.

On some occasions Windows refuses to disconnect the device, and I've had to shut Windows down completely, which achieves the desired result, even if in a painful fashion.

---

### Post by Miaxi on 2009-03-24
Well Vista auto-installed some weird driver and does not allow to use the save removal option. It creates a new drive called "NOKIA" instead of "drive F:". I shut down the PC before pulling the cable.

When pressing "done" on the phone, I am getting this:
[[img]http://www.ubuntu-pics.de/thumb/11473/screenshot_002_11fz3s.jpg[/img]](http://www.ubuntu-pics.de/bild/11473/screenshot_002_11fz3s.jpg)

It's not possible to edit anything.

If I pick "storage" on the phone, that drive disappears again.

---

### Post by Miaxi on 2009-03-24
bump

---

### Post by James_Lochhead on 2009-03-24
According to that earlier fdisk output your phone storage is not actually being recognised.

On my BlackBerry Storm I had to specifically enable an option on the phone to make it act like removable media. You might not have set this up properly.

---

### Post by Miaxi on 2009-03-24
Using the same setting as on the windows PC, where I did not have to do anything special apart from picking "storage" on the phone menu.

---

### Post by Miaxi on 2009-03-24
Also works with a Knoppix live CD. :S

---

### Post by Slim Odds on 2009-03-24
> **John_T said:**
> If the disk is inserted on a windows machine, and removed without the "safely remove hardware" shortcut, linux may see it it as unsafe to mount the device, and refuse to do so for read/write.

That might sound right if the drive was NTFS. I doubt that it would apply to these types of cards because the are usually FAT32.

Also, accessing the card from within the phone is a lot difference than accessing directly via a card reader (with respect to the file system).

---

### Post by Miaxi on 2009-03-24
:(

---

### Post by Miaxi on 2009-03-24
Ah come on, is this another of those "everything else sees the drive but ubuntu doesn't" things? -.-

---

### Post by snkiz on 2009-03-24
similar problem with my Samsung m510 no one has looked at as of yet

launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292522]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292522")

---

### Post by John_T on 2009-03-24
> **Miaxi said:**
> Ah come on, is this another of those "everything else sees the drive but ubuntu doesn't" things? -.-
It could be a (phone) driver specific thing, as you've said it works in a card reader.

Have you tried booting to an older kernel and seeing if that makes any difference, as reported by snkiz?  You may yet be able to help with diagnosing you're own "Oh come on..." question.

You previously said that:

> **Miaxi said:**
> "One time I could see the phone in Nautilus but not write on it. "

was that with your current setup, or before an upgrade?  Has it ever worked correctly with Ubuntu?

---

### Post by Miaxi on 2009-03-24
> **John_T said:**
> It could be a (phone) driver specific thing, as you've said it works in a card reader.

Have you tried booting to an older kernel and seeing if that makes any difference, as reported by snkiz?  You may yet be able to help with diagnosing you're own "Oh come on..." question.
Tried with the Ubuntu 8.10 live CD, which has 2.6.27-7-generic - does not show the storage but offers to configure a mobile broadband if I abort the process in the phone's menu.

> 
was that with your current setup, or before an upgrade?  Has it ever worked correctly with Ubuntu?
It has never worked correctly under Ubuntu. If I exit the menu inside the phone, Ubuntu claims to have recognised a camera with pictures and does this: [http://www.ubuntu-pics.de/bild/11473/screenshot_002_11fz3s.jpg](http://www.ubuntu-pics.de/bild/11473/screenshot_002_11fz3s.jpg) . It is not possible to edit that drive.

It works in Knoppix 5.1.0, which runs kernel 2.6.19.1. The storage gets mounted right away and I have full access.

:-({|=

---

### Post by Miaxi on 2009-03-27
Yea, quick update to this one, as I found the solution: linux kernel 2.6.29 handles the phone without the need of any "unusual devices" patches. 

Guide: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by BLTicklemonster on 2009-03-27
> **Miaxi said:**
> Ah come on, is this another of those "everything else sees the drive but ubuntu doesn't" things? -.-

Really, the forum is about out of room for those things, isn't it?

---

