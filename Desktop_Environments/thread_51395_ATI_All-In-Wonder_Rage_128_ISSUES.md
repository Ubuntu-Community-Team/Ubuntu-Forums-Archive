---
title: "ATI All-In-Wonder Rage 128 ISSUES"
date: 2005-07-23
forum: Desktop Environments
---

### Post by UbuNubee on 2005-07-23
I can't go above 640x480  60hz.  Can anyone tell me how to fix this? Thank you!!!

btw I'm new to Linux and this is the first distribution that I've attempted so please be nice  :razz:

Found on my own.. thanks for Naught ;0

---

### Post by luv2cmwork on 2005-07-26
Wonder if you could post your find?  Looking for same answer.

Thanks!

---

### Post by Mr Frosti on 2005-07-26
I am sure that this issue is easily fixable, however I don't know how to easily instruct the changes that are needed. 

A good starting point would be to check out your xorg.conf file. Before we make any changes, you want to backup the file by running the following command:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
``` 

Once the backup is made, you can open the file for editing by running this command:

```
sudo gedit /etc/X11/xorg.conf
``` 

look for the section that looks similar to:

"Section "Device"
        Identifier      "ATI All-In-Wonder Rage 128" (something close to this)
        Driver          "####"
        BusID           "PCI:1:0:0"
EndSection"

This is the part of the file that will deal with your video card configuration. Check the driver that it is using. If it says "vesa", try replacing this with "ati".

Next, look at the section that looks similar to:

"SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection"

There will be several section below this that are similar, except the "Depth" value will increment. You probably have depths of "1, 4, 8" etc. For each of these sections, add to the modes the maximum resolution that your monitor can handle. For example, if I wanted to add "1600x1200" to the above section, it would look like this:

"SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection"

You can test to see if this fixes your resolution problem by pressing Ctl + Alt + Backspace to restart the X server (your GUI).

++ IMPORTANT ++
If Gnome does not come back up properly, you will need to go to virtual terminal 1 by pressing "Ctl + Alt + 1" and logging in to modify this file again. Gedit will not be available, and you will need to restore the old xorg.conf file by running the command:

```
sudo mv /etc/X11/xorg.bak /etc/X11/xorg.conf
```

---

### Post by apps4apps on 2005-10-19
I was having the same 640x480 only issue with an ATI Rage128 AGP card here too and had a look at the config file. 

Surprisingly when I did,  I found that many other resolutions were already listed but they weren't showing up for selection in the GUI. To get other resolutions to show up, I deleted all resolutions except 1280x1024" "1024x768" "800x600" for all depths, saved the file, then hit <Ctrl><Alt><Backspace> to restart X. Again I ended up in 640x480 but this time I had many other resolutions available for selection. *More* than were entered in the file. When I checked the file again, depths 4 and 8 had 640x480 added and depth 24 had the following: "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480". If that's not buggy enough... The GUI (System->Preferences->Screen Resolution) now has the following listed: 1280x1024, 1024x768, 832x624, 800x600, 640x480, 1280x960, 1280x800, 1152x864, 1280x768, 1152x768 (in that order from top to bottom). I'm happy that I can now run in 1280x1024 but... Any thoughts anyone?...

The video card shows up as: > 	Identifier	"ATI Technologies, Inc. Rage 128 PF/PRO (AGP TMDS)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
and this is in version 5.04 for Intel x86

---

