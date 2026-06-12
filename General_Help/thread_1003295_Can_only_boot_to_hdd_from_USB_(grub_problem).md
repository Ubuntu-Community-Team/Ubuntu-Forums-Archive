---
title: "Can only boot to hdd from USB (grub problem)"
date: 2008-12-05
forum: General Help
---

### Post by RedPandaFox on 2008-12-05
I just installed Ubuntueee on my 2gb eeepc 701 with an 8gb SD card except the USB istaller worked except I cant boot to the grub without having the usb plugged in, after it boots the grub I can disconect the USB but i get error 15 when its not pluged in and it trys to find the grub

Ii tried installing qgrubeditor but I dont know how to get it to work propaly to put the grub on something without the usb plugged in.

---

### Post by Herman on 2008-12-06
It sounds like the installer put the IPL (Initial Program Loader) for  your new operating system's GRUB in the MBR of your flash memory stick instead of in the EeePC's SSD MBR.

I have noticed something a little strange about my EeePC, (I have the 4GB 701), and it seems to count the USB drives before the SSD drive in the BIOS.

You should be able to boot Ubuntu and re-install GRUB to MBR in the SSD.
Boot with the USB plugged in and then unmount it and remove it.
Then open a terminal and type 'sudo grub'
```
sudo grub
``````
find /boot/grub/stage2
``````
root (hd0,0)
```Where: (hd0,0) was the answer you got from the previous command "find /boot/grub/stage2"
```
setup (hd0)
```
```
quit
```
Now you should be able to reboot and you shouldn't need the USB anymore, (I hope, - if I've guessed right about what numbers to use). :)

---

### Post by RedPandaFox on 2008-12-06
```
setup (hd0)
```


returns error 17 cannot find selected partition

Where should I be setting the grub to? I installed the OS to the SD card which is always in

---

### Post by Herman on 2008-12-06
:) oh.
What was the answer you got from the earlier command "find /boot/grub/stage2" then ?

---

### Post by RedPandaFox on 2008-12-06
> **Herman said:**
> :) oh.
What was the answer you got from the earlier command "find /boot/grub/stage2" then ?

hd2

I tried that and it went through saying it was installing the grub except when it was done i rebooted and it told me I had error 21. So I put the usb back on and it still needs the usb to boot

---

### Post by Herman on 2008-12-06
I'm just guessing that what could be happening is your BIOS is numbering the drives with the USB as first hard drive, so GRUB's IPL is installed to that.
Then you probably installed GRUB to the SSD's MBR alright, but now when you try to reboot without the USB plugged in, your menu.lst is wrong because it was set up with your Ubuntu drive as the third hard drive instead of the first one.

Try posting a copy of the bottom part of your /boot/grub/menu.lst file here please and the output from 'sudo fdisk -lu',
```
gksudo gedit /boot/grub/menu.lst
```
```
sudo fdisk -lu
```

I'm using plain Ubuntu Intrepid Ibex installed in my EeePC, I hope Ubuntueee is fairly similar to the standard Ubuntu as far as booting goes.
Is it Hardy Heron or Interpid Ibex?
Intrepid Ibex uses uuid numbers instead of the old (hdx,y) numbering and I think it's a lot better for what we're trying to do right now, but nevermind, we should still be able to fix it fairly easily anyway. :)

---

### Post by RedPandaFox on 2008-12-06
```
default 0
timeout 1
hiddenmenu

title Ubuntu 8.04.1, kernel 2.6.24-21-eeepc
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-21-eeepc root=UUID=dddea7c8-0d9e-48a6-b13a-0a105035adc0 ro quiet splash
initrd /boot/initrd.img-2.6.24-21-eeepc
quiet

title Ubuntu 8.04.1, kernel 2.6.24-21-eeepc (recovery mode)
root (hd2,0)
kernel /boot/vmlinuz-2.6.24-21-eeepc root=UUID=dddea7c8-0d9e-48a6-b13a-0a105035adc0 ro single
initrd /boot/initrd.img-2.6.24-21-eeepc

title Ubuntu 8.04.1, memtest86+
root (hd2,0)
kernel /boot/memtest86+.bin
quiet

```


```
Disk /dev/sda: 2000 MB, 2000388096 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907008 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf9dcf9dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     3903794     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 1030 MB, 1030750208 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2013184 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00064f02

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     2008124     1004031    6  FAT16

Disk /dev/sdc: 7969 MB, 7969177600 bytes
255 heads, 63 sectors/track, 968 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005ac2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    14795864     7397901   83  Linux
/dev/sdc2        14795865    15550919      377527+   5  Extended
/dev/sdc5        14795928    15550919      377496   82  Linux swap / Solaris

``` 


and ubuntu eee is based on 8.04 but it asked me to do a dist upgrade so i dont know

---

### Post by Herman on 2008-12-06
Try booting with the USB drive and 
```
sudo grub
``````
root (hd2,0)
``````
setup (hd2,0)
``````
setup (hd2)
``````
setup (hd0)
```It should be (hd0) where you should be installing GRUB to.
You should really only need to use 'root hd2,0)', which means it will be the stage1 (IPL) for /dev/sdc1 's GRUB that you will be installing somewhere.
'setup (hd0)'  should install that IPL to the first hard disk's MBR (or SSD's MBR), where the BIOS will normally look to boot from, unless otherwise told.

When you reboot do you see a GRUB menu? 
Is there any way for you to get [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")?

Also, is it important for you to have your 2.0 GB internal SSD formatted with a swap area?
I'm just thinking maybe if it's not important you might like to create a 'Dedicated GRUB Partition' there maybe, [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").
If you still have trouble, you should be able to chainload any other disk from that, or at least get GRUB's Command Line Interface, which is very useful for booting with and/or troubleshooting at times like this.

---

### Post by RedPandaFox on 2008-12-06
Still didnt help, booting to either the ssd or the sd card returns grub error 21

---

### Post by Herman on 2008-12-06
Sorry, I was still thinking and editing my previous post while you were already working on what I first posted.

Is it important for you to have your 2.0 GB internal SSD formatted with a swap area?
I'm just thinking maybe if it's not important you might like to create a 'Dedicated GRUB Partition' there maybe, [How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_").
If you still have trouble, you should be able to chainload any other disk from that, or at least get GRUB's Command Line Interface, which is very useful for booting with and/or troubleshooting at times like this.

---

### Post by RedPandaFox on 2008-12-06
Ok, I had it s swap to try and make up for the limited RAM and seeing as I wasnt going to be using the internal storage from the SSD I let it automatically install which made it swap for me.

Alhow I have been using Ubuntu for a while I still am kind of a beginner and I need a basic level how to in everything I do :P

But its good to see someone is trying to help me, especially a fellow Aussie

---

### Post by Herman on 2008-12-06
Yeah, no worries, I wish the first thing could have worked though, but you know the old saying 'life wasn't meant to be easy". :)

Do you get any GRUB menu at all, (like this - [Grub Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#gui"))?

If you do, can you press your 'c' key to change into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") , because if you can, we might be able to try some tricks to see what GRUB is doing.
(Press 'Esc' to exit and go back to your GRUB menu if you like).

We already saw what Linux thinks your computer's drives look like with the outputs you posted earlier, and normally, but not always, the GRUB numbering is equivalent to the Linux numbering.

---

### Post by Herman on 2008-12-22
I just bought a new SD card for my Eee PC 4G and I'm very disappointed with the card. I don't know what the problem is, but my SD card is just about worse than useless. It's so slow to do anything, even just renaming a file or using the ls command to see if anything had been successfully copied into it makes my system freeze up. Copying files into it has been a real nightmare. 
If they're all anything like the one I bought, I wouldn't recommend SD cards to anyone. :icon_frown:

---

