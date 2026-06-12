---
title: "combination of metacity/compiz problems"
date: 2009-06-29
forum: Desktop Environments
---

### Post by plasm980 on 2009-06-29
Hi all,

I'm relatively new to the Ubuntu thing, but I've learned a LOT by searching this forum over the last several months.  I've recently come up against a series of problems that I can't seem to claw out of, and it's driving me nuts.  Any help would be much appreciated.

Background:

I have Ubuntu 9.04 with an NVIDA 9600M GT, using the nvidia-glx-180 drivers.  My xorg.conf file contains:

> Section "Device"
	Identifier     "Device0"
	Driver         "nvidia"
	VendorName     "NVIDIA Corporation"
        Option  "GlyphCache"  "1"
        Option  "InitialPixmapPlacement"  "2"
EndSection

Symptoms:

1) I used to use compiz to have all of the neat animation effects.  However, I was having issues with blocks of text not appearing in my gvim windows when I PgUp/PgDown through a file (it would just be black where there should have been text).  Moving the window itself would get the text to appear, so I figured it was a compositing or window manager problem.

2) I switched from compiz to metacity by going to System->Preference->Appearance->Visual Effects and selecting "None".  This solved the problem of text mysteriously not appearing in my gvim windows.  However, it also caused Xorg to start using a LOT of CPU for simple tasks such as scrolling in Firefox or moving windows around the screen.  In fact, when I first log into my Gmail account, Xorg pins one of my cores to 100% for a full 10-15 seconds (used 'top' to check) as it renders my inbox.  Another symptom is Xorg pegs to 100% when I scroll up and down pretty much any webpage in Firefox.  Both of these operations used to be trivial under compiz, so it's not a Firefox problem.

3) Now I am unable to switch from metacity back to compiz.  If I try to select "Normal" or "Extra" in the Appearance Preferences dialog box, I get an "Desktop effects could not be enabled" message.  If I run "compiz --replace" in a terminal window, I get 

> Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


Checking gconf-editor, apps->metacity->general->compositing_manager, the checkbox is not selected, so the metacity compositing manager shouldn't be running.  However it appears to be running anyways since my cairo-dock application is showing transparency correctly.

I'm now totally stuck with metacity with no way of getting back to compiz.  This wouldn't be so bad except for Xorg using 100% of CPU for trivial tasks.

---

### Post by Anzan on 2009-06-29
Try installing Compiz Fusion Icon. It lets you switch back and forth.

I hate to say this but have you tried logging out and in or even (egad) rebooting?

GNOME's underthings can get bunched up and sometimes that's the only way to quickly sort them out. 

I recommend Fluxbox.

---

### Post by plasm980 on 2009-06-29
> **Anzan said:**
> Try installing Compiz Fusion Icon. It lets you switch back and forth.

I hate to say this but have you tried logging out and in or even (egad) rebooting?

GNOME's underthings can get bunched up and sometimes that's the only way to quickly sort them out. 

I recommend Fluxbox.

Thanks!  Yeah, all of the steps I wrote were with reboots in between.  I get the same problems across reboots.

I'll try the Compiz Fusion Icon thing.

---

### Post by plasm980 on 2009-07-02
> **plasm980 said:**
> Thanks!  Yeah, all of the steps I wrote were with reboots in between.  I get the same problems across reboots.

I'll try the Compiz Fusion Icon thing.

It didn't work.  I get the same error as running "compiz --replace".  Anyone else have any suggestions? =)

---

### Post by plasm980 on 2009-07-02
I managed to get the metacity compositing manager disabled by checking the compositing box in gconf-editor, rebooting, then unchecking the box.  If the checkbox is unchecked on boot, the compositing manager runs on boot and toggling the checkbox has no effect.

Once the compositing manager was disabled, I ran compiz --replace successfully to switch to compiz.  However, if I log out and log back in, the system is running metacity again.

How do I make the switch to compiz permanent?  Thanks!

---

### Post by Favux on 2009-07-04
Hi plasm980,

Have you checked in Configuration Editor (gconf editor) that in desktop>gnome>session>required_components that the value for windowmanager is compiz?

---

### Post by ~sHyLoCk~ on 2009-07-04
> **plasm980 said:**
> I managed to get the metacity compositing manager disabled by checking the compositing box in gconf-editor, rebooting, then unchecking the box.  If the checkbox is unchecked on boot, the compositing manager runs on boot and toggling the checkbox has no effect.

Once the compositing manager was disabled, I ran compiz --replace successfully to switch to compiz.  However, if I log out and log back in, the system is running metacity again.

How do I make the switch to compiz permanent?  Thanks!

Write a script and name it as auto.sh
```

#!/bin/bash
compiz --replace&
```
Save it wherever you want.Put a "." infront of it {i.e. .auto.sh} to make it hidden to avoid from accidentally deleting it.

Then goto terminal and type:
```
cd /path to your script file
sudo chmod a+x .auto.sh
```

Go to system-> preferences->startup applications and add that script. Logout and Login and check.

---

### Post by plasm980 on 2009-07-06
> **Favux said:**
> Hi plasm980,

Have you checked in Configuration Editor (gconf editor) that in desktop>gnome>session>required_components that the value for windowmanager is compiz?

Worked like a dream.  Ubuntu now uses compiz after reboot or relogin.  Thanks!

Does anyone know why I'm getting the missing chunks of text in my gvim windows while using compiz but not metacity?  It just randomly displays the black background without the text for a few lines every now and then.  If I move the window around the screen, the text magically appears.  Also, if I move the cursor over the missing text using the arrow keys, the text appears where the cursor has gone, creating a "bread crumb" trail on the screen.  Thanks for your help!

---

### Post by Mayfairy on 2009-07-06
> **plasm980 said:**
> Worked like a dream.  Ubuntu now uses compiz after reboot or relogin.  Thanks!

Does anyone know why I'm getting the missing chunks of text in my gvim windows while using compiz but not metacity?  It just randomly displays the black background without the text for a few lines every now and then.  If I move the window around the screen, the text magically appears.  Also, if I move the cursor over the missing text using the arrow keys, the text appears where the cursor has gone, creating a "bread crumb" trail on the screen.  Thanks for your help!
I'm not sure if it's the same but I got a lot of visual artifacts when I used 180 drivers. Everything got better when I installed 185 drivers instead.

---

