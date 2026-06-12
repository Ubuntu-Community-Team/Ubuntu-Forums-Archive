---
title: "Need help with HostAP on Ubuntu 6.06"
date: 2007-04-02
forum: Education &amp; Science
---

### Post by chyeo on 2007-04-02
Hi All,

Anyone here familiar or used HostAP before?

I am having a problem in using HostAP. I've installed the HostAP (v0.5.7) driver in ubuntu v6.06 and now, I am having problem in running it. I totally have no idea on where to start. I've tried searching for the guides everywhere but that brought me to dead end. The problem is I am new to Linux too.

Anyone can guide me through this. :( Your help is really appreciated.

Thank you.

-chyeo-

---

### Post by tripleee on 2007-04-11
I'm not at all sure whether I can be any help, but anybody who tries to tackle this will want to know more or less the following:

[LIST]
[*] The version of HostAP you have and how you installed -- [FONT="Courier New"]apt-get install hostapd[/FONT] or what?
[*] The cards you are using, what brand and model, what driver, do you know they work with HostAP? what other driver(s)?
[*] Your network topology. Which part of the network are you trying to configure, what does it connect to, how?
[LIST]
[*] For example, if your upstream (ISP) is running DHCP and gives you an address in the 10.x.x.x netblock on eth0, and you run hostap on eth1 (wlan0, what have you), do you use DHCP for clients who connect, do you use WEP or WPA (or no encryption at all), what network, 192.168.0.1? If you don't know then say so. If you can't decide then say so. If you don't know which parts you can decide yourself, say so.
[/LIST]
[*] What you have tried and how it failed. Provide links to HOWTOs etc.
[/LIST]

Hope this helps a little bit already ...

---

### Post by chyeo on 2007-04-16
Hi triplee,

I've installed the HostAP v0.5.7 using the command (apt-get install). I am using wireless USB adapter (Model: ZyXEL G-202) instead of using wireless card, but I am not very sure either they do work with HostAP. 

Basically, I am doing this for my college project. I need to come out with 2 computers running on HostAP, meaning both will act as access point to replace the real access point. Then, I will have 1 client. What I need to come out is roaming between the client and the access points. I need to test the WEP and WPA security as well as the authentication schemes such as EAP & PEAP. I need to do comparison between WEP & WPA and EAP & PEAP.

Thanks for the inputs... it do help me a little bit... 

-chyeo-

---

### Post by tripleee on 2007-04-16
Can you find out which chipset is in the ZyXel adapter?  If you lspci (and/or lspci -v and/or -vv) with the USB adapter plugged in, do you get anything useful for that adapter?  When you plug it in, do you get anything useful in /var/log/syslog?

HostAPd (the access point software) is advertised to work with Prism chipsets and Atmels (hostap without the d, the wireless driver, or Prism54 for Prisms, Madwifi for Atmels) as per [http://hostap.epitest.fi/hostapd/](http://hostap.epitest.fi/hostapd/)

In my limited experience hostapd as such is a snap to set up once you have all the components talking to each other.  Apparently you don't have the wifi link up yet, so I'd suggest you concentrate on that first.

---

