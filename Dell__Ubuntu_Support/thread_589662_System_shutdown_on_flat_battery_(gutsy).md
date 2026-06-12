---
title: "System shutdown on flat battery (gutsy)"
date: 2007-10-24
forum: Dell  Ubuntu Support
---

### Post by macbuff on 2007-10-24
On Feisty my system (a Dell Latitude D610) would give several warnings when the battery was running low and finally would do a system shutdown in a tidy manner.

Since updating to Gutsy, the system doesn't prompt any more and just stops when the battery goes flat.

J

---

### Post by bluedragon436 on 2007-10-26
Have also had this issue come up....not sure what is up with that...I even went in to the power manager and changed it to warn me...but no such luck...it sometimes gives me one warning an by the time I can run to the outlet to plug it in it is shut down....I have tried to change the interval at which it warns me...and it still waits to the same point and then warns me...so I have to keep up with it myself....which is a pain...if anyone knows how to remedy this it would be greatly appreciated!!!

---

### Post by macbuff on 2007-10-27
At first I thought the problem was with the battery which is getting on a bit and only keeps around 50% of its charge.  But the same problem occurs with a virtually new battery. 

The Feisty system used to do a final popup to say that the syatem was about to be closed down and then it would perform a tidy shutdown.  After the shutdown the battery did have some life left to run memtest for a couple of minutes.

On Gutsy I get a couple of warnings and the system carries on until the battery (either one) is completely draned and then the system just stops.

J

---

### Post by bluedragon436 on 2007-10-28
Yeah mine gives me a warning around 19mins. left then if I don't manage to get it plugged in within a few minutes it just cuts off, no shut down no niceness to it...just off

---

### Post by moschops on 2007-10-29
Having the same problem here with my Dell Inspiron 700m.  It used to give good low battery warnings and then auto-hibernate as selected by the power manager.

Since a clean install of Gutsy it now gives warnings but does not hibernate - the battery shows 1% or 0% for another 10 to 20 minutes and then it dies when the power dies.  During that final time the laptop battery warning is flashing so it looks like the BIOS knows the battery is about to conk out...

Looking at /var/log/acpi.log I don't see any /etc/acpi commands executed at all before the battery dies.  But if I press the power button it successfully hibernates and resumes again as I configured (had to fix the video drive back to i810 first).

In /etc/default/acpi-support I have HIBERNATE_MODE=shutdown - not sure if that should be 'platform' or if that is releavent at all - the fact that nothing is logged leads me to suspect it is something else.

Other ACPI events like closing the lid and going into battery power save mode plus diming display when power is unplugged are working fine...

---

### Post by bluedragon436 on 2007-10-30
Hey at least you get some sort of warning other than just @ the 19min. mark...after that I get no other warning other than shutdown....  and I have tried to change about every option I can think of thus far...am thinking of completely re-installing it just to make sure I didn't miss anything...

---

### Post by app on 2007-11-01
With my Latitude D620 and Gutsy on a fresh modular bay hard disk I get no battery low warnings, and no scheduled shutdown, just abrupt power-off. I do get info about plugging the AC adapter in, so SOME power management messages on the dbus do work. Tinkering with Prefef / Power og gconf-editor /apps/gnome-power-manager does not help.

---

### Post by raxso on 2007-11-02
Mine does not give me any warning unlike feisty it give a warning before it dies. I also noticed that the battery wasn't working well on gutsy. Im using inspiron 6400 just 6 months old and usually on feisty when it is fully charged it gives me more than 2 hours used before i plugged it in to a power outlet and i noticed that the screen is dark when using battery unlike in feisty screen is good even running on batteries. any fixed on this.

---

### Post by Linicks on 2007-11-02
> **raxso said:**
> i noticed that the screen is dark when using battery unlike in feisty screen is good even running on batteries. any fixed on this.

This is a 'gotcha'.

Go to 

System->Preferences->Power Management >TAB>Battery Power.

The 'dim display brightness' slider works in reverse - so set it at 20% if you want 80% brightness, 30% if you need 70% brightness, 0% for 100% brightness etc.

Nick

---

