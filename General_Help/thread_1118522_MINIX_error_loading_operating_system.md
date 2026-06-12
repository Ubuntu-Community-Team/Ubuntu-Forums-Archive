---
title: "MINIX: error loading operating system"
date: 2009-04-07
forum: General Help
---

### Post by hey_ram on 2009-04-07
hi all,

i have ubuntu (hardy heron) installed on my system along with windows xp. 
as a fun thing, i wanted to try and install MINIX3 on my system too. but i wanted to Install it on a 2 GB USB drive that i am not using. the steps that i tried are:

1. downloaded the compressed image.
2. uncompressed it and stored it on the destination disk.
3. re-started the system and made the USB the primary boot device.
4. re-booted
5. upon re-booting, the system comes up with an error message:
"error loading operating system"

i cant figure out why i am getting this error. i checked the MD5 sums for the image. they confirm with the ones listed on the website.

any help will be appreciated. thanks!

---

### Post by mixmaster on 2009-04-07
You don't say which filesystem you used.  Are you sure that the bios of your system can boot from the fs on the USB stick?  A lot of older bios required that there be a bootable DOS partition.

---

### Post by hey_ram on 2009-04-07
hi,

the destination USB stick has a filesystem of type VFAT (FAT16). is that what u meant?

---

### Post by mixmaster on 2009-04-07
From the MINIX3 FAQ on hardware requirements (my emphasis):

> 
1.5. Peripherals

A small number of peripheral devices (audio cards, etc.) are supported. ***Currently there is no support for USB ***or FireWire. 

I think you are on a loser here.

---

### Post by hey_ram on 2009-04-07
but if I can install minix on a USB, and my BIOS supports booting from a USB disk, i think the system will emulate a hard disk and boot from the USB as if it were a normal hard disk. 

i looked up some forums which say that the USB must have an MBR (master boot record). any ideas how to create that?

---

### Post by kerry_s on 2009-04-08
are you sure you got the usb image?

[http://www.minix3.org/download/usb_image-3.1.2a.bz2](http://www.minix3.org/download/usb_image-3.1.2a.bz2)

looks like the newer versions are iso, so i would grab this->
[http://www.minix3.org/download/minix3_1_4_ide_r4220.iso](http://www.minix3.org/download/minix3_1_4_ide_r4220.iso)

and use this-> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

to install it to usb, it does all the work.

---

### Post by hey_ram on 2009-04-08
the usb images need to Be decompressed to give the iso files. 

the application that kerry_s suggested at the moment does not seem to be supported for Minix.

any other suggestions?
il try pretty much anything...

---

### Post by kerry_s on 2009-04-08
try the unetbootin, you point it to the iso you downloaded and the usb drive you want it on, it will do it's thing and unpack the iso to the flash drive and sets up the boot.

your doing this part:

> Installing Other Distributions Using UNetbootin

Download and run UNetbootin, then supply it with the appropriate ISO (CD image) file, floppy/hard disk image, or kernel and initrd files when prompted (see screenshot). Check your distribution's download page to find the appropriate file; if in doubt use the ISO file.

screenshot

If you're loading an ISO file or floppy/hard disk image, that's all that's required (just press "OK" to start installing); otherwise if you're manually specifying kernel and initrd files and you'd like to specify special booting options, check the distribution's boot configuration files (usually after the "kernel" line in either isolinux.cfg, syslinux.cfg, menu.lst, or grub.conf) and supply them on the "Option" line.

---

### Post by hey_ram on 2009-04-11
hi!

i tried the unetbootin option as well, but no luck. the documentation does not suggest that it can be used for Minix. in the "what does it do" section, it says that the application uses the .iso image file and creates a syslinux config file, making my USB drive bootable using that. 

these are the steps that i follow:
1. specify the .iso image file after starting the unetbootin script and entering root password.
2. once this is done, the script takes care of everything and asks for a reboot.
3. upon reboot, I entered the BIOS settings and altered the boot order to make the USB drive (which was shown correctly in the devices attached to the system) the primary boot device. 
4. re-start the computer. 

this is where problems seem to emerge.

the boot process then enters a screen which has "Default" written on the top of the screen. toward the middle are these lines:

"Press [Tab] to edit options
Automatic boot in 10 seconds"

Upon pressing the [Tab] key, a screen shows up which has the following written:
/ubnkern initrd = /ubninit

what do i do from here???

any suggestions?

---

### Post by hey_ram on 2009-04-11
but the maximum success i have had so far has been with qemu.

i am able to start the install process, but it just seems to hang in the beginning itself.

it starts off by asking if I want to install regular minix or just the smaller version of it. 

after that qemu just hangs with the line "reading boot image image"

any help is most welcome.
thanks.

---

### Post by hey_ram on 2009-04-17
i finally had to download minix 3.1.0 and make an install.

i did manage to get it to run on qemu, though there are issues with networking etc...

thanks for helping out,
appreciate it!

---

