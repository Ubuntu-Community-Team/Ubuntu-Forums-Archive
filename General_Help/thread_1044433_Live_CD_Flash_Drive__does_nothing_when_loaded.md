---
title: "Live CD Flash Drive  does nothing when loaded"
date: 2009-01-19
forum: General Help
---

### Post by AndyP79 on 2009-01-19
Hi All,
 Okay, So I am trying to load the CD on to an 8GB THumb Drive. This time it all went on there, so I resrtarted the computer. Nothing. It won't load the stuff on there. This time it told me that there was nothing on the Pen Drive. There was. 
So does anyone have any advice on this?
Thanks

---

### Post by zwygart on 2009-01-19
Have you installed a bootloader?
Is your computer able to boot a thumb drive?
I suggest you to install GRUB. Then configure it to load the kernel and initrd. 
Is your thumb drive correctly partitioned?

---

### Post by AndyP79 on 2009-01-19
In the latest edition of LXF it says nothing about bootloaders and GRUB. I am trying to use the MAKE A USB application that comes default in the menu with 8.10
I have seen nothing about the other stuff you were talking about, so I am not even sure where or how to do all that.

---

### Post by snowpine on 2009-01-19
Does your computer have the capability to boot from USB? You need to enter your computer's bios options (F2, F10, F12, etc. depending on the manufacturer) and change the boot order so the USB device is first priority.

I personally have had excellent luck using a utility called Unetbootin to create bootable USB drives. Good luck!

---

### Post by zwygart on 2009-01-19
OK, you tell me about a automatic installation. I will tell you the manual installation.

First you have to format the key in valid partitions. I had bought a key where the partition where not real. To do this you go in System>Administation>Partition editor. Delete the partition and create new ones (fat32).
Mount your drive and your iso. Then copy all the iso to your drive
```
sudo mkdir /media/USB
sudo mount /dev/sdb? /media/USB
mkdir /media/ISO
sudo mount -loop YourISO /media/ISO
sudo cp -r /media/ISO/* /media/USB/
```

Now to install GRUB, you have to copy grubfiles then run the install commands
```
mkdir /grub
sudo cp -r /boot/grub/* /media/USB/grub/
grub
grub>find /grub/menu.lst
#Note the letters outputted (hdX,Y)
grub>setup (hdX)
```
Be carefull to not take the grub from your computer
After that you edit your menu.lst
```
sudo gedit /media/USB/grub/menu.lst
```
append this entry
```
root (hd0,Y)
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper
initrd /casper/initrd.gz quiet splash --
```
by replacing the letters X,Y with the ones you saw before.

Now your USB drive is bootable.
Reboot your computer and during the boot press the key to choose the boot option. By pressing some off ESC, TAB, F?, DEL, (Dependig on the manufacturer).

If you have troubles post again. It may help if you post fdisk -l with your drive plugged in.

---

### Post by AndyP79 on 2009-01-19
Hi All,
 Okay, So I installed and used the UnetBootin, Great program, plug and play. I downloaded a clean ISO from the Ubuntu website, and used it. Everything went well, except...
 I tried to do the updates to the USB Ubuntu, after quite some time of sitting through 239 updates, it told me that the was not enough space. I am using an 8GB flash drive. So I restarted and went to my actuall computer, and checked the flash drive properties, and it says that I have 6.8GB free. 
Other then that it seems to look fine........

---

### Post by AndyP79 on 2009-01-19
Allright....I found the other thing, I does not save my changes I made......

---

### Post by snowpine on 2009-01-20
Unetbootin does not create a "persistent" USB install. It is like a Live CD; you will lose any updates or changes each time you reboot.

---

