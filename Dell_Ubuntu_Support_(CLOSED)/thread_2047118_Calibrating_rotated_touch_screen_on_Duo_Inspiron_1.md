---
title: "Calibrating rotated touch screen on Duo Inspiron 1090 - please help!"
date: 2012-08-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by loxley108 on 2012-08-24
Hi all

Am still enjoying learning all about Ubuntu and getting my Duo to work how I want it to - but one thing has really stumped me and its getting me down to be honest.

I have got the touch screen working fine whilst in netbook mode - callibrated etc. 

I have also assigned a rotation script from the Setup Guide and assigned it to a key - when I press it the screen rotates.

However, no matter what I do i can't get the touch screen callibrated whilst its rotated  - when i press it the curse is always a couple of inches away from my finger and no matter which way I move my finger, the cursor just goes up and down.

This is really frustating me as it means I can't use it as a tablet and that was a main reason for buying the Duo - i've looked in forums etc. but seem to be going around in circles.

I am running Ubuntu 12.04.

Fingers crossed someone can help me.

Thanks

---

### Post by Favux on 2012-08-24
Hi loxley108,

Could you link us to this rotation script you are using?

There are two screens correct?  Are both touchscreens?  Are both the same size and what is the size?

What are the touch screens called?  What's the output of **lspci** and **xinput list** in a terminal?

---

### Post by loxley108 on 2012-08-24
Hi 

Many thanks for your reply.

The rotating script that i use is this one: 
[http://ubuntuforums.org/showpost.php...&postcount=194](http://ubuntuforums.org/showpost.php...&postcount=194)

But just been ploughing through the 70 odd pages on the Duo thread and noticed there's another I can try here:

[http://ubuntuforums.org/showthread.php?t=1658635&highlight=dell+duo&page=71](http://ubuntuforums.org/showthread.php?t=1658635&highlight=dell+duo&page=71)

Will try this one later and see if it works.

There is a single screen but it flips over to make the tablet.

I'm not sure how to find out the output of *lspci* and *xinput list* in a terminal?

Thanks everyone for your help!

---

### Post by Favux on 2012-08-24
Your link to the script you are using isn't any good.  If its the one on the first post of the thread, the HOW TO, I already found it.  It's a C daemon that uses the CTM (coordinate transform matrix) to rotate.  And the CTM it is calculating for your touch screen is wrong, obviously.  So the touch screen is probably on evdev.  You should be able to disable it by opening Startup Applications and unchecking the run at start (or whatever the check box is called) for it.
> I'm not sure how to find out the output of *lspci* and *xinput list* in a terminal?
Open a terminal and enter one of the commands and post its output.  Do the same with the other command.

---

### Post by loxley108 on 2012-08-24
Hi

lspi output:


00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Multimedia controller: Broadcom Corporation BCM70015 Video Decoder [Crystal HD]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

xinput:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; eGalaxTouch Virtual Device for Multi    	id=14	[slave  pointer  (2)]
&#9116;   &#8627; eGalaxTouch Virtual Device for Single   	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_1.3M           	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]

Hope someone can help me - the screen isn't rotating at all - feel like i'm going round in circles.

Very depressing...

---

### Post by Favux on 2012-08-24
Alright so it is an eGalax touchscreen.  Please post the output of **lsusb** in a terminal.  We want to find out if the internal connection for the touchscreen is usb or serial.  Probably usb.

Looks like it offers both single finger and multi-finger touch.  I assume it is on the evdev X drive.  Let's check that.  Run this command in a terminal:
```
xinput list-props 14
```
and post the output.  That should show us multi-touc.  The ID # 15 would be single.  Also if you restart or hot plug the ID numbers can change to run **xinput list** again to check.

If it is on evdev which direction do you want it to rotate in?

---

