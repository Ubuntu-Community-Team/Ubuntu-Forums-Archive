---
title: "Unable to alter some graphics settings"
date: 2008-07-21
forum: Desktop Environments
---

### Post by spitfire23bc on 2008-07-21
Hi all, I've managed to mess up some graphics settings in Ubuntu 8.04 and can't work out how to sort it out.

Currently, the computer doesn't remember what resolution the monitor is (so restarting X always requires me to manually change the resolution), font sizes are all over the shop, and I can't change the icon/menu theme from the Gnome theme.

It was working fine with Compiz until yesterday (when I started playing...), but Compiz won't run now (Checking for Xgl: not present.).

I've been reinstalling nvidia bits and pieces, reconfiguring xserver-xorg, all to no avail.

Any ideas, please? :confused:

Dan

---

### Post by overdrank on 2008-07-21
> **spitfire23bc said:**
> Hi all, I've managed to mess up some graphics settings in Ubuntu 8.04 and can't work out how to sort it out.

Currently, the computer doesn't remember what resolution the monitor is (so restarting X always requires me to manually change the resolution), font sizes are all over the shop, and I can't change the icon/menu theme from the Gnome theme.

It was working fine with Compiz until yesterday (when I started playing...), but Compiz won't run now (Checking for Xgl: not present.).

I've been reinstalling nvidia bits and pieces, reconfiguring xserver-xorg, all to no avail.

Any ideas, please? :confused:

Dan

HI and have you tried to boot into recovery mode and use the xfix option?
You may also try the command ```
gksu displayconfig-gtk
``` to set up the graphics

---

### Post by spitfire23bc on 2008-07-21
> **overdrank said:**
> HI and have you tried to boot into recovery mode and use the xfix option?

Hmm, I don't seem to be able to boot into recovery mode; it gets so far and then just stops, with the little blinking cursor...

> **overdrank said:**
> You may also try the command ```
gksu displayconfig-gtk
``` to set up the graphics

Yeah, that's what I'm using, only I have to do it every time I restart X.

---

### Post by overdrank on 2008-07-21
> **spitfire23bc said:**
> Hmm, I don't seem to be able to boot into recovery mode; it gets so far and then just stops, with the little blinking cursor...



Yeah, that's what I'm using, only I have to do it every time I restart X.

Ok what is the model of the graphics card? And you are unable to boot to recovery mode, are you sure you are choosing recovery mode from the grub?

---

### Post by spitfire23bc on 2008-07-21
> **overdrank said:**
> Ok what is the model of the graphics card? And you are unable to boot to recovery mode, are you sure you are choosing recovery mode from the grub?

It's a GeForce 8400

And yes, before the grub login screen loads, I drop into a menu and pick Recovery Mode

---

### Post by overdrank on 2008-07-21
> **spitfire23bc said:**
> It's a GeForce 8400

And yes, before the grub login screen loads, I drop into a menu and pick Recovery Mode

Ok then you may try what PmDematagoda suggested here
[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

---

### Post by spitfire23bc on 2008-07-21
> **overdrank said:**
> Ok then you may try what PmDematagoda suggested here
[http://ubuntuforums.org/showthread.php?t=864202](http://ubuntuforums.org/showthread.php?t=864202)

It doesn't seem to make a difference. 

I also now don't have anything listed in System>Administration>Hardware Drivers  although that's likely to be my own fault for messing around with things.

---

### Post by spitfire23bc on 2008-07-22
Ok, I've solved some of this, but not all...

Things that are working now: O:)
- NVidia driver
- Screen resolution
- Compiz


Things that aren't working: :-?
- Can't change the icon and menu theme (System>Preferences>Appearance>Customise>Icons)

- Bizarrely, although I can change the window borders, everything that *should* appear orange appears blue (System>Preferences>Appearance>Customise>Window Border)

- Various special/multimedia keybindings (Volume controls, search) no longer work


Any clues, anyone?

---

