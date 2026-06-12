---
title: "Problems booting from USB"
date: 2009-01-19
forum: General Help
---

### Post by everlong123 on 2009-01-19
Hello,

First post, but long time reader. Please forgive me if I sound like a greenhorn.
I recently got a Cloudbook cheap to mess around with it. gOS is rubbish but am finding problems installing a dualboot XP-Ubuntu system.

Firstly, I can't even get the system to boot from USB. I've triple checked the BIOS settings and it should be fine. However, the damn thing just won't boot. It goes through initial startup and then appears to try and boot from USB and stops right there. It just displays a blank screen with a prompt cursor at the top and nothing else. No directory reference no nothing.
I can not type commands on this screen and after a while, it detects the unsuccessful boot and continues to load GRUB for gOS.
I can also get off the non-responsive prompt screen by pulling out the USB drive and then gOS precedes to load.

What is the problem? I've looked all over forums and no one seems to have this problem. Is it a problem with how I've setup the USB drive? I used this guide [http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html) or just copied the XP onto the USB drive or just a blank USB drive. My copy of XP is not nlite modified

all attempts to boot from USB give the same non-responsive screen.

Any help would be gratefully accepted.

---

### Post by Lucroth on 2009-01-23
I was having some settings issues with a USB thumbdrive I had setup so I decided to just reinstall to set everything back to default. 

I am now having the same thing happen to me. I tell it to boot from the USB and it just sits there with the cursor blinking at you. 

I have tried both using the built-in usb drive installer and following the instructions at [http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/) a couple times now and keep getting the same result. 

One thing that may be worth noting, when I do the install attempts using the "create a USB startup disk" utility it gets to approximately 40% and then immediately stops and says its done. It does it at the same place everytime.


SOLUTION:

Okay, here is the solution for anyone else having this problem. This is at least what worked for me and has seemed to be a solution for some other people. The flashing cursor essentially just means that it can't find an operating system to run. (installation didn't work right)

1. Put the thumbdrive in. Go to System -> Administration -> Partition Editor.

(If you do not have Partiton Editor listed there, then go to Applications -> Add/Remove programs. Find GNOME partition editor and add it to your system. Start at step one again)

2. In Partition Editor, in the top left go to GParted -> Devices and select your usb thumbdrive. (If you don't change the device selected you will reformat your harddrive, thats bad.) If you're not sure which is your thumbdrive, just look at the size of them.

3. In partition Editor right click on the line listing your device's information, choose 'unmount'. 

4. Up in the top bar, click on Device -> Create partition table. Just leave it set to msdos and click okay.

5. Now go to the "Create a USB startup disk" utility and run it normally and it should work.

---

