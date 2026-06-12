---
title: "Grub error"
date: 2009-04-16
forum: General Help
---

### Post by never_retreat on 2009-04-16
GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 17

I'm new to this ubuntu thing and I have know idea what this means.
I did some searching around and everything I read has something to do with dual booting. I'm not dual booting, no fancy stuff. This is a plain jane install. 
This problem started after downloading updates and wanting to reboot.
Any ideas? Spelled out in small easy to read words. LOL

---

### Post by codeseer on 2009-04-16
That means that it can't mount the partition you selected for some reason. You only have Linux installed? How many drives?

---

### Post by never_retreat on 2009-04-16
1 HD, 1 CD, 1 Flop

---

### Post by codeseer on 2009-04-16
You should be able to put the Ubuntu CD in and boot from that, choosing the Live CD option. That should take you to the desktop where you can click Places and then the drive and mount it up. Then look at /boot/grub/device.map using the text editor (gedit). Post the contents of that here.

---

### Post by never_retreat on 2009-04-16
When I put in the cd my options are

start or install
start in safe graphics mode
install with driver update cd
oem install
check cd for defects
memory test
boot from first hard disk

I picked the first one.

If I go to the boot folder there is no grub folder in it. just a few files.

I think I'm looking at the cd not the actual disk. Is that possible? I don't see any of my other stuff either

---

### Post by codeseer on 2009-04-16
Yeah, you're looking in the boot folder of the CD. Click on the 'Places' menu at the top and pull that down to select your drive from the list; it will have a white icon. That should put a link to it on your desktop then and you want to look inside that drive for /boot/grub

---

### Post by never_retreat on 2009-04-16
When I pull down places there are no drives listed. 

home folder
desktop
documents
music
pictures
videos
computer
cd/creator
network
connect to server
search for files

If I choose computer I get 3 icons
floppy, cd drive and file system

If i click file system i get the same thing as before.

---

### Post by codeseer on 2009-04-16
When you open a terminal and type 'blkid'?

---

