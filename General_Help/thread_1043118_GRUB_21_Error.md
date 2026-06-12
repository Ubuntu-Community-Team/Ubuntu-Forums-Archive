---
title: "GRUB 21 Error"
date: 2009-01-18
forum: General Help
---

### Post by rbrown653 on 2009-01-18
hey im really new to ubuntu and linux and i installed ubuntu 8.10 on my external hard drive.  But when I try to start my computer without my external hard drive I get a GRUB 21 error.  I want to be able to use my computer without the external hard drive attached.  Please help!!!

---

### Post by arctic on 2009-01-18
Seomthing I don't understand is: You have an external drive. There, your OS resides and ALL important information about the bootloader. If you unattach the USB-drive, you cannot boot your system... Errm.. what did you expect?

Anyway: here is how to fix grub:

Reinstalling or fixing Grub after error 21:

   1. Boot into the original Linux system with the external hard drive still installed (or you can boot from a Live Ubuntu CD).
   2. Open up a terminal and type sudo su
   3. Type fdisk -l and locate your Linux boot partition from the list Example: sda1 or hda1
   4. Type grub-install /dev/sdx or grub-install /dev/hdx to reinstall or repair Grub!
   5. Reboot and test!

      Notes: x represents the drive letter a, b, c, d etc. Replace with your actual drive letter.

      sdx= SATA, SCSI or USB devices hdx= IDE devices

All this information can be found in a hurry, using google. ;) The "problem" has been discussed in detail hundreds of times.

---

### Post by rbrown653 on 2009-01-18
I tried this but no luck.  I got all the way up to step for but i couldn't find the boot drive.

All I really need is to be ablt to go right to the windows loader when I turn on my laptop.  Is there a way to change bios or my laptop so that it skips grub altogether

---

### Post by upchucky on 2009-01-18
get advanced supergrub and knoppix to fix. read other posts here about how to do it, advanced supergrub has extra bells and whistles to fix mbr. knoppix live cd has both partition editors that lets u fix rare partition troubles that can happen, knoppix can fix windows files and lets u edit bootloader, xorg, and menu.lst files on non responsive systems

---

### Post by rbrown653 on 2009-01-18
is there a way to just get rid of grub?  so that my comp goes straight to windows loader

then i will install ubuntu on my internal hard drive and start over

---

### Post by caljohnsmith on 2009-01-18
How about following these steps to install Grub to the MBR (Master Boot Record) of your Ubuntu drive:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then to restore a Windows MBR to your Windows drive try:
```
sudo apt-get install lilo
sudo lilo -M  /dev/sda mbr
```
Reboot, and if you set your BIOS to boot the Ubuntu drive, you should be able to at least get the Grub menu, and if you installed Intrepid, you should be able to boot into Ubuntu. If you set your BIOS to boot the Windows drive, you should be able to boot directly into Windows. Let me know how it goes or if you run into problems.

---

### Post by underwhelmed on 2009-01-19
supergrub worked a treat for me.
I've had to use it twice now, once to rescue windows from ubuntu and once the other way round.  it is great! and in this complicated world of code it actually has a proper helpful dialogue.  it can replace the grub with the original windows mbr (as if ubuntu had never been there!)

---

