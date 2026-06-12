---
title: "Broadcom wifi drivers"
date: 2009-01-25
forum: General Help
---

### Post by danuk88 on 2009-01-25
I am using ubuntu 8.10

my wi-fi is working ok with the WL driver, but I want to be able to use packet injection.

I have downloaded the two files I need, and have tried to install the drivers with the following commands, but the B43 drivers are still not working.

tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo ../../b43-fwcutter-011/b43-fwcutter -w /lib/firmware wl_apsta_mimo.o

I have also blacklisted the WL driver to stop it loading.

Anyone know how I can get the B43 driver to install?

cheers

dan

---

### Post by Sam Lars on 2009-01-25
Is the b43 driver loading?  You can add it to /etc/modules to make sure it will.

---

### Post by danuk88 on 2009-01-26
No the B43 driver is not loading. also it is not listed when I type lsmod. how do I add it to /etc/modules to get it to load?

Thank you

Dan

---

### Post by Sam Lars on 2009-01-26
Just open that file with
```
sudo gedit /etc/modules
```
and add
```
b43
```
to the bottom and save it, and then when you boot it should always load.

---

### Post by danuk88 on 2009-01-26
I have now added b43 to the bottom of /etc/modules when I reboot and run lsmod I now have b43 in the list but I still have no wifi

Any ideas?

Cheers

Dan

---

### Post by kevdog on 2009-01-26
You didnt say anthing about your chipset. b43 is only for some chipsets whereas the STA (or wl driver) is for other broadcom chipsets.  What was wrong with the STA driver anyway?

---

### Post by krzysz00 on 2009-01-26
Have you installed the Broadcom firmware in the right place?

If this is all a hassle, try ndiswrapper.

---

### Post by Sam Lars on 2009-01-26
> What was wrong with the STA driver anyway?
He said he wants to use packet injection.

What chipset do you have?  Could you post the output of lspci so we can make sure you are getting the right driver?

---

### Post by Ayuthia on 2009-01-26
> **Sam Lars said:**
> He said he wants to use packet injection.

What chipset do you have?  Could you post the output of lspci so we can make sure you are getting the right driver?

Can you make that lspci -nn?  Some 4312 cards will not work with the b43 module (14e4:4315).

---

### Post by danuk88 on 2009-01-26
when I run lspci -nn I get,

00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
00:1f.5 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:292d] (rev 03)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

Cheers

Dan

---

### Post by Ayuthia on 2009-01-26
> **danuk88 said:**
> 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

This is the chipset that does not work with the b43 module at this time.  Unfortunately, you cannot use the wl module or ndiswrapper for packet injection.  Sorry.

---

### Post by danuk88 on 2009-01-27
That’s ok if it wont work, It works on my girlfriends lap top, was just trying to get it to work on mine so I didn’t have to keep switching laptops, ha ha

Thanks to every one who helped

Cheers

Dan

---

