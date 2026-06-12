---
title: "USB drive no longer mountable"
date: 2009-02-05
forum: General Help
---

### Post by Redscare on 2009-02-05
I have an imation 1GB usb drive on which I was trying to install a bootable version of Slackware (specifically Backtrack). I ran the included utility that supposedly made the drive bootable (this I unfortunately had to run through windows; both a '.bat' and '.sh' file are included). I removed the drive after the process finished and restarted the computer. I have since tried booting from the USB and mounting it in both windows and Ubuntu. This machine does recognize other USB's, just not this one. I am assuming that the MBR got messed up due to Vista's stupid user elevation system. The light on the usb does not go on, and it is displayed in the file browser but I cannot mount it; when I double-click on it I get the message "Unable to mount location; No media in the drive". What is strange is that the drive appears and disappears in both OS's as it is connected and disconnected, but I cannot access it. Any help is greatly appreciated.

---

### Post by warp99 on 2009-02-05
I would suggest using UNetbootin to write the image to the pen drive:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I've personally loaded Backtrack using the Linux version without any problems. It does work on both 32-bit and 64-bit machines, but only 32-bit images can be loaded using a 32-bit system and the same for 64-bit since it uses some supporting tools from the repositories. Hope this helps. ;)

---

### Post by Redscare on 2009-02-05
The problem is that I cannot write ANYTHING to the USB. I mentioned this earlier, but although I can see the name "USB Drive" in the file browser (under the computer directory), when I double-click I get an error "Unable to mount location; No media in the drive". Thank you for the response though.

---

### Post by warp99 on 2009-02-05
Unetbootin will repartition the drive and reinstall the image with the correct MBR. You can use the Backtrack ISO you downloaded or choose Backtrack from the drop down list in Unetbootin. 

The drive does not need to be mounted, but just the opposite is needed for Unetbootin to image the drive.

---

### Post by Redscare on 2009-02-05
First of all, thank you for your responses. Unfortunately, this still does not work. Where the program asks for a USB Drive I get a blank dropdown unless I click show all drives, but I do know (but I also do not think that any one of them is indeed) which is my usb drive (/dev/sda(1-7)). If it helps the light on the usb does not light up. So far the only reason I know ubuntu is recognizing it is that it appears in the filebrowser (but is unmountable, all I get is the icon).

Edit: I checked fdisk -l with and without USB, and it is not any /dev/sda{1-7}

---

### Post by warp99 on 2009-02-05
Plug the drive in, wait about 10 seconds then open a terminal and issue the following:

dmesg | tail -n 15

What's the device name (sdb, sdc, etc) that the drive is assigned? That's the /dev/xxx with the xxx replaced with your device name.

Edit:

If you don't know that's the pipe command between the dmesg and tail. It's located just above the "Enter" key.

---

### Post by Redscare on 2009-02-05
I did not understand the output, perhaps you can interpret it for me?
```
redscare@redscare-laptop:~$ dmesg|tail -n 20
[ 5124.273168] sd 10:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 5124.273178] sd 10:0:0:0: [sdb] Sense not available.
[ 5124.273277] sd 10:0:0:0: [sdb] Write Protect is off
[ 5124.273283] sd 10:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 5124.273288] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 5124.273743] sd 10:0:0:0: [sdb] READ CAPACITY failed
[ 5124.273748] sd 10:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[ 5124.273757] sd 10:0:0:0: [sdb] Sense not available.
[ 5124.273854] sd 10:0:0:0: [sdb] Write Protect is off
[ 5124.273859] sd 10:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 5124.273864] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 5136.112192] usb 7-2: new high speed USB device using ehci_hcd and address 8
[ 5136.244887] usb 7-2: configuration #1 chosen from 1 choice
[ 5136.245775] scsi11 : SCSI emulation for USB Mass Storage devices
[ 5136.246870] usb-storage: device found at 8
[ 5136.246881] usb-storage: waiting for device to settle before scanning
[ 5141.244537] usb-storage: device scan complete
[ 5141.245344] scsi 11:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 5141.249215] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 5141.249418] sd 11:0:0:0: Attached scsi generic sg2 type 0

```

---

### Post by warp99 on 2009-02-05
Now we're getting somewhere. Your device is /dev/sdb as indicated here:

```
[ 5141.249215] sd 11:0:0:0: **[sdb]** Attached SCSI removable disk
[ 5141.249418] sd 11:0:0:0: Attached scsi generic sg2 type 0
```

Since the partitions appear corrupted I would suggest repartitioning the drive, which is rather easy. Plug the drive in and issue the following:

sudo fdisk /dev/sdb

That will take you to the interactive menu. Press 'm' to see the menu, then press 'd' to delete your current partitions. Once that's done press 'n' for a new primary partition and make the entire drive one partition. Then press 't' to change the partitions ID and enter the hex code 'c'. One that's done press 'a' to toggle the boot flag on and finally press 'w' to write changes to the drive.

After everything is written pull the drive and reinsert the drive, then issue the following command to format the file system:

sudo mkfs.msdos -F 32 /dev/sdb1

At that point you'll be back were you started and can load the image using Unetbootin.

---

### Post by Redscare on 2009-02-05
Thank you very much for all your help, and I think that you are very close to solving it (my uneducated opinion). Unfortunately, there is another error:
```
redscare@redscare-laptop:~$ sudo fdisk /dev/sdb

Unable to open /dev/sdb

```
Again, thank you very much.

---

### Post by warp99 on 2009-02-05
Well I'm a little stumped at this point. I would reboot the computer then insert the drive and run 'dmesg | tail -n 15' again to see if the system assigns the same device (sdb) or a different one, then try to repartition the drive using fdisk as before. 

If that doesn't work please if you can link to those original scripts you used or attach them to this thread so I could take a look and determine what they did to your drive.

---

### Post by Redscare on 2009-02-05
So I have tried everything I could think of and nothing worked. I suspect the MBR of the drive is messed up, I was wondering how I could fix that. The script that did that is directly from Backtrack (it's the windows script (there is also a bash script) and I stupidly ran it under vista with all its stupid uac), and I think that is what screwed me up. Here is the script:
```
@echo off

cls

set DISK=none

set BOOTFLAG=boot666s.tmp



echo This file is used to determine current drive letter. It should be deleted. >\%BOOTFLAG%

if not exist \%BOOTFLAG% goto readOnly



echo Wait please, searching for current drive letter.

for %%d in ( C D E F G H I J K L M N O P Q R S T U V W X Y Z ) do if exist %%d:\%BOOTFLAG% set DISK=%%d

cls

del \%BOOTFLAG%

if %DISK% == none goto DiskNotFound



echo =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

echo                          Welcome to Slax boot installer

echo =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

echo.

echo This installer will setup disk %DISK%: to boot only Slax.

echo.

echo Warning! Master Boot Record (MBR) of the device %DISK%: will be overwritten.

echo If %DISK%: is a partition on the same disk drive like your Windows installation,

echo then your Windows will not boot anymore. Be careful!

echo.

echo Press any key to continue, or kill this window [x] to abort...

pause > nul



cls

echo Setting up boot record for %DISK%:, wait please...



if %OS% == Windows_NT goto setupNT

goto setup95



:setupNT

\boot\syslinux\syslinux.exe -ma -d \boot\syslinux %DISK%:

goto setupDone



:setup95

\boot\syslinux\syslinux.com -ma -d \boot\syslinux %DISK%:



:setupDone

echo Disk %DISK%: should be bootable now. Installation finished.

goto pauseit



:readOnly

echo You're starting Slax installer from a read-only media, this will not work.

goto pauseit



:DiskNotFound

echo Error: can't find out current drive letter



:pauseit

echo.

echo Read the information above and then press any key to exit...

pause > nul



:end

```
Thanks

---

### Post by Redscare on 2009-02-05
I just noticed something very interesting. With the device plugged in:
```
redscare@redscare-laptop:~$ sudo lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 004 Device 004: ID 1307:0163 Transcend Information, Inc. 512MB USB Flash Drive**
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
Without the device, the bolded line is not there:
```
redscare@redscare-laptop:~$ sudo lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
But the device has a capacity of 1GB. What is going on?

---

### Post by warp99 on 2009-02-05
I would try to restore the mbr by using the syslinux version under Ubuntu. So make sure you have syslinix installed. If not issue the following:

```
sudo apt-get install syslinux
```
Insert your drive and check to make sure that the device is /dev/sdb. Then issue the following string of commands:

```
:~$ sudo bash

:~$ cat /usr/lib/syslinux/mbr.bin > /dev/sdb
```
This will overwrite the mbr with the syslinux version which is known to be valid. Then pull the drive, insert and run fdisk again.

---

### Post by Redscare on 2009-02-05
Thanks again, now I get this:
```
root@redscare-laptop:~# cat /usr/lib/syslinux/mbr.bin > /dev/sdb
bash: /dev/sdb: No medium found

```

---

### Post by Redscare on 2009-02-05
Some new information: It seems progress has been made somewhere, I am getting this output now from dmesg after I connect the device:
```
[ 5585.124243] usb 4-2: new high speed USB device using ehci_hcd and address **9**
[ 5585.263900] usb 4-2: configuration #1 chosen from 1 choice
[ 5585.264530] scsi12 : SCSI emulation for USB Mass Storage devices
[ 5585.264712] usb-storage: device found at **9**
[ 5585.264715] usb-storage: waiting for device to settle before scanning
[ 5590.264472] usb-storage: device scan complete
[ 5590.265360] scsi **12**:0:0:0: Direct-Access     USBest   USB2FlashStorage 0.00 PQ: 0 ANSI: 2
[ 5590.280723] sd **12**:0:0:0: [sdb] Attached SCSI removable disk
[ 5590.281554] sd **12**:0:0:0: Attached scsi generic sg2 type 0
```
The bolded number increases by one with every connection.
Thank you very much for your responses so far.

---

### Post by warp99 on 2009-02-05
There may be a wrong entry in the udev persistent rules file. I would try the following:

First run:
```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules 
```

and delete any of the lines **below** the following lines that have anything to do with the USB drive in question, don't worry the entries will be automatically be regenerated on reboot:

```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
```

Save the file then reboot. Once again try to overwrite the mbr.bin as before.

---

### Post by Redscare on 2009-02-05
None of the lines appear to have anything to do with the USB; please keep in mind that the computer DOES detect other USB's. The code in the persistent rules file:
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DVD+-RW_AD-7640A (pci-0000:00:1f.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
```
Thanks

---

### Post by warp99 on 2009-02-05
I hate to say it but I think that the drive got corrupted by Vista and appears unrecoverable in Linux. According to syslinux boot disks can be made under NT/2K/XP, but there's nothing about Vista:

[http://syslinux.zytor.com/wiki/index.php/SYSLINUX#NT.2F2K.2FXP](http://syslinux.zytor.com/wiki/index.php/SYSLINUX#NT.2F2K.2FXP)

There is a thread over at the Slax forum that has some interesting workarounds when using Vista:

[http://www.slax.org/forum.php?action=view&parentID=6241](http://www.slax.org/forum.php?action=view&parentID=6241)

I would search their site for a solution since I don't have a clue about Vista since I've been pretty much Microsoft free since 2005. :p

---

### Post by Redscare on 2009-02-05
So I've irreparably screwed up the drive?
I'm just surprised I pulled that off using software.

---

### Post by mc4man on 2009-02-05
Out of curiosity, have you tried using a partition editor (gparted or other) on the drive to see if it recognizes what's on the disk and to remove/delete/format so you can start over fresh?

---

### Post by Redscare on 2009-02-05
I have tried looking at the disk in gparted, but this was when I was booted into the main OS. Do I need to do this through a livecd environment?

---

### Post by warp99 on 2009-02-05
> **Redscare said:**
> So I've irreparably screwed up the drive?

Well it's unrecoverable in Linux, but may be recoverable in Vista. The thread I posted at the Slax forums talks about running the script under the admin account. If there's an answer you're most likely going to find it over there.

---

### Post by turantula133 on 2009-02-05
I had the same problem and what worked for me was to # out the sbd line in /etc/fstab.  Might not be permanant but worked for me.

---

### Post by Redscare on 2009-02-07
> **turantula133 said:**
> I had the same problem and what worked for me was to # out the sbd line in /etc/fstab.  Might not be permanant but worked for me.

Unfortunately there is not even an sdb line (although dmesg still reports that the device is detected at sdb).

---

### Post by TopEnder on 2009-02-19
G'Day, I had a similar problem with a USB MP3 player could not mount after deleting some files an a power failure before been able to close the USB/MP3 correctly, would only allow the use of 329Mb instead of 2Gb.  I got the thing working correctly again by re-partitioning using Gparted Partition Editor (Ubuntu), selected correct device (unmounted if necessary Ha!) & then highlighted the partition, deleting it then re-partition the USB/MP3 player to maximum size.  How this helps and you the USB drive working.

---

