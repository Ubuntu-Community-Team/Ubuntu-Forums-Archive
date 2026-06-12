---
title: "Is it possible to use GRUB to boot from USB drive?"
date: 2009-02-03
forum: General Help
---

### Post by slew on 2009-02-03
Hello,

I am using a Sony Vaio VGN-FS715/W and I'd like to know if I can configure GRUB to search for and boot from a USB drive.
I've looked around and found some information on upgrading/changing the BIOS but the BIOS upgrade requires Windows and I can't tell if the BIOS upgrade will include USB boot support. 
The CD-ROM drive on this computer is broken and I'd like to try some other Live CD's while I wait to save money for a new drive.

Thanks a ton!

Intrepid / Ubuntu Studio

---

### Post by 1ronlung on 2009-02-03
80% sure the answer's yes.

Personally, I've kbuntu installed on a usb drive and used super grub disk to set the mbr to kbuntu on it.
When I wanna boot Linux, I use a one time boot menu to boot from USB.

On Super Grub Disk, USB and Laptop drives are listed as the same drive type, so can't see why you couldn't boot from both, but would expect an error if USB drive unplugged ..

---

### Post by slew on 2009-02-03
Thanks for your reply.

What is Super Grub Disk? Is this a program that I can install?

---

### Post by 1ronlung on 2009-02-03
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

can be dl/d free of charge onto floppy, usb, CD

Utility to deal with Windows and Linux booting.  Especially useful if you can't boot into either at all.

A couple of times I've had to resort to using it when the MBR of my USB Linux got fecked :)

---

### Post by caljohnsmith on 2009-02-03
You can download the Super Grub Disk from [here]("http://www.supergrubdisk.org"). Once you burn that, how about booting it, and at the main menu, press "c" to get the Grub command line, and then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
Those commands should show the size and partitions on your internal HDD and also (hopefully) your USB drive. Please let me know if one of them is the USB drive (most likely (hd1)), or let me know the output of those commands if it is not clear. We can work from there if you want.

---

### Post by slew on 2009-02-04
Thanks guys!

This looks like something I could use, except that my cdrom drive is broken and wont boot, burn or spin at all. It's been relegated to cup-holder status. 
Are there any other suggestions that don't require booting or using the cd rom drive? 
Thanks again!

---

### Post by caljohnsmith on 2009-02-04
Do you have a floppy drive? If so, it's possible to make a Grub floppy disk. Or do you have Grub all ready installed to your computer? If you do, you can run those Grub commands from your installed Grub. What drives do you have available that will boot?

---

### Post by slew on 2009-02-04
No floppy drive, this is a laptop computer. The only thing that WILL boot is the hard drive. I already have Grub installed. I'll try the commands when I get home from work today. 

Thanks!!

---

### Post by slew on 2009-02-04
Update..
I tried the options listed but grub didn't find anything for hd1, 2, 3, 4, etc up to 9. I tried editing /boot/grub/device.map with (hd1)	/media/USB DRIVE but, of course, no luck. If I put the usb drive in a usb port I can see the drive is there with the File Browser, but I can't figure out how to map the drive to the boot options.

---

### Post by caljohnsmith on 2009-02-04
OK, there's another boot manager that might be able to help you; it is called "PLoP", and it has its own built-in USB drivers. Consequently, it can often boot USB drives even when your BIOS has no support at all for USB booting. And the good part is you can still keep Grub, but you will just make PLoP another boot option in your Grub menu. So to give it a try, how about downloading the [plpbt-5.0.zip]("http://download.plop.at/files/bootmngr/plpbt-5.0.zip") file to your desktop, and then do:
```
cd ~/Desktop
unzip plp*.zip
sudo cp plp*/plpbt.bin /boot
```
Then pull up your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add PLoP to the Grub menu with:
```
title PLoP
root [COLOR="Blue"](hdX,Y)[/COLOR]
kernel /boot/plpbt.bin
```
Of course change (hdX,Y) to whichever is your Ubuntu partition. Then reboot, select PLoP from Grub, and select the option to boot a USB drive from the PLoP menu. Let me know how far you get.

---

### Post by slew on 2009-02-05
Hi,

I downloaded and installed Plop, rebooted and selected the USB drive to boot. The little red light blinks once on the usb drive and I see "Starting up.." but nothing happens.

I have started with following [these]("http://www.pendrivelinux.com/usb-gentoo-20070-install/") directions. 

I might try another distro from that page, not sure yet..

Thanks for your help!

---

