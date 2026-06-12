---
title: "Interesting touchpad issue"
date: 2010-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by teamgs on 2010-01-26
Greets,
While I have 12 years in the business with Win servers and desktops, I have only one week with Linux. :D I recently installed Mint 8 General Release on an old Dell Inspiron 5000, and while it went pretty much as planned, the touchpad wasn't recognized. 
 
After much messing around, and many reboots, I determined that, as long as a USB mouse is plugged in at the time of boot, the TP is also recognized and functions properly. If the USB mouse isn't plugged in at boot, the TP is no longer recognized. 
 
I have tried some of the older fixes that I found, such as i8402=reset into the grub.cfg, etc. but nothing works, except having the USB mouse plugged in a boot.
 
Any ideas?
 
I apologize if I have left off some glaring pertinant information, but as a noob in Linux, I am not sure of the conventions on this site. I will be happy to provide any additional data required to assist.
 
Regards,
 
Gary

---

### Post by bobcollard on 2010-01-27
> **teamgs said:**
> Greets,
While I have 12 years in the business with Win servers and desktops, I have only one week with Linux. :D I recently installed Mint 8 General Release on an old Dell Inspiron 5000, and while it went pretty much as planned, the touchpad wasn't recognized. 
 
After much messing around, and many reboots, I determined that, as long as a USB mouse is plugged in at the time of boot, the TP is also recognized and functions properly. If the USB mouse isn't plugged in at boot, the TP is no longer recognized. 
 
I have tried some of the older fixes that I found, such as i8402=reset into the grub.cfg, etc. but nothing works, except having the USB mouse plugged in a boot.
 
Any ideas?
 
I apologize if I have left off some glaring pertinant information, but as a noob in Linux, I am not sure of the conventions on this site. I will be happy to provide any additional data required to assist.
 
Regards,
 
Gary
Try installing either "gsynaptics" or "gpointing-device-settings"  You can find both in the Synaptic Package Manager or use one of the following codes in Terminal: " sudo apt-get install gsynaptics " " sudo apt-get install gpointing-device-settings "  (Without the quotes of course.)  Then put either one in your startup programs and reboot without the mouse plugged in.  It should give you a choice of using the touch pad or the mouse by disabling the touch pad.  Incidentally, I use Linux Mint too.

---

### Post by teamgs on 2010-01-27
Thanks for the assistance, Bob. I had tried using gsynaptics before, with no luck, but not by adding it to the startup menu, as you stated. 
 
After adding it, and rebooting, success! :D
 
BUT.... (You knew there was going to be a but...) After a second reboot, the same issue occured again, this time getting the error "GSynaptics couldn't initialize. You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics."
 
I assume that this is due to the TPad not being detected? 
 
I will keep troubleshooting...Thanks again!
 
Regards,
 
Gary

---

### Post by teamgs on 2010-01-27
After messing around some more, I have some more interesting behaviors to report. 
 
1. It appears that if I have the usb mouse inserted at boot, then the TP is detected everytime.
 
2. If after successful TP detection with the USB mouse inserted, I remove the USB mouse and reboot, then the TP is detected properly as well.
 
3. However, the next restart will again result in the TP not being detected.
 
This behavior is repeatable.
 
If this is related to the device detection sequence, is there a way to manually bypass the autodetection sequence and force device settings?
 
Strange....
 
Regards,
 
Gary

---

### Post by bobcollard on 2010-01-27
> **teamgs said:**
> After messing around some more, I have some more interesting behaviors to report. 
 
1. It appears that if I have the usb mouse inserted at boot, then the TP is detected everytime.
 
2. If after successful TP detection with the USB mouse inserted, I remove the USB mouse and reboot, then the TP is detected properly as well.
 
3. However, the next restart will again result in the TP not being detected.
 
This behavior is repeatable.
 
If this is related to the device detection sequence, is there a way to manually bypass the autodetection sequence and force device settings?
 
Strange....
 
Regards,
 
Gary
Go to sytem/mouse and keyboard and uncheck the touchpad, there should be two boxes, sorry forgot about that.  One won't work with the other engaged.  Then reboot.

---

### Post by teamgs on 2010-01-27
Hi Bob,
    The funny thing is that I did uncheck the touchpad option when I was in the startup programs list the first time, as I thought the same thing that you mentioned.  So the results were still the same.  It sees to me that the if the TP isn't detected by the OS properly at startup, then the gsynaptics app has nothing to find when it is run with the other startup apps, as they are the last to run.  In fact, the gsynaptics doesn't run until after the login.  
 
Thanks again, I really appreciate your help.
 
Regards,
 
Gary

---

### Post by bobcollard on 2010-01-27
> **teamgs said:**
> Hi Bob,
    The funny thing is that I did uncheck the touchpad option when I was in the startup programs list the first time, as I thought the same thing that you mentioned.  So the results were still the same.  It sees to me that the if the TP isn't detected by the OS properly at startup, then the gsynaptics app has nothing to find when it is run with the other startup apps, as they are the last to run.  In fact, the gsynaptics doesn't run until after the login.  
 
Thanks again, I really appreciate your help.
 
Regards,
 
Gary
If this solved your problem please Edit your first Post and include [Solved] in the Title so others may use this information.  Welcome to Linux.

---

### Post by teamgs on 2010-01-27
Hi Bob,
    Sorry, if I was unclear in my last post.  What I meant to say was that unchecking the Touchpad startup program did not solve the problem.  I still have the issue where the only way for continued detection of my TP is with a usb mouse also attached at startup.  If I have the USB mouse unattached, I can get one startup with the TP functional, but the next startup again finds the TP undetected.  Reattaching the USB mouse again starts the cycle.
 
Regards,
 
Gary

---

### Post by bobcollard on 2010-01-27
> **teamgs said:**
> Hi Bob,
    Sorry, if I was unclear in my last post.  What I meant to say was that unchecking the Touchpad startup program did not solve the problem.  I still have the issue where the only way for continued detection of my TP is with a usb mouse also attached at startup.  If I have the USB mouse unattached, I can get one startup with the TP functional, but the next startup again finds the TP undetected.  Reattaching the USB mouse again starts the cycle.
 
Regards,
 
Gary
Okay.  Did you try gpointing-device-settings?  It replaces gsynaptics which is becoming outdated, probably  why you got the error message.  Remove gsynaptics from your startup and uninstall it.  Then install the new one the same way.  Reboot a few times and see if that works.  I use gsynptics on Fluxbox and gpointing-device-settings on KDE.  both work for me, but hen I have a computer that is only six months old.  Don't give up.  If we cannot solve it here go to the forum for Linux Mint.

---

### Post by teamgs on 2010-01-27
Hi Bob,
    Gpointing gave a slightly different behavior, but ultimately the same results.  I booted after installing and placing it in the startup group.  After the OS came up, no TP movement, but no error message either.  Using just the keyboard, I rebooted the machine for fun, and, gues what?  The TP was active, and the gpointing interface popped up at startup.  I rebooted again with the same good results.  However, after the third reboot, no TP, no gpointing popup.  This is the way it stayed after numerous reboots, until I reconnected the USB mouse.
 
Really weird...
 
I have no intention of giving up.  I dig this kind of stuff.  Troubleshooting and learning new stuff is my favorite part of the business.  This is strictly a test machine, that may ultimately be left at our mountain cabin for basic internet access, so I am in no hurry.
 
I have already posted this issue on the mint forum, and was directed to some TP troubleshooting steps here.  I was unable resolve the issues with the steps (They were mainly for tablet pc's) so I thought I would just post the question here as well.
 
I will keep on plugging away, and continuing to scour the net for a solution I haven't tried yet.
 
Thanks a ton!
 
Gary

---

