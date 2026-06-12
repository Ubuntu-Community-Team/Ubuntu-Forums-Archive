---
title: "resolution need help!"
date: 2009-04-20
forum: General Help
---

### Post by mrsmither on 2009-04-20
can someone please tel me how to change the screen resolution.
I am stuck on 800*600 and can not get any higher!
Please help!!!!!!!!!!!!!!!!!!!
mr smither

---

### Post by Tyconic on 2009-04-20
For me (running Jaunty) it is under System -> Preferences -> Display

If you are using Nvdia chipset the other possibility is System -> Administration -> Nvidia X Server Settings

---

### Post by causeitsme on 2009-04-20
> **mrsmither said:**
> can someone please tel me how to change the screen resolution.
I am stuck on 800*600 and can not get any higher!
Please help!!!!!!!!!!!!!!!!!!!
mr smither

On the top bar, click system>preferences>display.

You should see from there options you can change.

---

### Post by mrsmither on 2009-04-20
yes thanx but i can't go any higher than i allredy am!
any idea?

---

### Post by facelesslucifer on 2009-04-20
i think it doesn't know ur VGA driver


if u wanna downlad VGA driver,the easiest way is update ur ubuntu. 


sudo apt-get install update-manager
sudo update-manager -d

---

### Post by mrsmither on 2009-04-20
thanx a bunch but it still doesn't work any sugestions...anybody

---

### Post by CMJ Tech on 2009-04-20
Don't know if this will help or not.  
My motherboard has an integrated graphics chip.  In my bios I can set the default screen resolution.  Are there any display settings in the bios for your motherboard that you can check?

Also, what brand of video adapter are you using?

---

### Post by mrsmither on 2009-04-20
i don't think it's a bios problem...
you the problem started when i started using a shich to use my screen for to computers (long story...)any way i'v got a ge-force i belive and i'm not shor whish one.
if you need ferther info i'll take the card out and have a look
thanx
mr smither

---

### Post by CMJ Tech on 2009-04-20
Knowing the type of GeForce card you have would be helpful in searching solution.

I did find a thread that may be helpful to you:
[http://ubuntuforums.org/showthread.php?t=1130097](http://ubuntuforums.org/showthread.php?t=1130097)

It describes a similar problem but in Xubuntu

---

### Post by mrsmither on 2009-04-20
thanx i'll try to get the name of the g-force
sorry but i'm new to ubuntu i don't sepos you could explayn what that guy did could you.
i would be highly appriciated!
thanx in advance
mrsimther

---

### Post by DJonsson2008 on 2009-04-20
You can change the resolution of your screen using the
more or less failsafe Ubuntu vesa driver and by editing your 
xorg.conf file by hand, but you must know the
resolutions/refresh rates your monitor can handle.

If your screen/card combination was working before
you likely have some automated backups to be found
in your /etc/X11 directory, that may provide clues
to previous settings, you may want to browse there,
perhaps rolling back by copying to a previous file 
that worked or reading the files to see what you had
going before.

There seems to be a point where the Ubuntu GUI breaks,
in terms of video drivers, displayconfig, jockey and 
so on, and editing the xorg.conf manually becomes the
best solution, not sure if that is your case or not,
but it happens sometimes.

The following commands will help, and perhaps save you
from having to crack open the case.

lspci | grep nVidia

and/or 

lspci can perhaps help you find if your system is
seeing the card and what it Identifies it as.

---

### Post by CMJ Tech on 2009-04-20
> **mrsmither said:**
> thanx i'll try to get the name of the g-force
sorry but i'm new to ubuntu i don't sepos you could explayn what that guy did could you.
i would be highly appriciated!
thanx in advance
mrsimther

That would be like the blind leading the blind! :D   I just started linux myself about a month ago and finally got my system working with ubuntu 7.10 yesterday.  After re-reading his post again, it sounds like he entered the commands (apt-get update) and (apt-get upgrade) he mentioned at the command prompt.  To get to the command prompt you have to open up a terminal window.  

Hopefully some more experience users will jump in soon!

I see someone more experience has jumped in!

---

### Post by mrsmither on 2009-04-20
can someone help?

---

### Post by mrsmither on 2009-04-20
sorry i'm new to ubuntu could you do me a VERY simple step by step.
It would be highly appriciated!
thanx in advance
MrSimther

---

### Post by chomptown on 2009-04-20
it took me a while to get my intel onboard graphics card to work.  People will tell you that using the vesa driver works, but I couldn't disagree more.

How about you go to a terminal and type:

blkid

copy/paste what it prints out into a response so we can see what type of hardware you are using.

---

### Post by mrsmither on 2009-04-20
here you go:
/dev/sda1: UUID="fe10492a-d9d5-409f-be28-0133407d3727" TYPE="ext3" 
/dev/sda5: UUID="45440452-18f5-4253-baf6-de30b06c0741" TYPE="swap" 
/dev/sdb1: UUID="C690858D90858521" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 


thanx!

---

### Post by chomptown on 2009-04-20
Oh oops, hahaha sorry wrong command, I probably shouldn't be doing this while working on other things at the same time.  please type "lspci"  into the command prompt and give us the results.  thanks

---

### Post by mrsmither on 2009-04-20
rie i'm gowing to bed...
what did that command do??
here's the risult of the second one:


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)
02:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 06)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0d.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

---

### Post by mrsmither on 2009-04-20
rie i'm gowing to bed...
what did that command do??
here's the risult of the second one:


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)
02:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 06)
02:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 06)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS)
02:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0d.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)

thanx in advance
mr smither

---

### Post by chomptown on 2009-04-20
The other command was for listing the drives connected to your computer.  It is just listing the locations and UUIDs.... something that doesn't matter to you.


It appears you have the NVidia graphics card, which I have seen some fixes for

> 01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

Have you tried editing your xorg.conf file yet?  If you don't know what that is, I'm sure we can point you in the correct direction so that we can at least see what drivers you are running at the moment.


When you get a chance go into your system folder then /etc/x11/xorg.conf just double click on that file, and paste it here.  As long as you are Not logged in as the root, you shouldn't be able to make any changes to the file.  We'll describe how to do that later.

---

### Post by mrsmither on 2009-04-21
here you go i hope you can help!

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by mrsmither on 2009-04-21
incedently i'm not to shure about any thing to do with information about the monitor.
I herd it had something to do with it.
Anyway hope you can help!
MrSmither

---

### Post by mrsmither on 2009-04-21
can ayone help??????????????

---

### Post by mrsmither on 2009-04-21
thanx so muthch i'v got it

---

