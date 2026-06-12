---
title: "Application windows - no title bar - can't move"
date: 2009-11-20
forum: Desktop Environments
---

### Post by DaveRowell on 2009-11-20
I'd like some help resolving this weirdness - please!

When I start ubuntu 9.10 this is what I get:
1 - normal appearing desktop on first workspace

2 - cannot change to another workplace either with [ctrl][alt][any arrow] or by clicking on switcher

3 - at this point any window opens in an abnormal state:
Windows open in upper left hand corner of screen covering the panel

Window title bar is missing = no window title = no "min" "max" "close" buttons = cannot move window either with mouse or with right click choice = no normal right click on the title bar responses = [alt]F4 won't close window

But the contents of the window seem to work OK - mail - internet ...

If the Show Desktop Button is pressed a window opens saying that either no Window Manager is loaded or that the Window Manager doesn't support the button.  Window Manager is Metacity as far as I know.

4 - System->Preferences->Appearance - [visual effects tab] shows no desktop effects selected even tho they were enabled at shut-down

Click Normal radio button - window opens "Searching for available drivers" - after the best part of a minute the display "changes" and a window opens asking if I want to keep these settings - choose "yes"
while everything now looks as it did - can change to other workspaces - switcher preferences allows selection of rows and columns - windows open next to the panel not on it - window title bars are normal - windows can be moved ...

5 - If proprietary nVidia driver is removed almost exactly the same things happen - only difference is that no desktop effects are allowed.

kernel 2.6.31-14 gnome 2.28.1 fresh install
AMD Athlon(tm) XP 3200+ - 1 GB RAM
nVidia GeForce2 MX/MX 400 NVIDIA Linux x86 Kernel Module 96.43.13 loaded driver thru KK menu choice after installation - this is driver currently recommended by nVidia
root partition ~14GB 27% used home partition ~95 GB 73% used

---

### Post by gettinoriginal on 2009-11-20
Since you are not sure what window manager is  running, you can do Alt F2 and type ```
metacity --replace
```, then reboot.

---

### Post by VCoolio on 2009-11-20
If the above solution doesn't stick to the next boot, then install fusion-icon. It's a tray icon that, when right clicked, allows you to choose window manager and decorator. It also remembers what you used (add it to your startup applications).

---

