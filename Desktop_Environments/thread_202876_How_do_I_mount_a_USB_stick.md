---
title: "How do I mount a USB stick?"
date: 2006-06-24
forum: Desktop Environments
---

### Post by chris_andrew on 2006-06-24
Hi,

I have a 128Mb USB stick that I would like to use, but am not sure how to go about it.  Does anybody know what I need to put in my */etc/fstab*, or any other measures I need to take?

Many thanks,

Chris.

---

### Post by crroush on 2006-06-24
What version of ubuntu are you using? Did you simply try to plug it in and it failed?

---

### Post by Dr. Nick on 2006-06-24
Most of the time messing with fstab isnt needed, it just works. If it fails the plug it in and post your fstab here along with a few details about the usb stuck (like number of partitions and file system)

---

### Post by chris_andrew on 2006-06-24
Hi,

I'm running Dapper.

My fstab looks something a little like this:

 <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext2    defaults        0       2
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       /tmp            ext3    defaults        0       2
/dev/hda3       /usr            ext3    defaults        0       2
/dev/hdc2       /var            ext3    defaults        0       2
/dev/hda7       none            swap    sw              0       0
/dev/hdc1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

Maybe i'm mising a USB related package?

Cheers,

Chris.

---

### Post by Tuxman on 2006-06-24
Doesn't it work when you just plug it in? I think it did work with me when I tried with a Live CD.

---

### Post by chris_andrew on 2006-06-24
Tuxman,

Thanks for your reply.  Not wanting to sound funny, but if it "just worked", I wouldn't be posting this question.

I should mention that the USB stick has never been used before, so I have no idea what filesystem it may have.

Many thanks,

Chris.

---

### Post by Tuxman on 2006-06-24
[QUOTE=chris_andrew]Tuxman,

Thanks for your reply.  Not wanting to sound funny, but if it "just worked", I wouldn't be posting this question.

I should mention that the USB stick has never been used before, so I have no idea what filesystem it may have.

Many thanks,

Chris.[/QUOTE]
Sorry, I just meant that it "just worked" on my PC. I should possibly say that instead.

Anyway, I found a thread about this problem on google, posted on this forum.
This is for Warty Warthog 4.10, but possible it will work for you to. 
[http://www.ubuntuforums.org/archive/index.php/t-5184.html](http://www.ubuntuforums.org/archive/index.php/t-5184.html)

---

### Post by chris_andrew on 2006-06-24
Tuxman,

Thanks for that.  I'll take a look at the thread, and post anything useful, back here.

Thanks for taking the time.

Chris.

---

### Post by Dr. Nick on 2006-06-24
I thought they had alot of the usb bugs smashed, but ive seen a few us questons lately so who knows.

Since the stick has never been used before I would look for other computers/ operating systems to test it out on. That would help determine if the stick is defective or anything like that. 

Also do you have any other usb devices to try, like a usb mouse or keyboard? IT may be that your USB controller isnt supported thus no usb device would work,

---

### Post by ifokkema on 2006-06-24
Also, I think you need to be in the plugdev group to be able to mount USB devices automatically.

---

### Post by chris_andrew on 2006-06-25
Thanks for that.  I'm going to take it to work tomorrow, to try on a Windoze laptop.

Cheers,

Chris.

---

### Post by rcatman on 2006-06-30
i run an old laptop so I dont have the opportunity to run Gnome because of speed and memory constraints. I COULD but it would be very slow. 

My experience with Xubuntu on my computer yields no automatic mounting when I plug in a usb stick.  What i do I will explain below....

I plug in my usb stick then look, using fdisk, to see where it is 'connected'. (im not super savvy). its usually /dev/sdb# where # is a number of course e.g. /dev/sdb1   
 note: could be sbd but im not sure

so i type "sudo fdisk -l" and it prints out a listing of hard disk partitions and then /dev/sdb1

I create a directory in /media named usbstick

then i mount it by typing      mount /dev/sdb1 /media/usbstick

typing in "ls /media/usbstick" then shows all the files! voila!

maybe its archaic but my experience with ubuntu has been in a limited fashion. I had to install the server part of ubuntu then manually install the rest. So my ways aren't the easiest but I've had to find them out myself.

Anyway, that should probably work for any computer!

---

### Post by chris_andrew on 2006-06-30
Wow, that worked.  

Cheers, big fella.

Chris.

---

### Post by cbudden on 2006-06-30
I also have a similar problem.  I have a Creative Zen and when I use it in disk mode and over 4GB it does not mount automatically, but does manually.  If I lower the space to 2GB it does mount automatically.  It did used to mount at 8GB half way though breezy but stopped.  I also own a 256 mb usb key which automounts fine. What size is your usb drive your trying to mount Chris?

---

### Post by chris_andrew on 2006-06-30
Mine is only 128 megs.  What version of Ubuntu are you using?  Usually when only a certain amount of memory is recognised, it is a difference between kernels, but I could be wrong..........

Anybody? 

Cheers,

Chris.

---

### Post by ifokkema on 2006-07-01
[QUOTE=rcatman]I plug in my usb stick then look, using fdisk, to see where it is 'connected'. (im not super savvy). its usually /dev/sdb# where # is a number of course e.g. /dev/sdb1   
 note: could be sbd but im not sure

so i type "sudo fdisk -l" and it prints out a listing of hard disk partitions and then /dev/sdb1

I create a directory in /media named usbstick

then i mount it by typing      mount /dev/sdb1 /media/usbstick

typing in "ls /media/usbstick" then shows all the files! voila!

maybe its archaic but my experience with ubuntu has been in a limited fashion.[/QUOTE]
This is the 'common' way we had to do things in the past. A few notes:
[QUOTE=rcatman]I plug in my usb stick then look, using fdisk, to see where it is 'connected'. (im not super savvy).[/QUOTE]
A somewhat faster way is typing
```
dmesg |tail
```
This shows you the last 10 lines of your system messages, where it will also say what device your USB drive got appointed to. This can be sda, sdb, etc.
If you want, you can then run
```
sudo fdisk -l /dev/sda
```
or sdb, etc, to check out the partition number you need. This is usually 1, but my experience with some drives that windows users have, it can also be 4.

[QUOTE=rcatman]I create a directory in /media named usbstick

then i mount it by typing      mount /dev/sdb1 /media/usbstick[/QUOTE]
If you use the usb stick a lot, it's faster to create an entry in the /etc/fstab file. Next time you connect the stick, all you have to do is
```
mount /media/usbstick
```
and you're done.

---

### Post by ifokkema on 2006-07-01
[QUOTE=cbudden]I also have a similar problem.  I have a Creative Zen and when I use it in disk mode and over 4GB it does not mount automatically, but does manually.  If I lower the space to 2GB it does mount automatically.  It did used to mount at 8GB half way though breezy but stopped.  I also own a 256 mb usb key which automounts fine. What size is your usb drive your trying to mount Chris?[/QUOTE]
I use an external HD through USB which has two partitions - a EXT3 (some 80 Gb) and an FAT32 (some 70 Gb). Both partitions auto mount without a problem.

[QUOTE=cbudden]I have a Creative Zen and when I use it in disk mode and over 4GB it does not mount automatically, but does manually.  If I lower the space to 2GB it does mount automatically.[/QUOTE]
I'm not familiar with the Creative Zen. What do you mean by "lower the space to 2GB"?

[QUOTE=cbudden]It did used to mount at 8GB half way though breezy but stopped.[/QUOTE]
"Half way" as in mounts half way, or it has suddenly stopped working half way in the time you used Breezy?

---

### Post by Don_DiZzLe on 2006-07-01
How do I format a USB stick to a FAT or FAT32 partition like in windows?

---

### Post by ifokkema on 2006-07-01
[QUOTE=Don_DiZzLe]How do I format a USB stick to a FAT or FAT32 partition like in windows?[/QUOTE]
By using fdisk to create a FAT32 partition, then using mkfs.vfat to format it.
If you don't know these commands, see
```
man fdisk
man mkfs.vfat
```

---

