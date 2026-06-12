---
title: "CDROMS wont mount Hardy 8.04"
date: 2008-12-07
forum: General Help
---

### Post by blazercist on 2008-12-07
Hey, randomly my CDROM's won't mount. Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7c673ae4-3daa-4ccc-a801-696a89b1fb62 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4d6d6d0b-7b8f-41f5-8a8e-d0704d3ee297 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0


 Nothing Shows up in Computer in Places regarding CDROM/DVD.


Manually mounting with sudo mount /dev/scd0 /media/cdrom results in the error: mount: special device /dev/scd0 does not exist


I'm stumped, any ideas would be helpful, please ask if you need additional info.

---

### Post by Rocket2DMn on 2008-12-07
What about /dev/cdrom or /dev/dvd - these are usually symlinks to your first cd device.  If neither of those exist, it's possible that your drive is broken, in which case you could look in BIOS to see if it's recognized there at least.

---

### Post by blazercist on 2008-12-07
/dev/cdrom and /dev/dvd yeild the same result, I did check BIOS to see if the drives were recognized and you were correct they are not there.   But what would cause both drives to die at the same time?  perhaps a faulty IDE socket or wire?  I dont want to have to replace my MOBO....

---

### Post by Rocket2DMn on 2008-12-07
If both drives cut out, then I think you are correct, it is either the cable or the board/connector.  Are the two drives in a master/slave IDE setup?  If so, and there is another connector on your board, try plugging them in there, even one at a time.  Are you using an IDE PCI card or is it integrated into the board?  Or are they SATA like your hard drive?  If so, plug try plugging them in where the hard drive is and see if they are recognized (and maybe try booting a livecd since the HD would be disconnected, assuming you have a LiveCD around).
Otherwise try plugging them into another computer using the same cable and then another cable.

I wouldn't image a cable would fail in full, you should at least get errors from it.  With a bad connector, who knows...  In any case, the point I'm trying to make is try everything possible to get the drives working in your machine or another machine before deciding to purchase new hardware.

---

### Post by blazercist on 2008-12-07
Unfortunately I'm afraid there is only one IDE connector on this motherboard and the drives are in a Master/Slave setup.  The IDE connector is integrated, these drives are rather old I've had them for many many years now.  My harddrive is SATA but these drives are IDE.  

Essentially you are saying what I was abstaining and lementing which is opening the case and start mixing and matching to determine the source of the problem... alas I think its my only option at this point.

---

### Post by Rocket2DMn on 2008-12-07
The only thing else I can think of to check is the output of
```
sudo lshw
```
There should be an entry for
```
*-ide
```
which should present some information.  If the entry isn't there, then it seems that it wasn't even detected in software.  You may also consider resetting your BIOS to its default settings in case some IRQs got mixed up.  Many computers also have a method of getting into a diagnostic testing mode during boot - this is usually achieved by doing something when you turn on the computer, like holding the Fn key as you hit the power button.

---

### Post by Rocket2DMn on 2008-12-07
The only thing else I can think of to check is the output of
```
sudo lshw
```
There should be an entry for
```
*-ide
```
which should present some information.  If the entry isn't there, then it seems that it wasn't even detected in software.  You may also consider resetting your BIOS to its default settings in case some IRQs got mixed up.  Many computers also have a method of getting into a diagnostic testing mode during boot - this is usually achieved by doing something when you turn on the computer, like holding the Fn key as you hit the power button.

---

### Post by blazercist on 2008-12-07
Two entries, I see no mention of CDROM, bbut here they are anyway, it looks like its just the controllers.  I have to look in to resetting BIOS as you've mentioned.  I don't see though how my IRQ's could've gotten screwy if I haven't changed any hardware....   Thanks by the way Rocket for helping this whole time.

*-ide:0
             description: IDE interface
             product: 82801IB (ICH9) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             logical name: scsi0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=ata_piix latency=0 module=ata_piix




 *-ide:1
             description: IDE interface
             product: 82801I (ICH9 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0 module=ata_piix

---

### Post by Rocket2DMn on 2008-12-07
I don't know if the information from lshw is appearing based on information that is simply stored in ROM somewhere on the motherboard or if it reads that information dynamically.  It's strange since you said the BIOS couldn't find the drives.  Hopefully this just means its a problem with the cable, or just the hardware.  You will need to plug other devices in to know for sure - for example, can it read an IDE hard disk?  Let me know what else you find.

---

