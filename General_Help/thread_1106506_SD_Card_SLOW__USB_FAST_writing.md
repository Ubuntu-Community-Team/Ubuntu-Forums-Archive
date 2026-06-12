---
title: "SD Card SLOW / USB FAST writing"
date: 2009-03-25
forum: General Help
---

### Post by w4llet on 2009-03-25
Hello guys

I am having a strange problem here and i cant solve it.

I have a mini sd card. I can use it on a usb adapter or a SD card adapter.

Problem is:

when I use any sd card on my sd card reader, write speed is very low. Something under 1.8m/s. 

If I remove it from SD card adapter and insert on the USB adapter and plug it in same SD card reader (my sd card bay can read several type of cards and have 1 usb port, a internal one, using same usb cabe directly on mainboard) write is pretty fast, something under 30mb/s.

I tried everything and problem is only when i try to write on sd cards in general. I tried mini sd with adapter, regular sd of several brands and speed. Every single one gives me slow writing speed. Only when i use USB adapter or pendrives write speed is very good. Reading is fast in any scenario.

I tried to manual mount sd card, didnt work.

I have checked how the mini sd card is automounting in mtab and in both cases (when using sd adapter or usb adapter) the options are the same:

/dev/sde1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

I have tried fstab too with several option gathered over a lot of forums on the internet. Nothing works.

When i manually mount creating a dir in /media or /mnt and trying some different options, best shot i had was a big ilusion. Files are almost instant writhed on sd card, but to be honest its a lie, because OS keeps writing in background at same low speed. Something like flushing data.

I dont know what I can do more about it, because any solution in beyond my knowledge.

I used sd card adapter over theses tests just to know that isnt a problem with the memory itself. Same memory, with two diferent adapters, at same cable on motherboard.

Sorry to write a lot.

English is not my main language, sorry for bad words.

Thanks.

---

### Post by w4llet on 2009-04-03
Ok guys.
I solved the problem.

Problem was low card internal reader quality.

Suppose to work as usb 2.0, as announced in product description. But, truth is only usb port was using usb 2.0. The cards slots was operating at usb 1.1.

After several unsuccessful tests in ubuntu, i went to windows vista and same slow writing problem was there. So, i figured wasnt a OS problem.

I bought a new internal card reader and now its writing at maximum card speed.

Just for you info: Bad internal reader was writing at 1.5k/s top. Good internal card reader: Over 10mb/s in same memory.

Thanks for all your effort to try to help me.

And dont forget: If u are sure u r using a internal reader at a 2.0 usb port, and its writing at low speed, blame the card reader and not ubuntu.

Cheerz!

:lolflag:

---

