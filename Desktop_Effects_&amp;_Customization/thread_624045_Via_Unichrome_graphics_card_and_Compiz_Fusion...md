---
title: "Via Unichrome graphics card and Compiz Fusion.."
date: 2007-11-26
forum: Desktop Effects &amp; Customization
---

### Post by Hickler on 2007-11-26
I just installed Ubuntu Gutsy on my desktop, but when I try to enable desktop effects, I get "Desktop effects could not be enabled" I have a Via Unichrome graphics card (honestly I haven't even heard of it) and I was wondering if this works with Compiz. I'm assuming I don't need any drivers because when I click "Restricted Drivers" it says my hardware doesn't need any... Can you help?

Thanks.

---

### Post by daengbo on 2007-11-26
It looks like you need to install this package:
xserver-xorg-video-openchrome

The description:
> Description: X.Org X server -- VIA display driver
 OpenChrome is a project for the development of free and open-source software
 for the VIA UniChrome video chipsets.
 .
 Originally called the 'snapshot' release, since it was a snapshot of an
 experimental branch of the unichrome cvs code, this is a continued development
 of the open source unichrome driver (from <URL:http://unichrome.sf.net>) which
 also incorporates support for the unichrome-pro chipsets.
 .
[B] Support for hardware acceleration (XvMC) for all chipsets has subsequently
 been ripped out of the unichrome.sf.net driver. Therefore your only option if
 you wish to make use of the acceleration features of your VIA chip with free
 and open-source drivers is to use this version of the driver.[/B]
 .
 This driver is originally shipped to be loaded as 'via' on xorg.conf, but this
 package renames it to 'openchrome', so it doesn't conflicts with the other VIA
 driver already available on Ubuntu.
 .
 More information about Openchrome can be found at:
 [http://www.openchrome.org](http://www.openchrome.org)

Make sure taht package is installed by clicking [this link]("apt:xserver-xorg-video-openchrome"), then go to System -> Administration -> Screens and Graphics and choose the openchrome driver. After you restart your graphics layer by logging out, you should be able to enable 3D effects.

Let us know if you have any other problems.

---

### Post by Hickler on 2007-11-26
I see... I'll be back in a minute with the results, and thanks for your help.

---

### Post by Hickler on 2007-11-26
I click it, say yes, and get this:

Can not install 'xserver-xorg-video-openchrome' (E:Unable to correct problems, you have held broken packages.)

can I just go ```
sudo apt-get install xserver-xorg-video-openchrome
```

**EDIT:** I tried installing it with apt-get, but it said

```
sudo apt-get install xserver-xorg-video-openchrome
[sudo] password for seth:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  xserver-xorg-video-openchrome: Depends: libviaxvmc1 (= 0.2.6+svn357-0ubuntu3) but it is not going to be installed
                                 Depends: libviaxvmcpro1 (= 0.2.6+svn357-0ubuntu3) but it is not going to be installed
E: Broken packages

```

---

### Post by Hickler on 2007-11-26
I'm gone to bed now, but I'll try again tomorrow... (after school)

---

### Post by searayman on 2007-11-26
i am pretty sire unichrome doesnt have a good enough open source driver for you to be able to run compiz fusion

---

### Post by ikey_d on 2007-11-26
I've been trying this for quite a while with Feisty and Gutsy... my conclusion is VIA cannot run compiz-fusion or beryl... I've tried the driver from VIA, openchrome with all kinda howtos... no go

---

### Post by Hickler on 2007-11-27
Ah, too bad. If I find a good how to, I'll post it at the forums somewhere.

---

### Post by altonbr on 2007-12-15
I'm having the same problems with my girlfriend's VIA Unichrome driver. Any answers yet?

---

### Post by markmaus on 2007-12-16
daengbo,
Thanks for the tutorial.  I'm trying to install the openchrome driver on a (Gutsy) Averatec 3225HS Laptop with the S3 Graphics Unichrome (KM400) video chipset.  I did manage to apt-get install xserver-xorg-video-openchrome, but I had to include libviaxvmc1 and libviaxvmcpro1 in the command, because atp-get wouldn't retrieve those dependancies on its own (strange).  I sucessfully went to the link provided above and it said that openchrome was already installed.  But when I went to System -> Administration -> Screens and Graphics, there was no "openchrome" to select.  So I editied my /etc/X11/xorg.conf file and changed "via" to "openchrome". (Was that a mistake?)  Now when I reboot, X does not start and I get a bunch of errors about "Microcode bcm43xx_microde5.fw not available or load failed."  I think that it is the old problem of with irqpoll and noapic and apci=off or some combination of about a dozen such commands.  Any advice would be appreciated.
Thanks,

---

### Post by VereVa on 2008-01-08
> errors about "Microcode bcm43xx_microde5.fw not available or load failed." 

install drivers for WiFi cards... (use ndiswrapper)

---

### Post by maxpower44 on 2008-01-24
I have the same problem, I installed xserver-xorg-video-openchrome. but I can't choose it from the "Screens and Graphics" utility.
I change it in xorg.conf with "openchrome"  but it does work.
According to the package properties, the installed file is via_drv.so so I tried via too (still in xorg) but it doesn't work.

BTW where is the log file ? when I open /var/log/Xorg.0.log I have the log for the xorg.conf.failsafe only. This is very annoying ....

---

### Post by cool2000m on 2008-01-25
> **markmaus said:**
> daengbo,
Thanks for the tutorial.  I'm trying to install the openchrome driver on a (Gutsy) Averatec 3225HS Laptop with the S3 Graphics Unichrome (KM400) video chipset.  I did manage to apt-get install xserver-xorg-video-openchrome, but I had to include libviaxvmc1 and libviaxvmcpro1 in the command, because atp-get wouldn't retrieve those dependancies on its own (strange).  I sucessfully went to the link provided above and it said that openchrome was already installed.  But when I went to System -> Administration -> Screens and Graphics, there was no "openchrome" to select.  So I editied my /etc/X11/xorg.conf file and changed "via" to "openchrome". (Was that a mistake?)  Now when I reboot, X does not start and I get a bunch of errors about "Microcode bcm43xx_microde5.fw not available or load failed."  I think that it is the old problem of with irqpoll and noapic and apci=off or some combination of about a dozen such commands.  Any advice would be appreciated.
Thanks,

I have the same problem. And when I enable xserver-xgl, the login just looping, unless I enable failsafe mode...

I have a KM400/ VT8378 video card. anybody know a fix?

---

### Post by maxfive5 on 2008-02-29
Hi!
I've just buyed a VIA PC2500E Mainboard with the Unichrome Prog. How can I enable compiz fusion? This is my first time in ubuntu...please reply me as soon as possible!!
:lolflag:

Tnx

---

### Post by mason215 on 2008-03-01
> **daengbo said:**
> It looks like you need to install this package:
xserver-xorg-video-openchrome

The description:


Make sure taht package is installed by clicking [this link]("apt:xserver-xorg-video-openchrome"), then go to System -> Administration -> Screens and Graphics and choose the openchrome driver. After you restart your graphics layer by logging out, you should be able to enable 3D effects.

Let us know if you have any other problems.


ok i bringing this thread back because i tried this, i went to select the "openchrome" video card, and then it just hung, so i rebooted it and now wont let me boot ubuntu(its just a blank black screen). is there a command so i can unistall the "openchrome" video card.

---

### Post by mason215 on 2008-03-01
bump

---

### Post by kulotzy on 2008-03-14
> **mason215 said:**
> bump

Same here... having troubles with the similar driver

---

### Post by daengbo on 2008-03-17
Sorry for the delayed response. To uninstall the driver, press ESC at boot time to choose a boot option, then choose to boot into single-user recovery mode. At the prompt, type the following:
apt-get remove xserver-xorg-video-openchrome libviaxvmc1 libviaxvmcpro1
apt-get install ubuntu-desktop
dpkg-reconfigure xserver-xorg

Then reboot. That should get you the old, non-accelerated desktop back.

---

