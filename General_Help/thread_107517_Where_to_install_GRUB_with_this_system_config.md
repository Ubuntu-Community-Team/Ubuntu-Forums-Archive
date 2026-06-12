---
title: "Where to install GRUB with this system config?"
date: 2005-12-23
forum: General Help
---

### Post by rafaelperrone on 2005-12-23
Im new to Linux and I know I did lots of mistakes, please help me.

Im installing Ubuntu on a system with the folowing config:

1 - 80 GB SATA drive with Win XP
2 - 160 GB SATA drive with Kubuntu
3 - 40 GB IDE drive with lots of MP3 and no OS

When the installation asked me where to place GRUB I chose default option, which is first hard drive. I was expecting for it to insall on my first SATA drive, which is the WinXP one. But it installed on the first IDE drive.

I dont want to boot from the IDE drive. So I installed again and this time I chose for it to install grub on the /dev/sda (which I believe to be my first SATA drive, correct me if Im wrong). But the I could boot from any of my disks, not even WinXP. When It would load during boot GRUB my screen was filled with GRUBS and it never stops.

So I did a fixboot and fixmbr to the windows drive and windows is working again. But not my Kubuntu install. 


How can I place grub on any of my WinXP SATA drive (I think my bios wont let me boot from the other SATA drive, as I can just choose "SCSI" from the boot options and not "SCSI1" or "SCSI2" or "SATA1", or ...whatever, just "SCSI") and get it to work properly?

WHats your advice on where to place GRUB? DO you think I should place it on which drive?

Thanks a lot!

Rafael

---

### Post by darth_vector on 2005-12-23
if it works on the ide drive i dont see why you wouldnt put it there. it will incurr a performance difference only for the period that you are loading the first two stages of GRUB. since this takes half a second or less its hardly worth worrying about.

---

### Post by rafaelperrone on 2005-12-23
I dont want to put it in my IDE drive because I have only MP3 there and I eventually might want to take it to some friends computer to copy some more MP3 or so. Then my computer wouldnt boot if I took it out.

---

### Post by rcerreto on 2005-12-23
I'm doing a lot of guessing here.
I think that grub can't find menu.lst

Look at /boot/grup/device.map

I expect it looks:

(hd0)  /dev/hda
(hd1)  /dev/sda
(hd2)  /dev/sdb

Then check /boot/grub/menu.lst to verify that menu entries refer to the hd related to /dev/sdb (supposedly hd2)

now run:
sudo grub-install /dev/sda
this should install grub into the first SATA disk

Don't know how confortable you are with this stuff, if it sounds obscure try posting:
/boot/grub/menu.lst
/boot/grub/device.map
/etc/fstab
and I'll give a look.

---

### Post by whshao on 2005-12-23
Use the famous "bootpart" method! It requires you to download and install a simple text command utility under Windows called "bootpart". I have made it work for Ubuntu, Mepis, and Debian with Windows. My setup is similar to yours:

1. 80GB Windows XP as primary master (/dev/hda)
2. 160GB Ubuntu as primary slave (/dev/hdb)

I don't know how you connected the third data drive, but it could be connected as the secondary slave (/dev/hdd) to your CD-ROM drive, the secondary master (/dev/hdc). So you need to set the jumper settings and all.

Then I followed this approach and it works flawlessly:

[http://www.aboutdebian.com/dualboot.htm](http://www.aboutdebian.com/dualboot.htm)

It only seems long, but the procedure is actually not that complicated. Basically, it says uses the Windows bootlader to select the OS. If you select Kubuntu from this text boot menu, you will be redirected to the GRUB menu. While I think you should read the whole page, the most important point are:

(1) While in Windows, make a backup copy of c:\boot.ini.
(2) When you are setting up your partitions, make sure the bootable flag is OFF for all Linux paritions. The only bootable parition should be on your Windows drive.
(3) Install the GRUB on the first partition (/) of the second drive. So at the Kubuntu GRUB installer, manually enter /dev/hdb1. The "1" is important.
(4) Restart the computer and it will boot into Windows automatically. This is when you can edit the Windows bootloader entries. Use the bootpart described in the webpage above and select the partition matching /dev/hdb1. Mine is 2, so my command line looks like this:

c:\bootpart\bootpart 2 bootsect.lnx Kubuntu Linux

(5) Restart the computer again. This time you will see the Windows text boot menu. Select Kubuntu, and the GRUB should show up.

I believe this is the best dual boot method because it keeps the windows and linux systems separate: GRUB on hdb and windows bootloader on hda. I also recommend that Your format your data drive using the file system FAT32 and mount it as /sharedrv during the manual partitioning stage. That way both Windows and Linux and read and write to it.

---

