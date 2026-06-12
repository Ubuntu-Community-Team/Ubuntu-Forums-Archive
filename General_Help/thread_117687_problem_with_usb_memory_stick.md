---
title: "problem with usb memory stick"
date: 2006-01-15
forum: General Help
---

### Post by NoNo_231 on 2006-01-15
Hello!

I have a tanscend memory stick 256MB compatible with linux. Well it played with live cd, palyed after installing ubuntu 5.10, but 2 days ago stopped.  I think that was the day that update manager downloaded something. It is really dead. It doesn't even read it. When plugging it, it does simply nothing.

I tried all the usb ports  (with the printer) and they work fine. Then tried the stick on windows and it works fine.

Can this be fixed? Does anybody know how to?

Thanks.

---

### Post by mcmillan on 2006-01-15
Did you try mounting the memory stick manually?

You can do this with the commands sudo mkdir /mnt/usb 
and then
 sudo mount /dev/sda1 /mnt/usb
If this works then there is a problem with automounting, otherwise it's a a problem with the stick itself I'd say.

---

### Post by MJSOnline on 2006-01-15
A problem with "auto mouting"?  How do you fix it?

Matthew

---

### Post by NoNo_231 on 2006-01-15
Yes I did. But the problem is that there is no sda, as far I understand. The reply to the mount command was "mount: you must specify the filesystem type".

---

### Post by mcmillan on 2006-01-15
I couldn't remember if you needed to specify that for usb drives or not, sorry try 
sudo mount /dev/usb/ /mnt/usb vfat
It might be a different file system if you've done something like format it to be ext3, but my usb drive seemed to work as vfat

If it is just a problem automounting I'm not sure how exactly to fix it, other than say to add an entry to fstab so you can mount manually easier. For instance my fstab entry is 
/dev/sda1       /media/usbdrive vfat    user,noauto     0       0

This lets me mount it with just mount /dev/sda1 . I also added a launcher to my panel so I can just click on that to mount it.

---

### Post by NoNo_231 on 2006-01-15
Nothing again. The problem is that it does not see the device. There was no usb dir. When I plugged in the printer the usb dir autocreated with lp0 inside.
I have also installed the usb viewer, where when I plug in a device it recognises it, but when I plug in the flash disk itt does nothing. 
The system is FAT.

---

### Post by mcmillan on 2006-01-15
The fact that it's not recognizing the device with the usb viewer is a bit disconcerting, since then presumably the computer is not recognizing the drive at all.  I'm a bit stuck for ideas on how to proceed though.

---

### Post by NoNo_231 on 2006-01-15
It seems to me like windows 98, which doesn't have the driver. 

However, as far as I remember, when I installed Windows XP Pro in this computer they didn't recognise it, and I installed the U-storage. But in Ubuntu it worked.  Until yesterday. I don't know what happens.

---

### Post by NoNo_231 on 2006-01-16
Hello! Does anybody have an idea? 

I have thu ubuntu installed at list one month and the only problem I had is that once it couldn't mount the drive, but it recognise it. It was at he early start and I did have problem to reinstall it.
But now this is something different. It does not recognise it. The only wired thing I remember to have done that day was that I tried to install eagle USB modem and doing some update.

Any ideas?

---

### Post by NoNo_231 on 2006-01-16
Well finally I solved the problem. :D :D :D 

It was a BIOS problem. I turned off the USB2.0 support from BIOS and Linux recognised it. The answer was found at the FAQ at [http://www.linux-usb.org/](http://www.linux-usb.org/).
I was trying 3 days. Finally I am thinking of believing that Friday and 13 isn't a good day.

Thank you. I hope I help if anybody has the same problem.

---

### Post by piq on 2006-01-17
I had the same problem. My USB memory stick worked yesterday, but today my computer couldn't find it. I used it on a mac yesterday and changed the name on it and I guess that was the problem. So I went to format it at in windows at my neighbour's pc and now it's working!:D

---

### Post by NoNo_231 on 2006-09-03
After many months problem solved 100% percent. After some of the last updates, don't know which exactly, I tried again usb 2.0 support from my BIOS and the USB worked. Reallly happy because I can use the LG DVDRW which I used only with my laptop. I tend to believe was with the Linux kernel and some incompatibility with BIOS, something that was fixed.

---

