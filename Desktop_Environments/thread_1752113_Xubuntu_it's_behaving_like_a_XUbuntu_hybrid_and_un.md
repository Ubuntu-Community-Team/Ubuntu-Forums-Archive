---
title: "Xubuntu it's behaving like a X/Ubuntu hybrid and unresponsive to settings manager?"
date: 2011-05-07
forum: Desktop Environments
---

### Post by Dáire Fagan on 2011-05-07
Although my panels and dock are still there and the same, several reboots ago my desktop background, and appearance of my desktop icons, fonts etc reverted back to as they were before I changed from Ubuntu to Xubuntu after upgrading the former to 11.04 about a week ago.

Please see the two attachments on how my desktop now looks.

As you can see from the first right clicking the desktop allows me to bring up my old Ubuntu/gnome desktop background manager, and it's the only way to change it.

In the second screenshot you can see that any changes I make to the Xfce settings manager are not applied.

---

### Post by teachop on 2011-05-08
Had some cross-polination between Ubuntu and Xubuntu myself, but not that variety.  I installed Ubuntu 11.04 and then the package xubuntu-desktop on top of that.

Make sure in Xfce that Nautilus is not set as your default file manager, I tried that, and it messed the desktop up after the first time I ran Nautilus.  It is OK to use it, but I had to leave Thunar as the default.

If you have trouble with overlay scrollbars showing up in some of the gnome applications, that can be turned off.

I had some issues with screen saver and power manager conflicts between the two also, but pretty much just started disabling stuff until it was working.  In the end, I reconciled with Unity, decided I like it, and am not using Xubuntu on my main machines...  Sorry I cannot help more.

---

### Post by Dáire Fagan on 2011-05-09
> **teachop said:**
> Make sure in Xfce that Nautilus is not set as your default file manager, I tried that, and it messed the desktop up after the first time I ran Nautilus.  It is OK to use it, but I had to leave Thunar as the default.

I found that Nautilus was making the desktop behave differently than it did when I first changed to Xubuntu, and different than the Xubuntu Live CD so I removed it and set the file manager to Thunar. 

Is Thunar the default? Because it still seems different than the Live CD and how my desktop was when I first install Xubuntu, and now when I right click on the desktop nothing happens at all!

I since did a fresh install but things are just the same so it seems some settings are being picked up from my home partition.

Thunar doesn't even have a navigation bar in it to go back, up to parent directory etc, I shall look through the settings to see if I can remedy this. If Thunar really is the default File manager why does it look so different and why when I right click my desktop does nothing happen?

Standby for screen shot.

> **teachop said:**
> If you have trouble with overlay scrollbars showing up in some of the gnome applications, that can be turned off.

Yeah, I've had some errors referencing gnome, and VLC's option to disable the screensaver although checked is not working which may or may not be related.

Oh also, things that I know are on my desktop because I can access them through Thunar when I go into the desktop directory but they do not appear on the actual desktop.

---

### Post by ManualSparrow on 2011-05-10
I think this is to do with Nautilus - you may need to make sure it isn't drawing to the desktop using gconf or something. EDIT: but you removed it, so it must be something else. Try ```
xfwm4 --replace
``` in the terminal and see what happens (should restart the window manager). If necessary add that command to the startup applications list.
Also some docks (Cairo Dock especially) didn't work at all with XFCE as I recall. Check your startup applications and make sure they don't include things from Gnome.

Also Settings>Desktop>Icons has three options on what you display - selecting None lets you have the full-blown apps menu.

---

### Post by Dáire Fagan on 2011-05-11
> **ManualSparrow said:**
> I think this is to do with Nautilus - you may need to make sure it isn't drawing to the desktop using gconf or something. EDIT: but you removed it, so it must be something else. Try ```
xfwm4 --replace
``` in the terminal and see what happens (should restart the window manager). If necessary add that command to the startup applications list.
Also some docks (Cairo Dock especially) didn't work at all with XFCE as I recall. Check your startup applications and make sure they don't include things from Gnome.

Also Settings>Desktop>Icons has three options on what you display - selecting None lets you have the full-blown apps menu.

Thanks for your input, I've reinstalled and right clicking now gives a menu and icons are visible on desktop etc.

---

