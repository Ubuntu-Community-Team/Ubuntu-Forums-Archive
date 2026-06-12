---
title: "Does anyone have wireless working with Karmic 64 bit?"
date: 2010-03-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Minipalmer on 2010-03-22
Hey guys,

I just installed Kubuntu 9.10 Karmic Koala 64 bit and realized something...

I haven't heard any success stories about Dell wireless working in 64 bit! I'm working on a Dell Inspiron 1525, and the recommended Ubuntu hardwire drivers aren't working. I thought I had tried everything until I realized that it was my first time running 64 bit.

So, my question, has anyone else gotten wireless to work on a Dell in 64 bit?

TIA

---

### Post by rpared01 on 2010-03-23
when i had my Inspiron 1318 i had no problem runing it on 64bit. i would just load the broadcom driver that come in the iso and bing go it works. had you tried loading the drivers that come on in the iso ?

---

### Post by daveritah on 2010-03-23
I had problems with my wireless. installed ndiswrapper according the directions given in a thread, and now my wireless is working. The drivers that came on ISO and loaded in Karmic 9.10 woudn't work for some reason, so I went over to ndiswrapper. I have Dell 1501 with an AMD 64, however I have loaded 32 byte Karmic instead of the 64 byte, was told 64 bit can be a bit challenging and not everything works well. Hope, ndiswrapper will work for you, like it did for me. -Dave

---

### Post by coffeeaddict22 on 2010-03-26
Hi,
I'm on a Studio 17 with no problems.  It's one of the catches with Linux (or life in general); when it's working well we're all to busy messing around to document it!!

The question is usually the WLAN card; Dell uses Broadcom cards, and Broadcom have a closed source driver for linux.  If you open a terminal and type in ```
lspci
``` you'll get a list of your pci hardware; usually theres a line like ```
0c:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)

```which is your controller.  For mine, I'm on a Broadcom 4322 card.

Ubuntu doesn't have closed source drivers as part of the default install, so you have to go into System/Administration/Hardware Drivers to install the Broadcom driver.  Ndiswrapper is literally that: a wrapper for the NDIS (Network Driver Interface Specification) that wraps a MS Windows driver and interprets the information from the card for the Linux kernel.  It's still a binary blob, and is a workaround that is gradually getting phased out.

---

