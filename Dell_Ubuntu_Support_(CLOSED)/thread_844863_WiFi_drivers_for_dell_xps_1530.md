---
title: "WiFi drivers for dell xps 1530"
date: 2008-06-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sanjeevkode on 2008-06-30
hi guys iam new to this forum , i bought a new dell xps1530 

i hve installed ubuntu 7.10 gusty , i need help to install wifi drivers and where i can find them ....

ur response n help is appreciated 

thank you

---

### Post by pablopancho on 2008-06-30
Hi,

What wireless card do you have? In my dell xps 1530 I have Intel PRO/Wireless 4965 AGN. Hardy Heron (8.04) detected it with no problems. Bluetooth works flawlessly as well. 
Is your system not detecting any wireless card or just not connecting? Maybe there are problems with network password? I found that network manager and gnome keyring don't like each other in ubuntu and the password is lost sometimes.

---

### Post by sc00ter on 2008-06-30
I also have a M1530 and nearly everything works out of the box. Please see a previous post I made that lists a couple of links which helped me get Ubuntu onto this fantastic machine.

[http://ubuntuforums.org/showpost.php?p=5158161&postcount=3](http://ubuntuforums.org/showpost.php?p=5158161&postcount=3)

---

### Post by sanjeevkode on 2008-06-30
> **sc00ter said:**
> I also have a M1530 and nearly everything works out of the box. Please see a previous post I made that lists a couple of links which helped me get Ubuntu onto this fantastic machine.

[http://ubuntuforums.org/showpost.php?p=5158161&postcount=3](http://ubuntuforums.org/showpost.php?p=5158161&postcount=3)

Hi Buddy thanks for the help , my lap top is using dell minicard 1395.Below is configuration of my laptop

ntel® Core™2 Duo T5550 with 667MHz frontside bus, 2MB L2 cache and 1.83GHz processor speed
4GB DDR2 memory for multitasking power
Multiformat DVD±RW/CD-RW drive with double-layer support 
Glossy 15.4" WXGA+ high-definition widescreen display with TrueLife technology and 1440 x 900 resolution
320GB Serial ATA hard drive (5400 rpm)
Biometric fingerprint reader for secure access to your data 
NVIDIA GeForce 8400M GS graphics with up to 128MB discrete video memory; 24bit HD audio & S-video output
Built-in 2.0-megapixel Web cam
8-in-1 media card reader supports SD, SD IO, SDHC, SD HD, MS, MS Pro, MMC and xD-Picture Card
IEEE 1394 (FireWire) interface and 4 high-speed USB 2.0 ports
Dell Wireless 1395 mini-card and 355 Bluetooth Module
10/100 Ethernet network card

in this wifi is not working when i connect through a cable it is working ....

---

### Post by sanjeevkode on 2008-06-30
> **pablopancho said:**
> Hi,

What wireless card do you have? In my dell xps 1530 I have Intel PRO/Wireless 4965 AGN. Hardy Heron (8.04) detected it with no problems. Bluetooth works flawlessly as well. 
Is your system not detecting any wireless card or just not connecting? Maybe there are problems with network password? I found that network manager and gnome keyring don't like each other in ubuntu and the password is lost sometimes.

Hi Buddy thanks for the help , my lap top is using dell minicard 1395.Below is configuration of my laptop

ntel® Core™2 Duo T5550 with 667MHz frontside bus, 2MB L2 cache and 1.83GHz processor speed
4GB DDR2 memory for multitasking power
Multiformat DVD±RW/CD-RW drive with double-layer support
Glossy 15.4" WXGA+ high-definition widescreen display with TrueLife technology and 1440 x 900 resolution
320GB Serial ATA hard drive (5400 rpm)
Biometric fingerprint reader for secure access to your data
NVIDIA GeForce 8400M GS graphics with up to 128MB discrete video memory; 24bit HD audio & S-video output
Built-in 2.0-megapixel Web cam
8-in-1 media card reader supports SD, SD IO, SDHC, SD HD, MS, MS Pro, MMC and xD-Picture Card
IEEE 1394 (FireWire) interface and 4 high-speed USB 2.0 ports
Dell Wireless 1395 mini-card and 355 Bluetooth Module
10/100 Ethernet network card

in this wifi is not working when i connect through a cable it is working internet is working .......

thank you

---

### Post by damis648 on 2008-06-30
You have a Broadcom chipset card. Broadcom does not make Linux drivers for thier cards, so you will have to use ndiswrapper with a Windows driver. There are plenty of guides with a bit of Googling. Try this one: [http://ubuntuforums.org/showthread.php?t=704088](http://ubuntuforums.org/showthread.php?t=704088) . I Can not verify that it works, as I have the Intel 4965AGN card.

---

### Post by pablopancho on 2008-06-30
Unfortunately I'm not an expert so I can't guide you through ndiswrapper installation but I found a thread where problems with wifi card has been solved. I hope this will help you: 
[http://ubuntuforums.org/showthread.php?t=817186&highlight=Dell+Wireless+1395+mini-card]("http://ubuntuforums.org/showthread.php?t=817186&highlight=Dell+Wireless+1395+mini-card")

---

### Post by stats on 2008-07-07
the driver is in the repo now
if you dint install  ndiswrapper then skip steps 2,3,4 
1.Update & upgrade using update-manager/synaptic/adept etc
2.
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then

```
sudo modprobe -r ndiswrapper
```

If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

---

