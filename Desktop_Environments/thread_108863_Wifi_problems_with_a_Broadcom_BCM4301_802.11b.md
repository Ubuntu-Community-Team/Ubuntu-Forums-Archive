---
title: "Wifi problems with a Broadcom BCM4301 802.11b"
date: 2005-12-27
forum: Desktop Environments
---

### Post by ElimFarQ on 2005-12-27
I have just recently installed Ubuntu on Compaq Presario R3003AP which has an onboard Broadcom BCM4301 802.11b Wifi card. The card works with Windows XP with no problems, so I know the problem is not hardware based. 

I believe it has been installed correctly, because when I run *lspci* I find the the following in the output.

*0000:02:02.0 Network controller: Broadcom Corporation BCM4301 802.11b (rev 02)*

However if the interface doesn't seem to be there. 

When I run the command *ifup wlan0* I get the following error message. *Ignoring unknown interface wlan0=wlan0.*

So it seems to me that the device drivers for the card are installed but the interface is just not there. 

Could I please get some help in creating the wifi interface. Or if I am incorrect, can I please get someone to correct me. 

If you require some more information please let me know.

Thanks

---

### Post by ruudiculus on 2005-12-27
Are you using ndiswrapper? If so try:

**ndiswrapper l**    //This will list your installed windows driver and hardware

If it says "driver found and hardware present" proceed by typing:

**modprobe ndiswrapper**    //Interconnects the ndiswrapper module with th hardware (wlan0)

And to enable wlan0 automaically at boot time type:
**ndiswrapper m**

If you're not using ndiswrapper, consider this help as trash :) If you think you have to use ndiswrapper and didn't use it until now, search the forum: there's a lot of good help on enabeling wireless cards using ndiswrapper.

---

### Post by greenfrog on 2005-12-27
Do a search on this forum for your wireless card.  There are several guides for installing this card.  I have the same one in my HP Pavilion.  It took several try's but I finally got it to work.

Good Luck:)

---

### Post by ElimFarQ on 2005-12-27
Thanks for the help.

I have not used NDISWRAPPER, this is a fresh install.

---

### Post by Lambert on 2005-12-27
The device is recognized but there is no linux driver for your device. So you need to use ndiswrapper to make the windows drivers work. You can search around as there are hundreds of posts about ndiswrapper but that can get confusing. 

There's also a link in my signature to the wiki about using ndiswrapper. Inside that page is a link to the main ndiswrapper wiki with intallation instructions also.

---

### Post by ElimFarQ on 2005-12-29
Got it working. Well I got the device drivers installed. All I need to do is test it. I shall do it tonight (No WiFi @ work). 

Thanks for the help !

---

### Post by madjinx on 2005-12-29
[QUOTE=Lambert]The device is recognized but there is no linux driver for your device. So you need to use ndiswrapper to make the windows drivers work. You can search around as there are hundreds of posts about ndiswrapper but that can get confusing. 

There's also a link in my signature to the wiki about using ndiswrapper. Inside that page is a link to the main ndiswrapper wiki with intallation instructions also.[/QUOTE]

ermmm, there are drivers, broadcom releases the source for the 43xx series chips.

---

### Post by Lambert on 2005-12-29
No source has been released.

>  We are attempting to reverse-engineer drivers for the Broadcom 43xx chipset, which is used in a [wide variety]("http://linux-bcom4301.sourceforge.net/go/hardware") of wireless cards.

It will only work with a 2.6.15 kernel or greater.

> 

The project page is [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)


Requirements
------------

1)      Linux Kernel 2.6.15 or later
        [http://www.kernel.org/](http://www.kernel.org/)


It's currently in dapper but it is very buggy with limited success stories currently. It's coming but not there yet.

---

