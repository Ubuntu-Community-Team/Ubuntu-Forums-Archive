---
title: "530n bios 1.0.15 ?"
date: 2008-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bfallik on 2008-08-19
I noticed that Dell released BIOS 1.0.15 for the 530, but these doesn't seem to be available when I run update_firmware.  Anyone know the reason for this?

I'm trying to resolve a (maybe BIOS?) related problem where my 530N doesn't always recognize a WD My Book attached via eSATA.  The machine has never detected the drive via a hotplug, but until recently was able to detect it when booting.  Now not even the BIOS detects it.  IIRC I have not modified the BIOS from its shipped version nor changed any settings.  I thought to update the BIOS as a first attempt at a fix.

Thanks in advance.

---

### Post by bfallik on 2008-08-24
bump?

---

### Post by linux_tech on 2008-08-24
What does update_firmware do when you run it?
Did you reboot the system after update_firmware?

1. Go to System>Administration>Software Sources . On the Ubuntu Software tab click on the option that says: Community-Maintained open source software (Universe)
2. Open a terminal and run the following commands: 
```
sudo wget -q -O - http://linux.dell.com/repo/firmware/bootstrap.cgi | bash 
``` 
```
sudo aptitude install firmware-addon-dell sudo aptitude install $(bootstrap_firmware -a) 
``` 
```
sudo update_firmware
``` 

3. The system will need to reboot to flash the bios. Once that is done you have successfully flashed your bios on your Dell. If you would like your system to automatically update your firmware: In a terminal type: perl -p -i -e 's/^#rpm_mode=.*/rpm_mode=auto/' /etc/firmware/firmware.conf 

Info here- [http://linux.dell.com/wiki/index.php/Repository/firmware#Downloading_firmware](http://linux.dell.com/wiki/index.php/Repository/firmware#Downloading_firmware)
and [http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx](http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx)

Another way to flash bios- [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

---

### Post by prinknash on 2008-08-25
> **bfallik said:**
> I noticed that Dell released BIOS 1.0.15 for the 530, but these doesn't seem to be available when I run update_firmware.  Anyone know the reason for this?

I'm trying to resolve a (maybe BIOS?) related problem where my 530N doesn't always recognize a WD My Book attached via eSATA.  The machine has never detected the drive via a hotplug, but until recently was able to detect it when booting.  Now not even the BIOS detects it.  IIRC I have not modified the BIOS from its shipped version nor changed any settings.  I thought to update the BIOS as a first attempt at a fix.

Thanks in advance.

I've never managed to work out quite how to update the BIOS on my Inspiron 530N from Ubuntu (the only operating system on that computer) so I made a Bart PE CD which I use to create a Windows environment just for that purpose. Works fine, and I've upgraded the BIOS two or three times from the initial version that came with the machine. It's now running 1.0.15.

p

---

### Post by bfallik on 2008-08-25
> **prinknash said:**
> I've never managed to work out quite how to update the BIOS on my Inspiron 530N from Ubuntu (the only operating system on that computer) so I made a Bart PE CD which I use to create a Windows environment just for that purpose. Works fine, and I've upgraded the BIOS two or three times from the initial version that came with the machine. It's now running 1.0.15.

p

Thanks for the idea, but it seems like Bart PE requires Windows installation media, which I don't have.  Strange that the BIOS update didn't work.  Perhaps more investigation is required.

---

### Post by bfallik on 2008-08-25
> **linux_tech said:**
> What does update_firmware do when you run it?

Did you reboot the system after update_firmware?

Please give more info on steps you did.
Info here- [http://linux.dell.com/wiki/index.php/Repository/firmware#Downloading_firmware](http://linux.dell.com/wiki/index.php/Repository/firmware#Downloading_firmware)
and [http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx](http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx)

Another way to flash bios- [http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)

Thanks for your reply.  No, I didn't reboot after update_firmware since u_f didn't actually make any changes.

I originally followed steps from the link you posted to linux.dell.com, however IIRC the steps don't identity or attempt to install a viable update.  No update is found automatically by the script.

I do believe I could manually download and install the firmware, but I'm wondering why the automatic process doesn't suggest any installation.

Thanks.

---

### Post by kaffa on 2009-06-03
STILL can't update my BIOS - trying to upgrade to 8GB of ram, only 3.2GB is being detected..  PLEASE HELP!

```
bryan@dell-desktop:~$ sudo getSystemId 
Libsmbios version:      2.2.13
Product Name:           Inspiron 530
Vendor:                 Dell Inc.
BIOS Version:           1.0.5
System ID:              0x020D

```

```
bryan@dell-desktop:~$ sudo aptitude install $(bootstrap_firmware -a)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2936-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2935-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2934-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x293a-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x10c0-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2916-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2930-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2920-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2926-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x293e-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x29c0-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2937-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2938-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2939-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x10de-dev-0x0402-subven-0x10de-subdev-0x0505"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x293c-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x244e"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x29c1"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2936-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2935-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2934-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x293a-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x10c0-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2916-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2930-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2920-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2926-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x293e-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x29c0-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2937-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2938-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x2939-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x10de-dev-0x0402-subven-0x10de-subdev-0x0505"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x293c-subven-0x1028-subdev-0x020d"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x244e"
Couldn't find any package whose name or description matched "pci-firmware-ven-0x8086-dev-0x29c1"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

### Post by coffeeaddict22 on 2009-06-03
Have you looked [here]("http://linux.dell.com/projects.shtml")? I've upgraded my laptop BIOS in Linux ( no prob) a week or two back, so I can vouch for it working.

---

### Post by Talon2 on 2009-06-03
> **kaffa said:**
> STILL can't update my BIOS - trying to upgrade to 8GB of ram, only 3.2GB is being detected...


 
Are you running the 64 bit version of Ubuntu?

---

### Post by Glendon on 2009-07-20
I'm having this same exact problem. Same machine. Same BIOS. Same errors.

Right now I'm trying the biosDisk method [here]("http://linux.dell.com/projects.shtml").

There seems to be a lot of folks claiming success when I search but I haven't been able to get an update. 

I've tried many methods. 

Hopefully this will work.

---

### Post by Glendon on 2009-07-21
I can't get this to work. 

Here's what I did.

I installed biosDisk (and tofrodos).

Then:

```
sudo biosdisk -o option 530_1015.EXE
cd /tmp
sudo biosdisk install 530_1015.img
```

So far, so good. 

I checked menu.lst to see if it was updated. It was.

```
title  530_1015.img
kernel /boot/memdisk
initrd /boot/530_1015.img
```

I rebooted, hit ESC to get to the Grub menu, selected 530_1015.img and got:

> Error 11: Unrecognized device string
Press any key to continue...

I'm not experienced with manipulating Grub so I'm hoping it's something obvious and easy. 

Any help would be appreciated.

---

