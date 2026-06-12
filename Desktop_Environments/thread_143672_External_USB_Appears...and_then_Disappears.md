---
title: "External USB Appears...and then Disappears"
date: 2006-03-12
forum: Desktop Environments
---

### Post by neorush on 2006-03-12
I recently purchased a Western Digital 160GB "My Book Essential" external drive.
Full Specs: [http://www.wdc.com/en/products/Products.asp?DriveID=217]("http://www.wdc.com/en/products/Products.asp?DriveID=217")
It connects through USB 2.0.

When I plug the drive in it creates all the necessary stuff for auto mounting the device, such as /dev/sdb and /dev/sdb1 (/dev/sda is currently a SCSI drive.) all of these show up in the device manager window and everything.

It does this for about 30 seconds.  All of the Disk tools hang during this 30 second peirod, a fdisk -l hangs until it disappears, opening the Admistration -> disks menu hangs until it disappears, etc.  All of the output from dmesg looks normal.  This drive does try and help by auto spinning down after no use (it works smoothly when plugged into windows), is it trying to spin down? After this "hang" the drive is then unusable, even if I plug it into windows, until I unplug it, the power switch also stops responding.

The drive is formatted as FAT32, but I tried NTFS, and EXT3, so its not a file system problem (formatted from windows).

If I try mounting the drive when its in its "hang" phase the mount command hangs to until it disappears again, and reports that /dev/sdb1 is a bad super block.  I have 2 of these drives and they both do the same thing, so its not a drive defect.  Has anyone experienced this before?  Any help would be great.

---

### Post by dcstar on 2006-03-13
[QUOTE=neorush]
......
If I try mounting the drive when its in its "hang" phase the mount command hangs to until it disappears again, and reports that /dev/sdb1 is a bad super block.  I have 2 of these drives and they both do the same thing, so its not a drive defect.  Has anyone experienced this before?  Any help would be great.[/QUOTE]
Open a terminal and run ```
dmesg
``` continually when you plug them in, you may see a message that is relevant to the problem.

---

### Post by neorush on 2006-03-13
[4325107.619000] usb-storage: device found at 18
[4325107.619000] usb-storage: waiting for device to settle before scanning
[4325188.747000] usb 1-1: reset full speed USB device using uhci_hcd and address 18
[4325191.815000] usb 1-1: device descriptor read/64, error -110
[4325206.981000] usb 1-1: device descriptor read/64, error -110
[4325207.144000] usb 1-1: reset full speed USB device using uhci_hcd and address 18
[4325210.209000] usb 1-1: device descriptor read/64, error -110
[4325225.384000] usb 1-1: device descriptor read/64, error -110
[4325225.547000] usb 1-1: reset full speed USB device using uhci_hcd and address 18
[4325230.562000] usb 1-1: device descriptor read/8, error -110
[4325235.676000] usb 1-1: device descriptor read/8, error -110
[4325235.839000] usb 1-1: reset full speed USB device using uhci_hcd and address 18
[4325240.854000] usb 1-1: device descriptor read/8, error -110
[4325245.968000] usb 1-1: device descriptor read/8, error -110
[4325246.069000] usb 1-1: USB disconnect, address 18
[4325246.074000] usb-storage: device scan complete
[4325246.204000] usb 1-1: new full speed USB device using uhci_hcd and address 19
[4325249.272000] usb 1-1: device descriptor read/64, error -110
[4325264.441000] usb 1-1: device descriptor read/64, error -110
[4325264.604000] usb 1-1: new full speed USB device using uhci_hcd and address 20
[4325267.670000] usb 1-1: device descriptor read/64, error -110

I googled these errors but found nothing useful...any ideas?

---

### Post by TheFaction20 on 2006-03-27
anyone got any help for us....cuz im experiencing this same exact problem with the same exact hard drive.

---

### Post by grappler on 2006-05-02
Hi

I'd like to know if you've solved this problem. I've had exactly the same problem on an IBM Thinkpad T41 running SUSE 10.0 linux and have spent a long time trying to solve it. I have come to the conclusion that it's a hardware fault.  I'd be interested if you're using the same hardware. I find that the problem doesn't occur on a slightly later version of the same laptop (T43).

---

### Post by grappler on 2006-05-02
Hi 

After having this problem for over a year with  every kind of flashdisk or hard drive attached by usb connector I think I have found a solution. 

Check out: 

[http://www.redhat.com/archives/fedora-list/2004-December/msg04693.html](http://www.redhat.com/archives/fedora-list/2004-December/msg04693.html)

The key commands are
 
modprobe -r ehci_hcd 

(remove this module)

modprobe ohci_hcd

(insert this module)

Then I could mount in the usual way - create a directory

mkdir /media/usbdisk (or maybe /mnt/usbdisk in ubuntu)


then assuming the device is /dev/sda

mount /dev/sda /media/usbdisk

This works!

---

### Post by speedybits on 2006-05-02
I've seen this happen with a GE 32MB USB drive, but it turned out that it was a loose USB connector on the drive itself. Just my 2 cents...

---

### Post by 89c51 on 2006-05-03
i am experiencing the same problems with my wd mybook essential (on ubuntu hoary that i have installed on my laptop)

itried the modeprobe -r ehci_hcd solution but it didnt help 

the driver uses the uhci_hcd and it gives me errors and i cant use the drive




on my gentoo box everything works fine:confused: :confused:

---

### Post by mattcole on 2006-05-04
grappler:

You, sir, are a gentleman and a scholar.  Fixed my problem in <10 s.

Rock.

Matt

---

### Post by Sendervictorius on 2006-05-05
I too have the problem, but only when I plug my usb flash drive into my usb hub. When I plug it into the usb port on my PC, it works fine. - Means to me there is a hardware fault somewhere, but other usb devices work ok on the hub.

The cycle time is around 5 seconds, between automounts - very irritating.

I tried the modprobe solution, and it fixes the problem allowing me to use the usbflash through the hub. However, after I reboot the problem comes back - until I do the modprobes again.

How do I make it permanent?

---

### Post by neorush on 2006-08-14
I've upgraded to Dapper 6.06, works now...wish I know what changed...6 is pretty sweet, just about everything works great now...

---

