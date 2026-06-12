---
title: "Loading Hoary on a computer without an OS"
date: 2006-02-21
forum: Desktop Environments
---

### Post by jaiaucuneide on 2006-02-21
I have a old computer apparently w/o an OS (when I turn it on it says Operating System Not Found) :confused: Anyway, I popped in Hoary and booted the computer but it still had the same message :mad: . So, I was wondering if it is possible to boot this version of Linux without an already existing OS...  I have also tried several other version and it does not work.  PLEASE HELP!! :(

---

### Post by dbott67 on 2006-02-21
Yes.  You'll need to get into the BIOS of the computer and change the boot order.  Right now, it may be set to boot from the hard drive or the floppy first.  Just change it to boot from CDROM first.

-Dave

---

### Post by jaiaucuneide on 2006-02-21
I thought the same thing, but I don't think there is BIOS on this computer is doesn't have to option of clicking F_ to enter setup....any other ideas? thanks for your patience[-(

---

### Post by aysiu on 2006-02-21
You may be right. If it's super-old, it may not have a BIOS that allows booting from the CD. You may need a boot floppy of some sort.

However, it's not just the F-keys that get you into the BIOS. Sometimes it's **Escape** or **Delete**--did you try those?

---

### Post by jaiaucuneide on 2006-02-21
NO, **ESC** and **DELETE** Don't work...thank you for your patience...

---

### Post by aysiu on 2006-02-21
I read this on [a site talking about Knoppix](http://digitalmedia.oreilly.com/2005/03/23/linuxmusic.html): > The next challenge was that the ancient computer I had planned to Linuxify, a Toshiba Satellite Pro 430CDT, can boot only from a hard drive or a floppy, not from a CD. (This phonebook-size laptop has a 120MHz Pentium processor, 48MB of RAM, and an 800-by-600-pixel screen.) After examining the options in the Knoppix.net Downloading FAQ, I downloaded [Smart Boot Manager](http://btmgr.sourceforge.net/download.html), a program that interrupts the normal boot process and lets you specify a different boot device. There are several versions; I downloaded sbminst.exe, a DOS program that installs Smart Boot Manager to a floppy disk.

With the floppy and the CD in their respective drives, I restarted the computer. Smart Boot Manager displayed a screen with a number of boot-device choices. I selected "CD-ROM," but Smart Boot Manager said the disc was corrupt. So I went back to the Mac, burned the ISO file to another CD without decompressing it first, copied that file to my XP machine, downloaded a freeware program that burns ISO images to CDs, and tried again. 

---

### Post by dbott67 on 2006-02-21
[QUOTE=jaiaucuneide]NO, **ESC** and **DELETE** Don't work...thank you for your patience...[/QUOTE]

All computers will have a BIOS (without it, your computer wouldn't be able to detect the hard drive & other attached peripherals).   As mentioned though, the BIOS may not support booting from CDROM.

***  What type of computer is it?***  Some computers have fairly obscure commands to get in.  For example, Compaq's BIOS was loaded to a hidden partition on the hard drive; the cursor would jump from the upper-left to the upper right for a couple seconds during boot.  While the cursor was flashing in the upper-right, you would need to press F10.

You could check the manufacturer's web site for a manual or just google the make and model of the computer followed by 'bios' and see if someone has posted the key combo.

If the BIOS was loaded to the hard drive (similar to the Compaq) and has been deleted, you'll need to get to a working computer & download the BIOS installer from the vendor website and copy it to a bootable floppy.  After that, boot from the floppy and install the BIOS.

HTH,
-Dave

---

### Post by jaiaucuneide on 2006-02-21
Its an old compaq presario

---

### Post by dbott67 on 2006-02-21
[QUOTE=jaiaucuneide]Its an old compaq presario[/QUOTE]

During boot does the cursor jump from upper-left to upper-right for a few seconds and then back again? (or it could be the other way around)

If so, press F10 when the cursor jumps and you should get in.

If it doesn't, you'll need to go the the Compaq website and download the BIOS utility for your model.

-Dave

---

### Post by dbott67 on 2006-02-21
I found this website:

[http://www.techadvice.com/tech/B/BIOS_Enter.htm](http://www.techadvice.com/tech/B/BIOS_Enter.htm)

For Compaq Presario - Press <Alt> <Ctrl> <Esc> at boot when you see the "Compaq" log in big letters.

---

