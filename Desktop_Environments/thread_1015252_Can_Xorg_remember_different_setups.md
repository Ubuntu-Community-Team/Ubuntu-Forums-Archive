---
title: "Can Xorg remember different setups ?"
date: 2008-12-18
forum: Desktop Environments
---

### Post by Halfwalker on 2008-12-18
This is one feature that XP handles cleanly and unobtrusively, and I really would like to have it working with Ubuntu on my laptop ...

I have three main working environments ...

[LIST=1]
[*]Laptop alone - using laptop lcd at 1920x1200, sitting on couch.
[*]Laptop at home with 24" display.  I usually like having the screens cloned, since the laptop sits closed or off to one side.  I use a usb keyboard and mouse, working solely on the 24" Dell 1920x1200 monitor.
[*]Laptop at work with 22" display.  Here I usually have the laptop open below the 22" 1680x1050.  The displays are arranged appropriately as an extended desktop
[/LIST]
Now XP just does it all, no extra configs.  Turn on the laptop alone, and there's the desktop on the lcd.  Turn it on (or recover from hibernate) while plugged into the 24" at home, and the right config is active, the desktop on the 24".  Turn it on at work, and the desktop extends to use both laptop lcd and 22".  It just reads the monitor ID and configures accordingly.

I can't seem to get that functionality in Ubuntu/Xorg/Gnome.  I can save a config for ONE of them, but that's how it comes up every time after that.  I have to manually go into NVidia Xserver Settings to change things around to the config I want.

I can't be the only one doing this type of setup.  How have others got it working ?  Can it work ?  That is, will the HAL post a msg up the stack to identify that a particular monitor has just been plugged in, so xorg reconfigures itself ?

D.

---

### Post by C.S.Cameron on 2008-12-18
Using switchconf you can boot to multiple setups.
I use it to boot a flash drive on my laptop, my office PC with dual monitors and my entertainment PC with HDTV.
It is available from the repositories.

---

### Post by Halfwalker on 2009-01-14
> **C.S.Cameron said:**
> Using switchconf you can boot to multiple setups.
I use it to boot a flash drive on my laptop, my office PC with dual monitors and my entertainment PC with HDTV.
It is available from the repositories.
Yeah, but that's booting, or restarting the session.  While it works, it's clumsy.

Right now with XP, I can do this smoothly ...

I'm sitting at home working on the 24" monitor.  Hibernate the system, pick up and head into the office.  Plug it in there and wake it up.  It sees the office monitor, and configures itself appropriately, using a lower resolution for the monitor and changing to dual-screen.

End of the day, same deal - hibernate the system and head home.  Get home, sit on couch and wake system up.  It comes up cleanly, sees there's no monitor at all and just works in single-screen mode.

Then, while it's live, carry it to the 24", plug things in, and poof, it switches to using the 24".

The facilities to do all this are present in Ubuntu, it just doesn't seem to be done.  I would imagine it's going to be a set of scripts that get called based on hardware insertions etc.  Should work ...

This kind of smooth seamless transitioning is what we need to really rule on the laptop.

D.

---

