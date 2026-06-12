---
title: "SD/MMC card reader doesn't work on my Inspiron 1525n"
date: 2009-03-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Unikraken on 2009-03-09
I have a Dell Inspiron 1525n that I have installed the "Dell OS Factory Recovery 8.10 DVD ISO" from here: 

[http://linux.dell.com/wiki/index.php/Ubuntu_8.10](http://linux.dell.com/wiki/index.php/Ubuntu_8.10)

I don't know if the SD/MMC card reader worked prior to this with the actual OS that came preinstalled on it, I tried to dual boot with Windows XP and ended up deleting the partition because the XP disc wasn't recognizing the hard drive. Thus I had to install the recovery disk from the dell wiki above. I know it was stupid but I think I've learned my lesson from that now.

The SD/MMC - MS/Pro card reader won't recognize any of my sd cards, whether they be a fairly old 32 Mb card, a newer 128 Mb card, or my newest 1 Gb micro card in an adapter. So it's not the card. The list of known issues doesn't list any problems with the SD card reader that I could find. I could really use some help! Thanks for reading my plight!

I did the command lspci and got this below:
> 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
**[COLOR="Red"]02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)[/COLOR]**
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


Which suggests that my computer sees the card reader. Why on earth would it see the card reader but not detect when I put in a card? Is there a way I can manually mount the cards?

---

### Post by Nxion on 2009-03-09
I have a XPS m1210 with the same card reader on it. For me it worked out of the box. When I would insert a card it would take about 5 to 7 seconds to regonize. What you could do is open a terminal and type dmesg then insert a card in the slot and then type it again. Did you see a change in the end of the out put? It could be a case that for some reason the dell recovery cd doesnt setup automount. Have you tried a USB flash drive?

---

### Post by Unikraken on 2009-03-09
> **Nxion said:**
> I have a XPS m1210 with the same card reader on it. For me it worked out of the box. When I would insert a card it would take about 5 to 7 seconds to regonize. What you could do is open a terminal and type dmesg then insert a card in the slot and then type it again. Did you see a change in the end of the out put? It could be a case that for some reason the dell recovery cd doesnt setup automount. Have you tried a USB flash drive?

Hey thanks for replying! I didn't see any changes in the output. USB drives work just fine. The only thing that doesn't work is the SD card slot.

---

### Post by Unikraken on 2009-03-09
Ok, Well for some reason my card reader just started working again. For those poor souls who might come across this thread looking for a similar issue, when you push the card in, keep it pushed in for just a second before you let it catch. That's the only thing I did and now the cards are recognized just fine. I'm perplexed!

---

### Post by Yonaka on 2009-03-27
I have an Inspiron 1420. Not the 1420n. I am running 8.10, and my SD/MMC reader will not work properly. Using dmesg, it displays that the SD card is inserted. It also gives the disk capacity. Is there a way I can get it to mount? It doesn't seem to want to work with anything I try. In the gnome partitioner, it does not show either. Any help is greatly appreciated.

Thanks,
Yonaka

---

### Post by paulchinnz on 2009-04-26
I've got an e1405 and was hoping Jaunty/9.04 would solve the problem, but it didn't for me.

---

### Post by CPUNeck on 2009-05-03
Well I have an HP Pavilion tx2635us w/9.04(64) with no SD card function.  I noticed some times I have a USB drive under my computer even though nothing is connected. If that drive is present in my computer, my SD card WORKS! So here is the work around for me.

If my SD card doesn't work, first connect a USB jump drive, let it mount, dis mount it, remove it, then insert the SD card... Wha La, works for me so far every time. Now if only the d&*% reader would lock my SD card in so I didn't have to hold it :-(

---

### Post by gigs94 on 2009-05-06
I have the same sd/mmc reader and it doesn't seem to work with xD cards, just with SD cards... I was wondering if that was the problem everyone else was having.

---

### Post by paulchinnz on 2009-05-06
It's the MS Pro Duo card for me that doesn't work, haven't tried other cards.

---

### Post by paulchinnz on 2009-10-31
Unfortunately no better with 9.10 (although lots of other things much better!).

---

### Post by nishant.singh28 on 2009-11-04
Same on my studio 1555.....the damn thing won't even detect my cam's MS Pro Duo. Thought 9.10 would be better in this regard.

---

### Post by maxky on 2009-11-23
I have the same Problem (Inspiron 1525, Ubuntu 9.10.
CPUNeck's workaround works for me too. When I plug in an USB drive,
the SD drive works without problems.

---

### Post by oneindelijk on 2010-08-29
In Lucid Lynx they work out of the box for my old hp nx8220, but not for a new Hp DV4-2165dx, although they are seen as
```
lspci | grep SD                                   [8]
03:00.2 SD Host controller: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)
```
But dmesq | tail yields no results upon inserting the card...
Just sharing the info :-)

---

