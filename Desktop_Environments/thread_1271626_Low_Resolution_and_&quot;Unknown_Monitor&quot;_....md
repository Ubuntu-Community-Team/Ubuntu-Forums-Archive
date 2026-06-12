---
title: "Low Resolution and &quot;Unknown Monitor&quot; ..."
date: 2009-09-21
forum: Desktop Environments
---

### Post by Vik Vasilev on 2009-09-21
After my old monitor broke I had to switch to a 17 inch Siemens-Nixdorf monitor, which I think is kinda old(but looks great) and Ubuntu does not detect it at all. 
In the display settings it says its an **Unknown Monito**r and the supported resolution are not listed. I cant switch to anything higher then 1024x768 and 60hz.
 Is there any way I can force the settings? :confused:
I`m using the ATI radeon free drivers.(ATI made my videocard legacy hardware a few months ago).
 I tried editting xorg.conf but nothing changed.
One more day at 60hz and i`ll go blind -.-

---

### Post by realzippy on 2009-09-21
..1024x768@60 maybe is the limit an old 17" monitor can handle.
Check the monitor model in google first before forcing any higher resolution...

---

### Post by Vik Vasilev on 2009-09-21
It works at 1280x1024@85 ( the highest tested before i bought it ).  The settings are missing in "Display preferences"

---

### Post by UpsideDownFace on 2009-09-21
I too had trouble changing /etc/X11/xorg.conf.
I used "Applications > System Tools > Root Terminal" to run "gedit xorg.conf" and things reverted to what they were originally.
But I kept trying, and eventually copied xorg.conf to xorg.conf.new,
I then edited xorg.conf.new as root, and copied it back to xorg.conf.

There is a convoluted backup system for xorg.conf,  which I failed to understand, which seems to restore default settings.

An alternative to editing xorg.conf is to use "Startup Manager" which may be under "Applications > System Tools"
If you haven't got it, you can get it from "System > Administration > Synaptic Package Manager" search for "startup manager".

---

### Post by UpsideDownFace on 2009-09-21
Sorry, Startup manager is under "System > Administration"

An alternative I was thinking about is "Applications > System Tools > Configuration Editor" then  under something like "gnome > screen > default > 0" you will find "rate" and "resolution" settings you can overtype or edit.

I spent ages being frustrated, so I hope this helps.

---

### Post by Vik Vasilev on 2009-09-21
> **UpsideDownFace said:**
> Sorry, Startup manager is under "System > Administration"

An alternative I was thinking about is "Applications > System Tools > Configuration Editor" then  under something like "gnome > screen > default > 0" you will find "rate" and "resolution" settings you can overtype or edit.

I spent ages being frustrated, so I hope this helps.

Okay, thanks for the help. I have the Configuration Editor running now, but I cant  find "Gnome -> Screen -> ...." :confused:

---

### Post by UpsideDownFace on 2009-09-21
Unfortunately I don't know the exact location.
I have two linux computers and the configuration editor is different, even though I have tried to make the installations as close as possible to the same.

Both my Configuration Editors show
  /
    apps
    desktop
    schemas
    system

but one also has
    GNOME

I think you just have to search

One of mine has "/desktop/gnome/screen/Tadpole/0" with the rate/resolution
The other has "/desktop/gnome/screen/default/0-1"
     and also "/desktop/gnome/screen/Newt/0-1"
 Newt and Tadpole are computer names

So I'm sorry, you just have to search till you find rate/resolution in the right-hand panel of the Configuration Editor
Then change them and hope you got the correct one!

---

### Post by bobince on 2009-09-22
When the you get “Unknown monitor” it means the EDID data can't be read from the monitor. This happens to me due to a kernel bug, but it can also happen if you have a really old monitor from before EDID was commonplace. Unfortunately when this happens X makes *very* conservative default guesses as to how fast the monitor can run, resulting in today's common resolutions being unavailable.

You can fix this by adding a ‘HorizSync’ command to tell X the monitor can go much faster. xorg.conf hacking is a pain, but configurations that worked for me under Jaunty and Karmic are in [this thread](http://ubuntuforums.org/showthread.php?p=7910567).

---

### Post by Vik Vasilev on 2009-09-22
Thank you Bobince. I think the monitor does not support EDID. Last time i tried to edit xorg ubuntu started in low graphics.
 Will try the thread in the link.

---

### Post by LanceyD on 2009-11-03
any solution to this, i'm having the same problem.  nvidia 185 drivers, Ubuntu 9.10 (9.04 previously) and Belinea 19" CRT, monitor ran fine 85hz 1024*768 in Windows but no option in x server, just "auto" and "60hz"

---

### Post by TheProphetJonah on 2009-11-23
Ok, I've had the resolution up to 1280x1024x24 on this monitor with this card (Matrox Millennium AGP) and the monitor being a KDS-usa SVGA 17 inch.
I got that resolution using Puppy TeenPup 2009 Legacy.

I've used a similar setup on The Operating System Whose Name We Do Not Often Mention and gotten 3D graphics (Generic SVGA and the pci version of the same card) to use their Flight Simulator program which they've since discontinued. I can run that in wiNe anyway.

So I want to try out the FlightGear and Sabre simulators.

Problem, I HAVE to have the 3D rendering to get it. No 1280x1024 = No 3D.

The "discover monitor" button in the dialog box for configuring System>Preferences>Display gives me the Unknown Monitor display and that's all.

I'm running Ubuntu 9.10 on an i686, 512mb RAM and 800mHz processor, 120 gigabytes spread over two IDE and two SCSI drives. 1 gig of swap on each drive.

---

### Post by gatewayasteroid on 2009-11-23
> **Vik Vasilev said:**
> After my old monitor broke I had to switch to a 17 inch Siemens-Nixdorf monitor, which I think is kinda old(but looks great) and Ubuntu does not detect it at all. 
In the display settings it says its an **Unknown Monito**r and the supported resolution are not listed. I cant switch to anything higher then 1024x768 and 60hz.
 Is there any way I can force the settings? :confused:
I`m using the ATI radeon free drivers.(ATI made my videocard legacy hardware a few months ago).
 I tried editting xorg.conf but nothing changed.
One more day at 60hz and i`ll go blind -.-

I had the same with my 1366x768 LCD.

I generated a ModeLine with

```
gtf 1366 768 60
```

then I created a minimal xorg.conf

```

Section "Monitor"
	Identifier     "Monitor1"
Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795
EndSection

Section "Screen"
    Identifier  "Screen1"
    Monitor     "Monitor1"
    Subsection "Display"
        Modes "1368x768"
	EndSubsection
EndSection

```

---

