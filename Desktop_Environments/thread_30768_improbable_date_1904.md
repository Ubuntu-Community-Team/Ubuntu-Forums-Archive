---
title: "improbable? date 1904"
date: 2005-04-30
forum: Desktop Environments
---

### Post by chele on 2005-04-30
I've had a machine (PPC powerbook 550) revert to a wrong date, with the result that the Gnome Panel & Nautilus refuse to start.

I was able to use the date command to inform the system of a reasonable current date, and everything is now normal.

The problem is that the machine is normally in the hands of a normal person, not a geek like myself. How can I ensure that, in the future, if the system date gets screwed, due to user error, or hardware error, or whatever, that the gui, Gnome, will still run? 

Perhaps a way to make sure that the date is always 04.2005 or later? (since that is when this distribution was distributed) Or what? Even a popup which says: hey, I doubt it is really 1904, please enter the current date and time...

Of course, part of the issue, I guess, is that this is a system without a full-time Internet connection, and even when it is connected, it is a a weird, round-about way. (dialup via remote wireless router) Normal, bootup NTP does not compute....

I am wondering if this would happen when the machine was not shutdown smoothly, or when the battery runs out of juice.

any feedback muchly appreciatted :-)

---

### Post by chele on 2005-04-30
Is there some package other then NTP that might work around this?

---

### Post by ssam on 2005-04-30
this happens to macs when they get to between 5 and 10 years old. the battery that runs the internal clock runs out.

you'll need to get a new battery from somewhere (or leaving the machine always plugged in works on an old imac of mine)

there is a small chance that it could just be a problem with the pram, holding alt+apple+p+r at boot untill you hear the chime twice, might help, but you probably need a new battery

---

### Post by chele on 2005-04-30
[QUOTE=ssam]this happens to macs when they get to between 5 and 10 years old. the battery that runs the internal clock runs out.

you'll need to get a new battery from somewhere (or leaving the machine always plugged in works on an old imac of mine)

there is a small chance that it could just be a problem with the pram, holding alt+apple+p+r at boot untill you hear the chime twice, might help, but you probably need a new battery[/QUOTE]

Is there a workaround until such time as a new pram battery can be installed? Is there a way to tell Gnome to just go ahead anyway, even though the date is wrong? 

Generally, this machine is plugged in all the time, and the main battery runs the machine for a couple hours.

---

### Post by ssam on 2005-10-11
this caught me out today. i should have known. very scary until i spotted complaint about the date in an apt-get reinstall (i was at the point of removing and reinstall gnome-components)

---

### Post by jdp on 2005-10-11
A new PRAM battery is surely in order as suggested.  To keep the date you should probably leave the machine powered on.  You might also try an AppleScript that sets the date to something reasonable before launching BootX, if it's way off.  I'm assuming you use BootX on the 550, as it's a NuBus machine, right?  That's quite an odd setup for Ubuntu.  I've got a 520c, but I wouldn't dare try Ubuntu without the PPC upgrade and a lot of RAM. :)

---

