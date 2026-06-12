---
title: "Dell D600 WiFi not working"
date: 2009-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mintcake on 2009-10-21
I am an absolute Ubuntu beginner and cannot get WiFi or networks to work on recently installed 9.04.

There seems to be fixes out there but the technomagic speak lost me.

Sorry guys but you will have to dumb-down this one.

---

### Post by adempewolff on 2009-10-22
It is hard to say exactly what will work without knowing your wireless card, but.... try this first:

Click on the "System" menu on your top panel.  Then click "Administration", then "Hardware Drivers".

This should display a list of proprietary drivers.  My intuition is that you will probably see a driver called: Broadcom STA wireless driver.  This driver works for most of the lower end dell wireless cards.

Click on it, click the "Activate Button".  Ensure your wireless switch is on and restart your system.

If this doesn't work we can do some more troubleshooting

---

### Post by mintcake on 2009-10-23
adempewolffe
Many thanks for your help. 
When I look for drivers it shows 'No proprietary drivers are in use on this system' 
I have done some other tests and it confirms that a Broadcom Corporation NetXtreme BCM5705M Gigabit ethernet AND
Broadcom Corporation BCM4306 802.11b/g wireless lan are installed


many thanks for your time

Mintcake

---

### Post by adempewolff on 2009-10-25
Okay, your chipset uses the b43 driver.  In theory the driver is already installed you just need to install the firmware.

This page does a pretty good job of explaining what to do:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

In short you just need to install the package "b43-fwcutter".  If you can access the internet with an ethernet card, do so and download that package.  If you do not have internet access, insert the cd you installed from, open "Software Sources" (System:Administration) and check the Ubuntu CD in the "Installable from CDROM" box.

Then you can install the package in Synaptic (System:Administration), or by typing in a terminal (Applications:Accessories:Terminal):
```
sudo apt-get install b43-fwcutter
```

Installing the package should automatically extract and install your firmware.

---

### Post by mintcake on 2009-11-19
> **adempewolff said:**
> Okay, your chipset uses the b43 driver.  In theory the driver is already installed you just need to install the firmware.

This page does a pretty good job of explaining what to do:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

In short you just need to install the package "b43-fwcutter".  If you can access the internet with an ethernet card, do so and download that package.  If you do not have internet access, insert the cd you installed from, open "Software Sources" (System:Administration) and check the Ubuntu CD in the "Installable from CDROM" box.

Then you can install the package in Synaptic (System:Administration), or by typing in a terminal (Applications:Accessories:Terminal):
```
sudo apt-get install b43-fwcutter
```

Installing the package should automatically extract and install your firmware.
Many thanks for your help. I have been away so apologise for tardy reply. I installed fwcutter and got some major system error reports. WiFi did not work. next day switched it on and WiFi was there. Seems to be some hardware issues but WiFi seems consistent now.

Many thanks as I do think that your advice was key to it all.

---

### Post by ingjerd on 2010-03-27
I am having the exact same problem on my dell d600.

When I tried your instructions in a terminal window it says:
Could not find the package.

I am on Ubuntu 9.10

Is there any other way to get the wifi to work?

---

### Post by rpared01 on 2010-03-27
what i do is:
go to the software resources and enable the ubuntu cd.
next i open the cd
then go to "/pool/restricted/b/bcmwl/" on the cd
double click on "bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb"
then reboot and bam...wireless is working for me

after just go back software resources and uncheck the cd

---

