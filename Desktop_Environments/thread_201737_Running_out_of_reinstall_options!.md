---
title: "Running out of reinstall options!"
date: 2006-06-22
forum: Desktop Environments
---

### Post by xyz on 2006-06-22
Hi everyone-

The following began to happen after an attempt at an internet-upgrading to Dapper. I've been trying to reinstall Breezy for the past week. 
I'll try to make this as short as possible:

1. I've reinstalled pretty much following the same procedure every time (trying ext3 and/or ext2) /media/hda3 mounted as / - leaving mount options to default - tried to set "Boot flag" to ON or OFF whatever that means!

2. I feel like I've run into just about every possible error in the book and followed many guides about them:

X,unable to parse...,dpkg problem,vesa/vga,,couldn't find the file /etc/apt/sources.list, Error 15,16...,corrupted .deb,kernel panic,GRUB missing and so on.

3. It is advised to reboot after reinstalling but that leads to a non-operational OS,too. Same happens when installing the usual 152 updates. Needless to say the system hangs a lot.
Right now I'm on it but don't dare make the next move (rebooting,downloading updates) and I have no idea how long it'll keep on working this way!

4. should I resrote the "backup.gz" of my system? I've saved it on an external HD.

5. should I download Dapper and install? From what I've been reading lately, I'm not sure this is the right time to do it.

6. Adding Multiverse/Universe repos causes pbms,too.

Thank you so much for your help and time.



Toshiba Satellite A40
2.70 gHz 512 RAM


> Host bridge: Intel Corp. 82852/855GM Host Bridge (rev 02)
 System peripheral: Intel Corp. 855GM/GME GMCH Memory I/O Control Re gisters (rev 02)
 System peripheral: Intel Corp. 855GM/GME GMCH Configuration Process  Registers (rev 02)
VGA compatible controller: Intel Corp. 82852/855GM Integrated Graph ics Device (rev 02)
 Display controller: Intel Corp. 82852/855GM Integrated Graphics Dev ice (rev 02)
 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 03)
 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 03)
 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 03)
 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 83)
0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 03)
 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Contro ller (rev 03)
 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Contr oller (rev 03)
 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 03)
 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem  Controller (rev 03)
0 Ethernet controller: Intel Corp. 82801BD PRO/100 VE (MOB) Ethernet Controller (rev 83)
CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus  Bridge with ZV Support (rev 33)


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


> title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1



Just a little...
> dmesg
ide: failed opcode was: unknown
[4296589.354000] hda: task_out_intr: status=0x51 { DriveReady SeekComplete Error }
[4296589.354000] hda: task_out_intr: error=0x04 { DriveStatusError }
[4296589.354000] ide: failed opcode was: unknown
[4296634.791000] hda: task_out_intr: status=0x51 { DriveReady SeekComplete Error }


---

### Post by yager on 2006-06-22
My system did not survive the update well from Breezy to Dapper.  I had to go with a fresh install using the Dapper CD.  I suggest you go this route so you have a clean install to work from.  Once that is done, you will have a bunch of updates that you need to install, one of which will be a new kernel.

Don't forget to save any critical data files if you have the one partition on your system.

---

