---
title: "How to classify annoying UI bug that freezes the system"
date: 2021-08-26
forum: Desktop Environments
---

### Post by spidermatt on 2021-08-26
So I'm really not sure if this is a general Ubuntu level bug with Xorg, an issue with Gnome 3 on Ubuntu, or more specifically, an issue with the DisplayLink driver (although unlikely).

I have fresh install of Ubuntu 20.04 desktop on a Dell Latitude Rugged 5420, encrypted LVM configuration, with Gnome 3 bare metal as well as a few Gnome addons (most of which have been disabled for process of elimination). I have the latest DisplayLink drivers and am running a Targus quad-port docking station connected via USB C port. I am running four identical video outputs on the Targus. The issue I have found can be triggered regardless of whether or not my built-in laptop display is on/open. When triggered, my video output freezes, none of my input appears to be responsive which includes both external keyboard connected via Targus and internal keyboard. I can not switch to any of my TTY terminals or seemingly get the system to shutdown from CTRL + ALT_L + DEL key combinations either. One would assume the system is froze at this point but oddly, if I have music or a video playing, the audio keeps functioning (which is also connected via the Targus). To remedy the situation, I have to hard kill the power using the power button and then cold boot.

Triggering the problem is the easy part. All I have to do is move my mouse pointer to the position on the screen where my four monitors intersect in a 2 X 2 pattern. Again, this is still true even with my internal laptop display activated which is configured to the lower left of the 2 X 2 grid. Given that I have a lot of work to do and I have already suffered great setbacks from this problem in recent days, I do not have time right now to determine exactly what the pixel buffer to this life ruining dead zone which I can not cross with my virtual dagger. Reboots take a bit with my work environment so now I at least can avoid it a little better.

Any help on where I should post this bug would be great because I really don't understand enough to say which of these systems would likely be responsible for this type of issue.

Thank you in advance!

---

### Post by TheFu on 2021-08-28
Eliminate odd things first.  Start with displaylink.  [https://www.displaylink.org/forum/showthread.php?t=67148](https://www.displaylink.org/forum/showthread.php?t=67148)

---

### Post by spidermatt on 2021-08-30
While I appreciate that advice (which I've already done as much as I can) it is unhelpful here. The very basis of the problem is that it exists only in this multiple monitor setup which I can only achieve on this particular machine by using DisplayLink. I only have one HDMI output so I can not recreate a quad monitor setup with that obviously.

---

