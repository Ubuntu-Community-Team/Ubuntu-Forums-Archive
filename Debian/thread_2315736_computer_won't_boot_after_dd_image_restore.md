---
title: "computer won't boot after dd image restore"
date: 2016-03-02
forum: Debian
---

### Post by marty10 on 2016-03-02
[COLOR=#333333][FONT=Lucida Grande]Hello all ![/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I have a Debian Jessie 32 bits machine with standard partitions : one EFI, one for the root system and a swap.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I did a dd image backup of it hard drive thinking i would be easy to restore it or clone to another device... but it seems it is not that simple ![/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]My PC won't boot : no bootable drive found ![/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I did the same once with a 64 bit Debian Jessie which i fixed using an ubuntu live CD with boot-repair, but here with the 32 bits version it doesn't work : it keeps saying i have an EFI incompatible partition and i should use a 64 bits linux...[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Note : i boot-repair from a 64 bits ubuntu live cd. Should i use a 32 bits version ? Because i can"t make a 32 bits Debian live CD to boot, usb key won't show up in boot options (32 bits install CD works fine)[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I ha read some things and tried some others but nothing works[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Grub and EFI are really obscure for me...[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]How could i fix my debian 32 boot ?[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Or how can i properly clone my debian 32 on other PC ? am i missing something using dd ? should i use another tool ?[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Thanks a lot[/FONT][/COLOR]

---

### Post by buzzingrobot on 2016-03-02
You should post the exact dd command you used.

Also, did the PC fail to boot immediately after using dd, or after restoring it with that image? 

The most common cause of dd errors is incorrectly identifying a device name and overwriting a drive. There's no error checking.

---

### Post by marty10 on 2016-03-02
Hello,

I installed Debian Jessie 32 bits and it was booting ok.

I did a dd to make an image of the entire drive : 

dd if=/dev/mmcblk0 of=/media/usbdrive/backup.img

I then restore the image the other way around : 

dd  if=/media/usbdrive/backup.img of=/dev/mmcblk0 bs=4M

The PC won't start anymore. No grub. Just the message "no bootable device found"

I tried to restore grub from a live CD with chroot or with boot-repair but with no luck

---

### Post by arochester on 2016-03-02
mmcblk0 ...an sdhc card?  What are the basic specs of your computer?

From the RaspberryPi Forums "If you get only one partition when cloning the image to an sd card, make the block size smaller when executing the dd command. bs=32k works, but bs=1M or bigger does not. The other option is to not specify a block size and dd will use the default of 512. It will work but takes forever." - [https://www.raspberrypi.org/forums/viewtopic.php?f=91&t=46911](https://www.raspberrypi.org/forums/viewtopic.php?f=91&t=46911) 

...You have specified 4M...

---

### Post by marty10 on 2016-03-02
Hello,

Thanks for the link and tip ! i will check that !

I am using a micro computer with embedded eMMC : the Intel Compute Stick

thanks

---

### Post by buzzingrobot on 2016-03-02
> **marty10 said:**
> 
dd if=/dev/mmcblk0 of=/media/usbdrive/backup.img

I then restore the image the other way around : 

dd  if=/media/usbdrive/backup.img of=/dev/mmcblk0 bs=4M




In my use of it, dd will buffer data if it finds enough RAM to put it in and then return the prompt.  Unfortunately, most data are still buffered, not written to the target device. I follow dd with "sync", which flushes the buffers. I usually just tag it on the end of the line like so: "dd if=............... && sync".  Typically, it's the synching that takes the most time since that's when the actual transfer of data to the physical device occurs.


That may or may not be a factor here.

---

### Post by marty10 on 2016-03-02
i tried again to chroot like so :


sudo mount /dev/mmcblk0p2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt


then inside chroot : 
update-grub
(everything is ok here)


then :
grub-install
(error : /usr/lib/grub/i386-pc/modinfo.sh doesn't exist. Please specify --target or --directory)

Same problem at reboot : "no bootable device found"

Grub don't even show up, so maybe this has nothing to do with grub ?

---

### Post by marty10 on 2016-03-02
ok, everything went fine ! I used a reFind disc image : [https://wiki.debian.org/GrubEFIReinstall](https://wiki.debian.org/GrubEFIReinstall)
i was able to boot my partition and from here re-installed grub.
my PC is now booting again.


...i am kind of frustrated not understanding why Clonezilla didn't re-installed it and why i wasn't able to re-install it manually though...

---

