---
title: "Power Management"
date: 2007-06-16
forum: Desktop Environments
---

### Post by drberg1000 on 2007-06-16
I've had this laptop for nearly two years now and started using Ubuntu at the same time (Linux only since 2000).  I've still not gotten a power management scheme that works for me.  This is do largely to switching from one Desktop Environment to another trying to find the right one.

Can anyone suggest how I could get a setup that won't change if I switch from my current fvwm under KDM because my wife and son both currently use KDE.

What I'm looking for is something like this:

I'd like a system wide policy that sets default power down timeouts for the display, hard drive, network card, etc.  I'd also like it to hibernate after a system defined maximum idle time.  Default actions for the power and sleep buttons should also be set at a system level.  

The thought here being that I can bounce from gnome to kde to fvwm to enlightenment and onward without having to redo power management every time.

Ideally, then gnome-power-manager or the kde equivalents would be able to adjust these to more conservative values for individual users.  

Am I asking too much?

---

### Post by jimbo99 on 2007-06-17
I guess I must have it lucky.  I've simply asked that no power management at all be affected on my machine.  In other words, when I set it to "Never" I mean it should never do anything, ever.  Yet it still insists on turning off the output to my display.  I have a 24" lcd HD with numerous inputs.  Under windows when I say no power management it does NO power management.  Under Ubuntu when I say no power management it decides I'm wrong and does it anyway.

---

### Post by drberg1000 on 2007-06-18
Perhaps I can be more specific.  I think all I really want is a program/script that will decide when the system is idle and initiate a hibernate/suspend.  I don't want to depend on Gnome-power-manager, kpowersave or the like.  

Any suggestions on where I should look?  Google isn't helping me any.

---

### Post by ignignokt00 on 2007-06-19
> **jimbo99 said:**
> I guess I must have it lucky.  I've simply asked that no power management at all be affected on my machine.  In other words, when I set it to "Never" I mean it should never do anything, ever.  Yet it still insists on turning off the output to my display.  I have a 24" lcd HD with numerous inputs.  Under windows when I say no power management it does NO power management.  Under Ubuntu when I say no power management it decides I'm wrong and does it anyway.
Same here.  It makes it unbearable to watch movies, because I have to get up and jiggle the mouse every 10 minutes or so.

I just want to be able to turn off the monitor when I want it turned off.

---

### Post by starNIX on 2007-07-29
turn of acpi in xorg.conf

---

