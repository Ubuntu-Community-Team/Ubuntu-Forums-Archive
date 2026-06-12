---
title: "BIG grub issue"
date: 2009-05-24
forum: General Help
---

### Post by Mautobu on 2009-05-24
so, i'm new to linux, and have ubuntu 8.10 i think. i wanted to reinstall windows on one of my pc's, but the pc wouldn't boot. i found a tutorial that was fairly vague, but it said to change the menu.lst in /boot/grub by adding a line 

# timeout        15

before the linux partition. i then realized that i couldn't because i wasn't in root and didn't know how to change that. so i copied it to the desktop, and did

sudo rm /boot/grub/menu.lst

and then tried to move the modified menu.lst that was on the desktop to the grub folder, but did a major screwup.

cd /boot/grub/
mv menu.lst ~/ ./

my root folder is now inside of itself, and i have no menu.lst in the grub folder. i then attempted to install lilo bootloader over grub, restarted and (to no real surprise) discovered that the pc now has no master boot record.

help.

---

### Post by abyrne on 2009-05-24
use a ubuntu server, alternate, or minimal cd to re-install grub.

On a server CD:

 1. go to RESCUE A BROKEN SYSTEM 
 2. follow the prompts  
 3. hit INSTALL GRUB.

On a alternate or minimal CD:

 1. go to OTHER OPTIONS 
 2. hit RESCUE MODE
 3. follow steps 2-3 in the server cd instuctions

and reboot

Oh, and by the way, NEVER REMOVE (rm) YOUR MENU.LST!!!!!!

---

### Post by Mautobu on 2009-05-24
burnt the cd, put it in, and i get a message that reads:

no boot signature in partition

reboot select poper boot device or insert boot media in selected boot device press any key


i've already selected the dvd drive to boot first and it doesn't, which was the original problem and why i was removing grub in the first place.




edit:
mobo is asus m2n mx se
sempron processor
2 gigs ram
just fyi

---

### Post by trench.me on 2009-05-24
> **abyrne said:**
> use a ubuntu server, alternate, or minimal cd to re-install grub.

Oh, and by the way, NEVER REMOVE (rm) YOUR MENU.LST!!!!!!

Unless, of course, boot-fail and a forum thread like this is the desired result. 

**Mautobu** - [http://www.hp2133guide.com/forums/viewtopic.php?t=1345&sid=58eed479d9418166ed4dca5e95c96eb4](http://www.hp2133guide.com/forums/viewtopic.php?t=1345&sid=58eed479d9418166ed4dca5e95c96eb4)

---

### Post by Mautobu on 2009-05-24
yeah... about that, i rebooted to see if lilo would work, and now have no interface period, just the "no boot signature in partition" message.

tried to boot without the hdd plugged in, ie, just off the dvd, but no luck.

---

### Post by trench.me on 2009-05-24
Have you checked your BIOS to make sure it's set to read ROM's before hard disks? You might need to try booting from [a floppy]("http://www.linuxjournal.com/article/4622") or [usb]("http://nsaunders.wordpress.com/2006/11/06/a-usb-stick-grub-and-ubuntu/"). 

I'm finding some [interesting results from google]("http://www.google.com/search?q=no+boot+signature+in+partition") that you should probably check out too.

(... I'm pretty sure, from your description, the [MBR is fine]("http://www.dreamincode.net/forums/showtopic87489.htm").)

---

### Post by Mautobu on 2009-05-24
well, i'm pretty sure i'm screwed then, as i have no other linux box with which to make a disk or usb stick. is there a way of just putting the windows MBR on the partition, or another MBR over it without making a new linux partition on my main pc?

---

### Post by raymondh on 2009-05-24
> **Mautobu said:**
> well, i'm pretty sure i'm screwed then, as i have no other linux box with which to make a disk or usb stick. is there a way of just putting the windows MBR on the partition, or another MBR over it without making a new linux partition on my main pc?

will this help?

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Good luck,

---

### Post by Mautobu on 2009-05-25
can't boot from a cd, period, but thanks

---

### Post by trench.me on 2009-05-25
A DOS bootdisk might do the trick.

Take a look at this site and see if it helps at all: [http://www.bootdisk.com/](http://www.bootdisk.com/)

I had to recover using a Win 98 bootdisk a couple years ago on an XP/Ubuntu machine if memory serves.

---

### Post by Mautobu on 2009-05-31
is there somewhere that i can just get the menu.lst?

i could then run an ubuntu live cd then replace the file on the drive using my other pc.

---

### Post by VMC on 2009-05-31
> **Mautobu said:**
> well, i'm pretty sure i'm screwed then, as i have no other linux box with which to make a disk or usb stick. is there a way of just putting the windows MBR on the partition, or another MBR over it without making a new linux partition on my main pc?

Boot from floppy. From cli type ```
fdisk/mbr
```

---

### Post by arubislander on 2009-05-31
The menu.lst should still be in your home directory where you copied it to. If you have any means of getting the file back on your drive using another PC, then you might also be able to copy it back using the Live CD...

---

### Post by VMC on 2009-05-31
Here's how to use your floppy and SGD:
[http://www.supergrubdisk.org/index.php?pid=6](http://www.supergrubdisk.org/index.php?pid=6)

---

### Post by Mautobu on 2009-06-01
so, moved the menu.lst successfully, BUT same MBR issue as before, so, how the F do i get my root out of the grub folder?!

---

