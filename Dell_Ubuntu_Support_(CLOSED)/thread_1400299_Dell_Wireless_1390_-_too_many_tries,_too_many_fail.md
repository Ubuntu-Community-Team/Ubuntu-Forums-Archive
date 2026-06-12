---
title: "Dell Wireless 1390 - too many tries, too many failures, 2 day and counting"
date: 2010-02-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by igiveup on 2010-02-06
Hello everyone,
 
I am new to Linux and picked Ubuntu out of a suggestion that it is easier for new users. I installed Ubuntu within windows and can access it after restarting the computer and selecting it. There were issues with accessing the internet by LAN due to lack of active X (LAN security/login procedures) so I tried wireless and needless to say I found nothing.
 
I looked up many topics regarding the 1390 and I know I am not the only one to have problems; however, I am yet to be able to solve it. I have downloaded ndiswrapper...deb and related files and ran/installed them. However, most of the "fixes" were regarding older versions- 7-8- of ubuntu and not with the current 9.10 version. The problem comes when I find "applications" that is not installed and could not be installed through the terminal command. Also, I sometimes run into problems like on startup there are errors regarding the b43 (i have the fwcutter deb). I cant find the "Network" (not network tools) application and when i try to install a driver using the windows driver utility (ndiswrapper?), it gives a notice that says it cant detect hardware or something and also cant find network config tools when i press the configuration button. Ive tried a lot and things are a big mess right now and it has become very frustrating.
 
I will give the current details below-
 
Problem: Unable to use my wireless card to detect wireless connections due to incomplete setup of proper applications and/or configurations.
Status: No internet connection what-so-ever; LAN and Wireless both are off limits right now; tried several instructions off of forums of ubuntu, linux, and even a lunix-dell "wiki" but none has worked.
Computer: Dell Vostro 1500
Wireless: Dell Wireless 1390 WLAN Mini-Card (Broadcom?)
OS: WinXP 32 bit SP3; Ubuntu 9.10 32 bit
 
extra info:
 
"deb" list:
b43 fw cutter 011-1 i386
cabextract 1.2-2 ...
libaudio2 1.9.1-2 ...
libopenal1 1.4.272-2 ...
ndisgtk 0.8.4-1 ...
ndiswrapper common 1.9 1.54 ...
ndiswrapper utils 1.9 1.54 ...
cabextract 1.2-2 ...
wine 1.137
wine-gecko 0.1.

*-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:0c:00.0"]pci@0000:0c:00.0[/EMAIL]
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f9ffc000-f9ffffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: [EMAIL="pci@0000:03:00.0"]pci@0000:03:00.0[/EMAIL]
       logical name: eth0
       version: 02
       serial: 00:1d:09:bf:a4:d4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:17 memory:f9bfe000-f9bfffff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1f:3a:04:95:55
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by bobcollard on 2010-02-06
In your menu under "System" find Hardware Drivers and open that.  If you have already installed B43-fwcutter then there should still be one left called Broadcom STA  That is what you need.  You will have to have an Interenet connection like Ethernet to download the Proprietary Driver.  Then restart your computer.  After that go to your Internet icon in the task bar, right click it and open Edit connections.  Enter your ISP information and that should work.

---

### Post by igiveup on 2010-02-06
the probem is i have NO access by ethernet due to the login issue. usually in IE, an active X secruity alert comes in, you install what they need, then they direct you to download and install a security-login program. I even tryed installing the program on the Ubuntu OS but it doesnt work right- even with "wine".
 
Is there a way you can link me to all the files i need or tell me what they are so i can search for it?
 
else, is there a way to download these files while I am on winXP? i can always put on USB drive and then access it from Ubuntu through that.

---

### Post by Zerocool Djx on 2010-02-06
hey guys,.. I'm going through the same thing,.,...

Found this on youtube,..

[http://www.youtube.com/profile?user=emiemi2#p/u/9/v0Ist9aEKEg](http://www.youtube.com/profile?user=emiemi2#p/u/9/v0Ist9aEKEg)

---

### Post by igiveup on 2010-02-07
[edited]
after a while I noticed the wireless appeared. so far i have trouble connecting from getting off LAN RE-connecting but without LAN it will automatically go to wireless without much trouble.
 
well, at least it works... so it seems

---

### Post by Zerocool Djx on 2010-02-08
go a friends house, public library and connect Ethernet cable,.. take 5 min to install...

---

