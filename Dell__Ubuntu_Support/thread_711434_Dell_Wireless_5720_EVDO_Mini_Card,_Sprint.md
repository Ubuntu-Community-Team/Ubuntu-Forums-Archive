---
title: "Dell Wireless 5720 EVDO Mini Card, Sprint"
date: 2008-02-29
forum: Dell  Ubuntu Support
---

### Post by knx2 on 2008-02-29
I have tried to get the internal sprint card to work in this laptop but cannot find any information on how to do it.  I read another thread on here that someone was trying to get one to work but he said he had to hack up option.c in the kernel.

I believe the kernel that i am running supports the card i am running.

I am running Linux Zeus 2.6.24-10-generic #1 SMP Fri Feb 22 19:08:18 UTC 2008 i686 GNU/Linux

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

lsusb does not print anything out.


Found out my Vendor is 0x413c and the Product is 0x8134

---

### Post by barichardson5727 on 2008-03-02
I have a dell laptop with an evdo adapter that is working after using these tutorials:

[http://www.totalnetsolutions.net/2007/08/22/evdo-on-debian-ubuntu/](http://www.totalnetsolutions.net/2007/08/22/evdo-on-debian-ubuntu/)

This will show you how to use kppp to use the gui to start your adapter:
[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)


Good Luck!

---

### Post by knx2 on 2008-03-07
Anyone have any ideas?  I still cannot get this to work

---

### Post by barichardson5727 on 2008-03-09
Have you ever used this adapter successfully under windows? You must activate the device under windows using the provided software before you can use the device in linux. You only have to activate the card once.

If you could post everything you have tried at this point, your config files or any further details about your errors that would be extremely helpful.

---

### Post by knx2 on 2008-03-14
Finally got this card to at least work... However, only with the usbserial driver and not the airprime which is supposed a lot faster.
When I load the airprime module nothing happens.  Do I have to load the airprime with anything else to get it to work?  Or is my card still too new for the airprime to be updated with my card info?

Linux Zeus 2.6.24-12-generic #1 SMP Sat Mar 8 02:29:24 UTC 2008 i686 GNU/Linux
is what I am running now... 
modprobe usbserial vendor=0x413c product=0x8134
Is what I use to get it online.

---

### Post by timcredible on 2008-03-14
i don't know about sprint, but i got my verizon wireless broadband card to work, maybe same info would apply to sprint cards - info on it [here.]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=19&Itemid=27")

---

### Post by knx2 on 2008-03-15
I do not have a problem connecting... Just the speed through usbserial is about half as fast as airprime.  For example.  I can grab files from kernel.org at 60kbps currently... On my old evdo card through airprime I was getting 200kbps... Same rev A cards... usbserial just has a cap on it.

---

### Post by barichardson5727 on 2008-03-17
I have been planning to try the airprime driver on my laptop just haven't had the time. Hopefully within the next few days I will get it done.

I know that it will require modifying the airprime module to accept the vender and device id of the 5720 card. I hope that is all though.

---

### Post by rocksocke on 2008-03-25
hi! many thanks for this post!

did anybody of you had success in using this chips GPS functions?
i read on novatel's site ( [http://www.evdoinfo.com/content/view/1944/64/](http://www.evdoinfo.com/content/view/1944/64/) ) it should support it?

thanks a lot.

---

### Post by knx2 on 2008-03-25
Let's work on getting it to work full speed first... usbserial will NOT run this card full speed.

---

