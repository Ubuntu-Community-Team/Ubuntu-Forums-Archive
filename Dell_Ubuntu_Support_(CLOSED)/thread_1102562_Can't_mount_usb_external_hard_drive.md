---
title: "Can't mount usb external hard drive"
date: 2009-03-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rockygrrl1313 on 2009-03-21
HELP PLEASE!  I just got a dell mini 9 running Ubuntu.  I know nothing about Linux.  I purchased a seagate external usb2 hard drive so I can move my files off my home pc which is dying (windows vista go figure) when I plug the hard drive into the Ubuntu system it says it cannot mount the volume.  It is NTFS.  Can someone please walk me through step by step what I do here.  There are similar threads but they are over my head.  Please help, I just need to get away from windows.

---

### Post by ugm6hr on 2009-03-22
If you want to use NTFS:

Open terminal (in Applications -> Accessories menu top-left)
```
sudo apt-get install ntfs-config
```

Then a new menu entry for NTFS drives should appear.  It is self-explanatory from there.

---

### Post by vokillist on 2009-04-03
I also have a Segate External Dive and that code didn't offer any new menus for me. I have ubuntu studio 8.10 installed. I am new to linux and love it so far but I'm hung up on this one thing. I have a cruzer flash drive that I had no problems with just the Segate. If anyone can walk me through another option I would be greatfull.

---

### Post by drs305 on 2009-04-03
vokillist,

Once you have installed ntfs-config you should be able to find it at Applications, System Tools, NTFS Configuration Tool. Or you can open it with:
```
gksudo ntfs-config
```

However, that may not be your answer. Are you sure the drive is NTFS? Secondly, if you used it in Windows, are you sure you shut it down correctly. If not, mount it back in Windows and use Safely Remove to unmount it and correct any errors.

Finally, if you plug it in on Ubuntu, have you tried the "mount" command to see which drives are mounted (and make sure it isn't mounted somewhere you haven't looked)?

---

### Post by vokillist on 2009-04-03
It's NTFS. I found the NTFS configuration tool in system tools and it gives me one option : "Enable write support for external device". I have tried it with and without that option checked and still no luck on mounting the Segate.

---

### Post by drs305 on 2009-04-03
Try mounting it manually with this command. If it doesn't mount, please give us the error message.

First make a mount point, then mount the drive. Make sure you change the sd[COLOR="DarkRed"]**XX**[/COLOR] with your device. If you don't know what it is, run "sudo blkid".

```

sudo mkdir /media/mydata
sudo mount /dev/sd[COLOR="DarkRed"]**XX**[/COLOR] -t ntfs /media/mydata 

```
Example: sudo mount /dev/sdb1 -t ntfs /media/mydata

---

### Post by vokillist on 2009-04-03
Many apologies, I was in the mind frame that if I had windows on the same computer that Ubuntu was on that I had to use the "Safely Remove" option. I have Windows Vista on another machine and when I pluged the Segate back into it and then used the "Safely Remove" option it worked. Thank you so much for the help, I hope other people can benefit from this thread.

---

### Post by WitchCraft on 2009-04-04
> **vokillist said:**
> Many apologies, I was in the mind frame that if I had windows on the same computer that Ubuntu was on that I had to use the "Safely Remove" option. I have Windows Vista on another machine and when I pluged the Segate back into it and then used the "Safely Remove" option it worked. Thank you so much for the help, I hope other people can benefit from this thread.

If you didn't safely remove the drive, you can still mount it in Ubuntu (just that it doesn't mount automatically):

Go to console/terminal, type:
```

sudo mkdir /mnt
sudo mkdir /mnt/disk
sudo mount -t ntfs-3g /dev/sdb1 /mnt/disk **-o force**

```where /dev/sdb1 is the device file for your external usb drive

Please not that making folders for your drives in /media as recommended before is (although it works) NOT a good idea, because /media is used by HAL, and in the event HAL automounts a drive with the same name as one that you mounted manually, it COULD overwrite the data on your manually mounted disk...

---

### Post by Blanchard on 2009-04-08
This solution here help me with my problem using an external hard drive with my Mini 9.  Make sure it is connected to the Internet. Make sure the external HD is connected.

Re: Cannot Mount Volume - Ubuntu 8.04 - external usb ntfs drive 
________________________________________
Hey RLJ, fellow noob here...

I ran into the same problem and did some google researching and ran across this. It fixed my problem for me. Apparently my external MY BOOK 500gb NTFS HD and yours as well has an internal Log File which says whether or not it was shut down properly. You need to clear that log file and someone somewhere created a very handy program to do just that. Here are the commands to enter into the terminal to get the program and then to tell it to fix your particular device.

sudo apt-get install ntfsprogs

- ok That will get the program ntfs fix that you need the next command will tell it to fix your drive, make sure your drive is plugged in at this point:

sudo ntfsfix /dev/sdb1

now the "sdb1" is the particular device which is popping that error cannot mount message at you. In order to find out what the device is designated as, plug in the device, wait for the error to pop up and then look at the error details. It should tell you /dev/sdb1 or /dev/sdb2 or something to that extent. In my case and most likely in yours if you don't have any other usb storage devices plugged in it is probably sdb1.

This work like a charm for me, the program ran and cleared the log file, then proceeded to mount the drive for me, I was then able to access the drive.

Hope it works for you to, cheers!
Halfling

---

### Post by syednabi on 2009-04-15
Please help, or point me to appropriate doc.

I just installed Ubuntu 8.10 in Dell M60 laptop. No windows, its completely Ubuntu.

My primary HD is partitioned as following
:~$ sudo blkid
/dev/sda1: UUID="cb0facfc-285f-410d-b6f7-e957d1cefcb7" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="88a3bd52-5941-4e40-8e36-2a119760dfaa" 

Now I am trying to use access WD External HD (contain windows documents) via USB.

I connected the drive and powered up but, can't find the drive. Following message is in the message.log

[175856.111194] Unknown InputIN=eth1 OUT= MAC=ff:ff:ff:ff:ff:ff:00:1b:ea:c8:23:d6:08:00 SRC=0.0.0.0 DST=255.255.255.255 LEN=328 TOS=0x00 PREC=0x00 TTL=64 ID=22756 PROTO=UDP SPT=68 DPT=67 LEN=308 


Can you please help me to sort out the issue, and guide me on how to activate the USB to recognize and mount USB external drive with FAT/NTFS.

Thanks.
SyedNabi

---

### Post by drs305 on 2009-04-15
You can try to run the following commands with your usb drive connected to try to troubleshoot this:

```

mount  # Shows currently mounted partitions/devices. Do you see it?
mount | grep '/dev/' #  For less output
lsusb  # Shows system's usb devices
sudo blkid  # You usb device should show up if it is recognized.

```

---

### Post by deanbug on 2009-05-06
> **ugm6hr said:**
> If you want to use NTFS:

Open terminal (in Applications -> Accessories menu top-left)
```
sudo apt-get install ntfs-config
```

Then a new menu entry for NTFS drives should appear.  It is self-explanatory from there.

Thank you.  That worked.  I had went to SPM and installed ntfs support, but i have must have missed one.  I am very impressed with the community support.

---

### Post by aggiebill on 2009-05-06
> **ugm6hr said:**
> If you want to use NTFS:

Open terminal (in Applications -> Accessories menu top-left)
```
sudo apt-get install ntfs-config
```Then a new menu entry for NTFS drives should appear.  It is self-explanatory from there.

I followed this advice and it worked for me!  

The menu item was under System -> Administration -> NTFS Configuration Tool.  I then check marked "Enable write support to external disk" and was good to go.  I am using Jaunty 9.04

---

### Post by DeveloperNils on 2009-05-28
I'm new to the forum but not new to UNIX and Linux. However, having said that I have been "retired" for about 8 years (after over 30 years as a software design engineer and embedded OS developer) and am rusty but still remember enuff to be dangerous.

**But I have a problem that is driving me nuts right now.**

I have been following the thread relating to **can't mount an external USB hard drive formatted NTSF **. So far I have not seen anything here that even comes close to fixing the problem. I have tried several ***fixes*** nothing works so far.

I am using a 250GB USB NTSF external hard drive. It does not automatically mount when booting or when I unplug and re-plug and gives me a message "Cannot mount volume. [unclean shutdown failed to mount /dev/sdb1]"

I have plugged and unplugged and it disappears and reappears in the /dev/ table so it is being recognized. It is not listed in /dev/fstab so when I attempt to mount it gives me an error "Cannot mount volume... not in fstab".

The error tells me that it was not closed properly.

**mount /dev/sdb1**
**mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab**

I've had my Mini9 for about a month (it's loaded with Ubuntu 8.10) and everything has been working as expected. I am needing to put a lot of engineering software like CAD and other development software and files on the ext. hard drive. The 8GB of Mini9 RAM is already about half used.

I really need some help figuring this out. Would appreciate a serious solution to this.

---

### Post by ugm6hr on 2009-05-28
That error means that you did not "safely remove the USB drive" from Windows.

Easiest solution is to plug it into a Windows computer, safely remove it properly, then try Ubuntu again.

---

### Post by drs305 on 2009-05-29
DeveloperNils,

If access to Windows is either not possible or inconventient, you can also clear the "unclean shutdown" messages with the following:
```

sudo apt-get install ntfsprogs  # installs ntfsprogs package
sudo ntfsfix /dev/sd[COLOR="DarkRed"]XX[/COLOR]   # clears the Logfile and fixes common errors; change [COLOR="DarkRed"]XX[/COLOR] to correct designation.

```

---

### Post by ugm6hr on 2009-05-29
> **drs305 said:**
> DeveloperNils,

If access to Windows is either not possible or inconventient, you can also clear the "unclean shutdown" messages with the following:
```

sudo apt-get install ntfsprogs  # installs ntfsprogs package
sudo ntfsfix /dev/sd[COLOR="DarkRed"]XX[/COLOR]   # clears the Logfile and fixes common errors; change [COLOR="DarkRed"]XX[/COLOR] to correct designation.

```

I have never done this.... it is good you can recover this within Ubuntu.

However, I would question the logic in having an NTFS drive if you cannot access an MS computer.

---

### Post by rmeske on 2009-06-06
Hi All,

It has been about 8 years since I last worked with Linux and I have to say I am extremely impressed with how far the installation and Desktop interface has come. I was able to instal on a Thinkpad T43 and it came right up without any major issues except one.  I know this is the Dell area, but this thread matched my issue so I thought I would start here.  If I should post this elsewhere please let me know.

I have two USB drives, a SimpleTech 500GB and a Seagate FreeAgent 1.5TB.  Both are formatted as NTFS.

The SimpleTech came up with no problem, but I am having a problem mounting the Seagate Freeagent drive.  I have tried all the suggestions in this thread and am still having a problem.

When I plug in the drive it does show up in the Computer File Browser but when I attempt to open it with the USB Drive Icon, it gives an error:

Unable to mount location
Can't mount file

When I use sudo blkid it is listed:
/dev/sdb1: UUID="E698B79998B76729" LABEL="FreeAgent Drive" TYPE="ntfs" 

The NTFS Configuration Tool does not list it as a new partition detected. But does allow me to enable write support for external device.  That does not seem to help.

I did safely remove from Windows but tried ntfsfix anyways with no luck.

When I attempt a sudo mount -t ntfs-3g /dev/sdb1 /mnt/disk it does mount and I am able to access it through the File Browser by accessing it through the File System and opening the mnt folder and then accessing the disk folder.  However, if I attempt to open the USB Drive icon it still says Unable to mount.

When connecting, the message log shows:

Jun  6 09:07:40 UT43TSD kernel: [ 1414.953942] usb 5-3: new high speed USB device using ehci_hcd and address 5
Jun  6 09:07:40 UT43TSD kernel: [ 1415.102645] usb 5-3: configuration #1 chosen from 1 choice
Jun  6 09:07:40 UT43TSD kernel: [ 1415.145951] scsi4 : SCSI emulation for USB Mass Storage devices
Jun  6 09:07:45 UT43TSD kernel: [ 1416.214422] scsi 4:0:0:0: Direct-Access     Seagate  FreeAgent XTreme 4115 PQ: 0 ANSI: 4
Jun  6 09:07:45 UT43TSD kernel: [ 1416.231121] sd 4:0:0:0: [sdd] 2930277168 512-byte hardware sectors (1500302 MB)
Jun  6 09:07:45 UT43TSD kernel: [ 1416.233120] sd 4:0:0:0: [sdd] Write Protect is off
Jun  6 09:07:45 UT43TSD kernel: [ 1416.235491] sd 4:0:0:0: [sdd] 2930277168 512-byte hardware sectors (1500302 MB)
Jun  6 09:07:45 UT43TSD kernel: [ 1416.236990] sd 4:0:0:0: [sdd] Write Protect is off
Jun  6 09:07:45 UT43TSD kernel: [ 1416.237009]  sdd: sdd1
Jun  6 09:07:45 UT43TSD kernel: [ 1416.251764] sd 4:0:0:0: [sdd] Attached SCSI disk
Jun  6 09:07:45 UT43TSD kernel: [ 1416.251843] sd 4:0:0:0: Attached scsi generic sg2 type 0

Though I can access the drive by manually mounting, it would be nice to be able to mount/unmount it through the USB Drive Icon.

Any ideas?

Thanks,
Ron

---

### Post by drs305 on 2009-06-06
I don't know if the system is having a conflict because you have two separate usb drives or not, but you can probably solve it with an entry in fstab. Although fstab is more for permanent drives, in this case it might provide an automount capability that you are currently lacking.

I would do a couple of things. First, I would make a unique label for it. Since you already have run ntfsfix, you have ntfsprogs installed. Make the label like with this command. Throughout this post I will use "mydata" as the label and mount point (they don't have to be the same name) and sdXX as the designation of the drive. Use "sudo fdisk -l" to determine what the drive designation really is. Change accordingly.
```

sudo ntfslabel /dev/sd[COLOR="DarkRed"]XX[/COLOR] [COLOR="DarkRed"]mydata[/COLOR]

```

Next make a mount point for the device to automount on and make yourself the owner. If you don't want it to display on the Desktop, use /mnt instead of /media:
```

sudo mkdir /[COLOR="DarkRed"]media/mydata[/COLOR]
sudo chown -R *[COLOR="DarkRed"]yourusername[/COLOR]*: [COLOR="DarkRed"]/media/mydata[/COLOR]

```

Next, open fstab for editing and add the device. This command assumes your uid is 1000. You can check with the "id" command:
```

gksudo gedit /etc/fstab

```
Add this line:
> 
LABEL=[COLOR="DarkRed"]mydata[/COLOR] /[COLOR="DarkRed"]media/mydata[/COLOR] ntfs auto,users,uid=[COLOR="DarkRed"]1000[/COLOR],umask=027,utf8 0 0


Finally, unmount and attempt to mount it. If you get no error messages when mounting it, the fstab entry is correct:
```

sudo umount /dev/[COLOR="DarkRed"]sdXX[/COLOR]
sudo mount -a

```[COLOR="DarkRed"][/COLOR]

---

### Post by rmeske on 2009-06-06
Actually I have the same issue whether using one or two USB drives.

Thank you for the information on adding it to fstab.  This saves me from having to manually mount it.  However, it does not solve the issue of having the drive listed under computer:/// and not being able to mount and unmount it from there.  Any ideas as to why this is an issue?  

Seems to be possibly related to the USB plug&play function.  It shows an icon for the drive when plugged in and takes it away when I unplug the drive.

At least for now I can manually unmount the drive when I need to unplug it and then manually run the auto mount upon plugging it back in.

---

### Post by drs305 on 2009-06-06
> **rmeske said:**
> Actually I have the same issue whether using one or two USB drives.

Thank you for the information on adding it to fstab.  This saves me from having to manually mount it.  However, it does not solve the issue of having the drive listed under computer:/// and not being able to mount and unmount it from there.  Any ideas as to why this is an issue?  

Seems to be possibly related to the USB plug&play function.  It shows an icon for the drive when plugged in and takes it away when I unplug the drive.

At least for now I can manually unmount the drive when I need to unplug it and then manually run the auto mount upon plugging it back in.

I dragged out an NTFS external drive and played with it for about 30 minutes trying to duplicate the problem.

Before adding it to fstab, did you get an error message: "Invalid mount option when attempting to mount the volume ..."

If so:

I got that message and was able to eliminate it. If you are interested in experimenting (no possible damage to your NTFS external), here is how I got it to restore what is supposed to be the default behavior. 

1. Disable the entry in fstab (so it doesn't override the test). Place a comment symbol # at the start of the line referencing the external device.
Try plugging in your external and make sure it still doesn't work properly and that fstab doesn't let it automount.

2. Open gconf-editor:
```

gconf-editor /system/storage/default_options/ntfs/

```

2a. In the right pane, right click on both entries and delete them so there is nothing in either the fstype_override or mount_options.
2b. Do the same thing in the next folder, ntfs-3g.
(Don't delete the keys, just the contents)


You don't need to copy the settings before removing them. Right click, "unset" restores the default settings.

With both ntfs and ntfs-3g containing empty values, try plugging in the external and see if it behaves as it should. Mine did. I then restored all the values to their defaults (RC, "unset") and everything still worked.

While you have gconf-editor open, if you wish you can change the automounting default from the /apps/nautilus/preferences/media_automount listing. Just below is the option to set for whether nautilus opens each time an external device is mounted.

Maybe this will work for you.

Don't forget to go back and re-enable the fstab line if you wish.

---

### Post by rmeske on 2009-06-08
Though I am not getting that error, I tried your suggestions but still have the same issue.  I did some searching on the Seagate Freeagent drives and apparently these are known to have problems with Linux.  There was actually a fix made to the Kernel to take care of some of the issues, like the drives power save feature causing the USB connection to be dropped.  Mounting of these particular drives still seems to be problematic.  My entry in fstab had to use the UUID as the Label did not always work.

Looks like I will be shopping for another USB drive and this time I will check on it's Linux support.

Thanks to all of you who helped!

---

### Post by djrudra on 2009-08-06
> **ugm6hr said:**
> If you want to use NTFS:

Open terminal (in Applications -> Accessories menu top-left)
```
sudo apt-get install ntfs-config
```

Then a new menu entry for NTFS drives should appear.  It is self-explanatory from there.


many thanks for this fix..worked like a charm :D

---

### Post by daisy91 on 2009-08-27
Rockygrrl1313,
 
I had a similar problem (possibly).......see the thread for "Attaching an external hard drive" if you haven't yet managed it.......maybe it is the same issue ?
 
 
DOH ! just seen the rest of the thread..........

---

