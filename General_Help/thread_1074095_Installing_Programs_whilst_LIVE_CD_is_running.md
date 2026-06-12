---
title: "Installing Programs whilst LIVE CD is running"
date: 2009-02-18
forum: General Help
---

### Post by Greg Xix on 2009-02-18
I have run the Live CD and Knoppix from my USB Flash disk and while I was using those I installed WINE and ran/installed a few programs for it.

My question is, where do the "installed" programs(Wine, the game I downloaded) reside while they are installed? Are they on the hard drive temporarily? 

Obviously they are gone when I reboot the Live CD and must be done again which is fine, but where is their "temporary" storage place?

---

### Post by grndslm on 2009-02-18
I'm just curious... why are you so curious?

I'd assume it uses RAM, but it could be empty hard drive space.  Would be interesting to know exactly what happens during the LiveCD.

---

### Post by grndslm on 2009-02-23
Now I'm curious about this myself.

When running a LiveDVD I created with remastersys, I notice it says I have some swap space available.  Does it just automatically use a swap partition on the computer?  What if it's a Windows install, with no swap partition?  Does it use empty NTFS space (not very likely)?  ... or does it turn some of the RAM into swap (no point)?

---

### Post by grndslm on 2009-02-24
Soo... I asked around on #ubuntu and got the answer!

The LiveCD will use swap space if it's available on the hard drive, but if it's a HD with windows only... there's no swap space for the CD.  Figures.

---

### Post by 3rdalbum on 2009-02-24
They go into RAM. If you've got a Linux swap partition on a hard disk already, Ubuntu will start using it (I think?). So, I guess if you don't have much RAM, in a way the applications will be in your swap partition.  Ubuntu will not start storing its own files on hard disks, even if they are ext3 formatted.

---

### Post by ashwinhgtx on 2009-02-24
You can do a persistent install on your flash drive. Then all the new programs you install will be saved on your flash drive. You can also save documents, music etc. on your pendrive. Check this out
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

It will be like a normal Ubuntu install and not like a live CD.

---

### Post by grndslm on 2009-02-24
You know what's even cooler than usb persistence is using Remastersys to create your own custom LiveDVD with different packages, themes, & configurations.  Then you can hand out free LiveDVDs to your friends, just like Mark Shuttleworth! ;)  But your friends will think you're cooler than Mr. Shuttleworth, because they don't know him.  :D

And once you're finished... you can use usb-creator to get flash drive persistence.  I love Linux!

---

### Post by Greg Xix on 2009-02-28
> **ashwinhgtx said:**
> You can do a persistent install on your flash drive. Then all the new programs you install will be saved on your flash drive. You can also save documents, music etc. on your pendrive. Check this out
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

It will be like a normal Ubuntu install and not like a live CD.



Yeah, that site is where I got setup with Knoppix on my USB Flash drive(Live USB), which prompted my original question.

It DOES NOT save things on the Flash disk by default(although I think that option is available) as everything is gone when I reboot/reload the USB-Knoppix, but I was wondering if in fact it is saving files, downloads, etc. elsewhere on my hard drive because I do have Ubuntu installed on my HD. Or if in fact it would do this with an Ubuntu Live CD.

Actually, I dont want any files, changes, etc. to be saved at all anywhere, which is why I asked. I have my reasons for not wanting anything saved.

---

