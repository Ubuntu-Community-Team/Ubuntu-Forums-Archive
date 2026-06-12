---
title: "SanDisk Cruzer Micro 4.0GB won't mount!"
date: 2009-02-10
forum: General Help
---

### Post by slothbotkiller on 2009-02-10
Okay, lets just start -- thanks by the way.

History: My father gave me this Cruzer Micro a few months back and told me "fix it and it's yours."
Description: It is password protected and I checked on Windows it has no driver but that shouldn't have an effect on me when using Ubuntu... wow I am tired... 
Issue: The Sandisk Cruzer Micro is password protected and needs to be reformatted. It also doesn't have its U3 driver installed. My presumption is that there was an operating system like Ubuntu installed on the Cruzer Micro (hence no U3 driver for Windows). I tried installing the driver on Windows of course no luck -- i tried that with and without the pendrive plugged in My Windows box, My Ubuntu box does not even try interacting with the pendrive however it does show the following: 

brian@brian:~$ lsusb
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 009: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 005 Device 004: ID 090c:c371 Feiya Technology Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
brian@brian:~$ 

On Windows there seems to be two drives: a "Removable Disk (F)" and a "CD Drive (G) Audio CD" that holds an audio file which ironically doesn't play it appears to be 44 bytes large. Can anyone get me a step further in cracking this beast of a puzzle? If not, is there any opensource software for Ubuntu that i can download and install in order to reformat this pendrive?

I have also withdrawn some more (perhaps useless) information for you:

brian@brian:~$ sudo dmesg | tail -c 2000
: 0
[ 3002.974026] ForceXPAon: 0
[ 3003.037992] ForceXPAon: 0
[ 3003.102754] ForceXPAon: 0
[ 3121.622530] ForceXPAon: 0
[ 3121.862510] ForceXPAon: 0
[ 3122.042048] ForceXPAon: 0
[ 3122.278548] ForceXPAon: 0
[ 3122.342063] ForceXPAon: 0
[ 3122.406544] ForceXPAon: 0
[ 3122.470585] ForceXPAon: 0
[ 3122.534552] ForceXPAon: 0
[ 3122.598563] ForceXPAon: 0
[ 3122.662028] ForceXPAon: 0
[ 3122.726060] ForceXPAon: 0
[ 3122.790026] ForceXPAon: 0
[ 3122.854070] ForceXPAon: 0
[ 3122.918038] ForceXPAon: 0
[ 3122.982567] ForceXPAon: 0
[ 3123.046000] ForceXPAon: 0
[ 3123.110588] ForceXPAon: 0
[ 3223.681610] usb 5-5: USB disconnect, address 9
[ 3228.292712] usb 5-5: new high speed USB device using ehci_hcd and address 10
[ 3228.431325] usb 5-5: configuration #1 chosen from 1 choice
[ 3228.435172] scsi14 : SCSI emulation for USB Mass Storage devices
[ 3228.441489] usb-storage: device found at 10
[ 3228.441513] usb-storage: waiting for device to settle before scanning
[ 3233.441013] usb-storage: device scan complete
[ 3233.442390] scsi 14:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[ 3233.443869] scsi 14:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[ 3233.460378] sd 14:0:0:0: [sdb] Attached SCSI removable disk
[ 3233.460747] sd 14:0:0:0: Attached scsi generic sg2 type 0
[ 3233.477699] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 3233.478097] sr 14:0:0:1: Attached scsi CD-ROM sr1
[ 3233.478442] sr 14:0:0:1: Attached scsi generic sg3 type 5
[ 3241.630043] ForceXPAon: 0
[ 3241.870124] ForceXPAon: 0
[ 3242.050084] ForceXPAon: 0
[ 3242.286100] ForceXPAon: 0
[ 3242.350174] ForceXPAon: 0
[ 3242.414664] ForceXPAon: 0
[ 3242.478610] ForceXPAon: 0
[ 3242.542612] ForceXPAon: 0
[ 3242.606613] ForceXPAon: 0
[ 3242.670607] ForceXPAon: 0
[ 3242.734632] ForceXPAon: 0
[ 3242.798089] ForceXPAon: 0
[ 3242.862085] ForceXPAon: 0
[ 3242.926731] ForceXPAon: 0
[ 3242.990107] ForceXPAon: 0
[ 3243.054577] ForceXPAon: 0
[ 3243.118172] ForceXPAon: 0
brian@brian:~$ 


brian@brian:~$ sudo mkdir /mnt/usb
brian@brian:~$ 
brian@brian:~$ sudo mount /dev/sdb /mnt/usb
mount: No medium found
brian@brian:~$ 

... that seemed to do nothing.

I will continue my quest for knowledge tomorrow.

source: [http://ubuntuforums.org/archive/index.php/t-898644.html](http://ubuntuforums.org/archive/index.php/t-898644.html)

--------------
Here is the output of...

brian@brian:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8696e643

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       37678   302648503+   5  Extended
/dev/sda2   *       37679       38913     9913344    7  HPFS/NTFS
/dev/sda5               1         124      995967   83  Linux
/dev/sda6             125         622     4000153+  82  Linux swap / Solaris
/dev/sda7             623        4269    29294496   83  Linux
/dev/sda8            4270       37678   268357761   83  Linux
brian@brian:~$ 

The Cruzer Micro doesn't appear to be on this list of partitions. I do have Gparted now thanks. I am guessing it would have looked something like this:    
Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         489     3927861    6  FAT32

but that's not it unfortunately. I had a false glimmer of hope for a moment there until I realized it was only my SD card.

---

### Post by mb_webguy on 2009-02-10
Could you post the output of "sudo fdisk -l" in the terminal while the USB drive is plugged in please?

If you see an entry for it, you can probably use GParted to format it.  If you don't have it already, install it with "sudo apt-get install gparted".  You'll see it under System->Administration->Partition Editor.

Select the device that corresponds to your drive, make sure it's not mounted, and format it.  I'd suggest FAT32 if you might use it on a Windows machine, or ext2 if not.  (Notice I said ext2 and not ext3, since the ext3 journal would unnecessarily take up precious space on the 4GB drive.)

---

### Post by halovivek on 2009-02-10
try using mount from terminal.

---

### Post by slothbotkiller on 2009-02-10
> **mb_webguy said:**
> Could you post the output of "sudo fdisk -l" in the terminal while the USB drive is plugged in please?

If you see an entry for it, you can probably use GParted to format it.  If you don't have it already, install it with "sudo apt-get install gparted".  You'll see it under System->Administration->Partition Editor.

Select the device that corresponds to your drive, make sure it's not mounted, and format it.  I'd suggest FAT32 if you might use it on a Windows machine, or ext2 if not.  (Notice I said ext2 and not ext3, since the ext3 journal would unnecessarily take up precious space on the 4GB drive.)

Is there another way I can try forcing a mount on the Cruzer? I have had no luck with the Cruzer so far yet.

---

### Post by mc4man on 2009-02-10
> My presumption is that there was an operating system like Ubuntu installed on the Cruzer Micro 

Actually it looks like someone used a program like 'universal customizer' to create a new isofs partition (partition that emulates a cdrom drive
You can insert whatever you want in the partition when creating, the typical use was/is to have a payload that 'steals' all the personal info of the windows pc the drive is connected to. (xp and earlier.

It appears though all you have is a .cda file (windows 'marker' file for an audio cd track.

In a lot of cases the isofs partition is password protected and may be a problem to remove.
Your best bet is to format the drive to the extent that you can and get some good use from it.

Something like the 'ultimate boot disk' may be helpful if you can't format normally

If you were curious about the G drive and the hack see here

[http://www.raymond.cc/blog/archives/2007/11/23/hack-u3-usb-smart-drive-to-become-ultimate-hack-tool/](http://www.raymond.cc/blog/archives/2007/11/23/hack-u3-usb-smart-drive-to-become-ultimate-hack-tool/)

---

### Post by slothbotkiller on 2009-02-10
> **mc4man said:**
> Actually it looks like someone used a program like 'universal customizer' to create a new isofs partition (partition that emulates a cdrom drive
You can insert whatever you want in the partition when creating, the typical use was/is to have a payload that 'steals' all the personal info of the windows pc the drive is connected to. (xp and earlier.

It appears though all you have is a .cda file (windows 'marker' file for an audio cd track.

In a lot of cases the isofs partition is password protected and may be a problem to remove.
Your best bet is to format the drive to the extent that you can and get some good use from it.

Something like the 'ultimate boot disk' may be helpful if you can't format normally

If you were curious about the G drive and the hack see here

[http://www.raymond.cc/blog/archives/2007/11/23/hack-u3-usb-smart-drive-to-become-ultimate-hack-tool/](http://www.raymond.cc/blog/archives/2007/11/23/hack-u3-usb-smart-drive-to-become-ultimate-hack-tool/)

Ah! So that is why I couldn't remove 123 hidden sender I had Bitdefender 2009 installed and hidden sender was under my safe or trusted applications list, that makes sense.  Wow thanks I will look into it in about an hour. I am a bit worked up about homework I hate the stuff yet love the classes.

---

### Post by mc4man on 2009-02-10
not sure about that 'hidden sender' bit, if there is a payload on the drive, (not just the .cda) note that it can't do anything on linux and vista Os's.

---

### Post by slothbotkiller on 2009-02-10
> **mc4man said:**
> not sure about that 'hidden sender' bit, if there is a payload on the drive, (not just the .cda) note that it can't do anything on linux and vista Os's.

Hmm.. yes, i realize now that it isn't relevant. I tried wiping it with darik's boot and nuke but failed -- it sees it as an unknown device or "????". do i pick another hdd eraser? I don't want to erase any of my hdd data just the usb device.

---

