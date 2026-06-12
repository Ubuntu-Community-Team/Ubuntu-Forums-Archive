---
title: "USB key cannot find kernel image : linux"
date: 2009-02-09
forum: General Help
---

### Post by belbrux on 2009-02-09
I installed ubuntu 8.10 on a USB key with the software "Create a startup disk". System -> Administration-> Create a startup disk.
I made a partition of 2GiB on the USB key with GParted : FAT32 and flagged it as boot. 
I used also unetbootin_304-4_i386 and had the same problem.
My BIOS can boot on a USB key and I installed Ubuntu on 2 different keys.

When I boot on a these USB keys I receive following message :
Searching for Boot Record from USB RMD-FDD .. OK
SYSLINUX 3.63 Debian - 2008-07-15 CBIOS Copyright (C) 1994-2008 H. Peter Anvin
boot:
The PC does not go further . If I type on the ENTER key. I receive the message :
Could not find kernel image : linux. 

N.B. I also verified that all recommended dependencies where installed for unetbootin.

---

### Post by C.S.Cameron on 2009-02-09
Sounds like your CD could be bad.

---

### Post by belbrux on 2009-02-10
I retried my CD live ubuntu 8.10 and it works perfectly. I am using it now to give this answer.

Thanks C.S. Cameron for your suggestion.

---

### Post by C.S.Cameron on 2009-02-12
Wonder if it could have something to do with the partitioning of the disk.
Have you tried deleting the partitions and letting U-C or Unetbootin format the disk?
I've had the problem you described trying to install to an 8GB drive using U-C but Unetbootin ended up working.

---

### Post by belbrux on 2009-02-17
C.S. Camerone,I followed your advice and tried it on a USB key 2GiB with no partitions. Same problem.

Since unetbootin also exists for Windows XP I tried it also with the program unetbootin-windows-312.exe. Same problem, I received following message:
Searching for Boot Record from USB RMD-FDD..OK
SYSLINUX 3.72 2008-09-25 CBIOS Copyright (C) 1994-2008 H.Peter Anvin
boot:

As you see the only difference in the message is the number of the version of SYSLINUX.

My motherboard is an ASRock P4S61 with a ATI Radeon 9600 Pro GameFX Board.
AMIBIOS SETUP UTILITY -Version 3.31a . 
BIOS version : P4S61 BIOS P2.50

---

### Post by old_codger on 2009-02-17
I get exactly the same error. My USB was already formatted with win32 and I used usb-creator. Same 'Could not find kernel image', at the 'Boot:' prompt when I press Enter. If I don't it just sits there. It's obviously booting.

I then tried formatting to win32 with Gparted under ubuntu and then using usb-creator. Exactly the same.

I read on another forum that I should use a ubuntu 8.10 liveCD to boot from and try the same thing.

Exactly the same result.

Any ideas? Anyone???

---

### Post by old_codger on 2009-02-19
OK. Making some headway now :)

Well, sort of :(

I ignored the Ubuntu usb-creator thingie and followed the instructions here...

[http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

and formatted the first partition, (the vfat one), as fat16 as opposed to fat32 as it suggested and now I get a menu up. However, the only ones that work are the ones that say, 'Test memory', or 'Boot from first hard disk'. All the other options that mean booting from '/casper/vmlinuz' just make the machine sit there and stop responding.

Any suggestions?

---

### Post by old_codger on 2009-02-19
OK. making more even headway... again, sort of.

I've left the stick formatted at fat16 and resized the partition from the one set in the link I gave, (750Mb), to the capacity of the stick which is 2Gb. I then used the unetbootin method which some links on these forums suggested and that seems to boot and run OK. In fact, that's how I'm typing this on line now :)

I'm now going to try running the 'USB Creator' thing leaving everything as is, the thinking being, (although its probably wrong), that the booting boot is now running fine.

Actually, as I type tht, I'm not sure it sounds right either :D But I'll try it anyway and let you know. Somebody else said it wrked.

I'll let you know

Andy

---

### Post by old_codger on 2009-02-20
OK! Well that wasn't such a good idea :D

---

### Post by belbrux on 2009-02-21
I also used the instructions "Create Ubuntu 8.10 flash drive automatically"
from pendriveliux :
[http://www.pendrivelinux.com/ubuntu-8.10-persistant-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-8.10-persistant-flash-drive-install-from-live-cd/)

Same error message.

---

### Post by fredfelter on 2009-02-21
I'm having a similar but not identical problem,

I used a new FAT32 formatted 2gb usb key and from WindowsXP opened the live 8.10 Ubuntu CD > Admin > Create USB SU disk > gave it the max reserved space and everything seemed to install well. However when I plug the USB into my new Aspire One with the BIOS changed to boot from it I get a black screen with CCév_ in the upper left corner. No key strokes seem to affect it so nothing happens. 

Any ideas? Thanks.

---

### Post by belbrux on 2009-02-22
I think I have found the beginning of the solution at the pendrivelinux.com site :"How to fix Could not find kernel image : linux error "
[http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux](http://www.pendrivelinux.com/error-could-not-find-kernel-image-linux)

My problem can probably be resolved with 
"3. If the syslinux.cfg file does exist and your still encountering the error,open the syslinux.cfg file with a text editor and make sure that the paths to your kernel and initrd files are correct." 

If I verify the files on my key :
1) I have two syslinux.cfg files  the first at  /syslinux.cfg
                                  the second at  /syslinux/syslinux.cfg
2) I find a intrd.gz file at /casper/intrd.gz
   Why a .gz file which is a compressed file?

If I open syslinux.cfg with a text editor it gives :
include menu.cfg
default vesamenu.c32
prompt 0
timeout 300
gfxboot bootlogo

Can you help me to make the paths to kernel and intrd files correct ?
Thanks in advance.

---

### Post by fredfelter on 2009-02-23
This ¨solution¨ was, I´m sure, well meant but how would I ever do this? 

¨If the syslinux.cfg file does exist and your still encountering the error,open the syslinux.cfg file with a text editor and make sure that the paths to your kernel and initrd files are correct."

As a Linux newcomer with NO experience deciphering OS files and just barely able to use the most basic terminal commands I would have to invest uncountable hours to research this task. If only there were complete step by step instructions from beginning to end for all the most useful elements of Linux usage.

---

### Post by belbrux on 2009-02-28
I found a solution by asking help by the SLAX distro forum:
"format the USB key with FAT (which is FAT16 and do not use Fat32) in   Windows XP ( not Linux).Be careful the key must be smaller than 4 GB.

The keys works perfectly with this distro.

But now I have following problem.
I installed Ubuntu 8.10 with usb-creator .
There is no problem at the install.
When I boot with my Ubuntu 8.10 USB  the installation is donne without problem but immediately after the install there is a FREEZE.
I can not use my Keyboard and my mouse and I must shutdown by pressing the contact key.

---

### Post by adityasv on 2009-03-15
Guys, I finally figured this out.
For USB sizes greater than 1 GB, go to Gparted (sudo gparted).
In gparted,
1. Select the USB device
2. Format as Fat16
3. Check that the flag section only has - boot (I had boot, lba - and had to remove lba)

Exit Gparted.

Then create the USB startup disk from System->Administration->Create USB startup disk.

It works great!

---

### Post by Centrist on 2009-04-08
Using FAT16 worked for me.

I tried FAT32 first, and that got me the kernel image error. I used gparted to format my flash drive to FAT16, unplugged, remounted, and then ran the Intrepid USB startup disk tool. Was able to boot from the USB drive fine after that.

But make sure you unplug/remount before running the startup disk tool, otherwise it will prompt you to format the drive again. I unplugged the flash drive and then plugged it back in to let Ubuntu mount it for me.

---

### Post by nik_gr on 2009-05-09
i did as you said and FINALLY when i got eh Boot prompt and hit enter i got the installation screen.

it asked me about me keybaod but when ti wanted to autodetect my cdrom it failed... also with netowrk drivers.

Somehow the debioan instalaltion thinga that the drivers and stuff are located in the cd/dvd drive instead of the usb key so the instalaltion cannot proceed!

How did you guys manage to overcome these obstacles and let debian aware that the installation files and folder are locatd in the usb key instead?

ps. iam so excted that it finally got booted the kernel :)

---

### Post by nik_gr on 2009-05-11
please help!

---

