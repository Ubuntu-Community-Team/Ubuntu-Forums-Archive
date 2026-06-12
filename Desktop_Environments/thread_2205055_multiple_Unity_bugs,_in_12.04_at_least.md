---
title: "multiple Unity bugs, in 12.04 at least"
date: 2014-02-11
forum: Desktop Environments
---

### Post by Daniel_Knight on 2014-02-11
I don't see anyone having mentioned this problem, which is strange, since it's very annoying: the unity icons sometimes blank, and I have to go to the dash thing to see if the program icon is there so i can drag it back, and sometimes it won't drag to where i wan't but will put it at the bottom. I noticed too that cancelled downloads result in ghost icons in Unity. I also noticed that the Wesnoth game icons gave me particular trouble, like after having moved them in via the dash when they failed to show after installation, including the map editor icon, that they AGAIN disappeared. I also noticed HTTrack blanked, and restarting did not reveal it again, I had to go to the dash section. Another annoyance, not a big perhaps, is that a few times Unity would not scroll up when I tried to place an icon upwards, and when it scrolls either way while having an icon grabbed to move it, it is SLOOOOOOW to move. It also seems to have overly fast speed problems when going to the top or bottom, it makes it hard to get to icons in between, it's like an overly sensitive mousepad that responds to every little thing, it's not smart, it's dumb. A few times dupligate icons got stuck on the border, I guess when my trackpad accidentally grabbed icons or trying to move them, though I noticed in Windows 7 this grabbing problem didn't exist, but so when grabbing the actual icon the duplicate would disappear.

---

### Post by buzzingrobot on 2014-02-11
> **Daniel_Knight said:**
> ...unity icons sometimes blank, and I have to go to the dash thing to see if the program icon is there so i can drag it back, and sometimes it won't drag to where i wan't but will put it at the bottom. 

Can you explain where these icons are located?  Or, where you would like them located?  Unity doesn't put icons on the desktop.  What does "sometimes blank" mean?  What icons does this affect?  Where do you drag an icon from the Launcher "back" to?


> ... the Wesnoth game icons gave me particular trouble, like after having moved them in via the dash when they failed to show after installation, including the map editor icon, that they AGAIN disappeared.

Applications have icons by virtue of their creation of corresponding ".desktop" files in /usr/share/applications.  Well-behaved programs should install their ".desktop" files there.  Programs that are not installed in conventional Ubuntu fashion -- say, via a tar.gz archive -- will not create the proper ".desktop" file and, hence, will appear to have no available icon.

---

### Post by ralph-beeby on 2014-02-13
I too am having problems since, I think, an update towards the beginning of this week. Unfortunately it's a different problem: the dash has stopped working! I've also noticed that the grey tags that name each program on the launcher have a red band on the launcher-side end - don't know if this is symptomatic of anything?

I managed to remedy this yesterday by entering
$ unity --reset
and rebooting the machine, but the problem has come back this morning. Any ideas?


(Oddly enough this has only affected my work computer, not my home computer! Key differences are that my home computer is running the 64-bit OS with the low-latency kernel, whilst my work computer is 32-bit and generic...but surely that shouldn't make much difference to the desktop environment?)

Update: turns out my problem was driver-related. Have removed the proprietary and am back on the open-source version, and now everything works the way it used to!

---

### Post by Frogs Hair on 2014-02-13
Video driver and hardware unless identical may be a factor as well . Wait and see if the reset command worked  after some use.

---

