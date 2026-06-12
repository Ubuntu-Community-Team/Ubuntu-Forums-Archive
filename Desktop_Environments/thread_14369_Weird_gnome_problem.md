---
title: "Weird gnome problem"
date: 2005-02-06
forum: Desktop Environments
---

### Post by lyeinyoureye on 2005-02-06
When I log into gnome, I get eleven sequential (I close one at a time) popups telling me 
**Error** 
[I]I've detected a panel already running,
and will now exit.[/I] 
I've tried reinstalling gnome, but it's still an issue. Any ideas?

---

### Post by rufius on 2005-02-06
Try removing a file called ".ICEauthority". It's own by root and you'll have to do a "sudo rm .ICEauthority" to remove it but that could possibly fix it.

---

### Post by lyeinyoureye on 2005-02-07
Well, that was already gone (I had the login problem after k3b), however, I reinstalled, got the exact same problem, then started up gnome w/o any scripts and I've been fine ever since....
it's weird, but whatever works!
Thanks for the help btw! :D

---

### Post by lyeinyoureye on 2005-02-07
Ok, now it's doing it again... but only when I change wallpapers?
 #-o 
??

---

### Post by JackDog on 2005-02-07
I have seen this problem before in hoary (5 weeks ago) however I dont know of a permanent solution. To get you logged in though, just pop out to a console and do a killall gnome-panel. For some strange reason, Gnome allows this process to stay active even after the DE shots down. Logically, gnome would kill all its kids to ensure everything is cleaned up. This could be a problem with gnome-panel though where its ignoring kill commands too.

---

### Post by rosslaird on 2005-02-07
I also had this problem, soon after a fresh install. The killall option probably works best, but a reboot will also do it (I know, Linux users are never supposed to reboot, but it does fix a few nasty problems at times).

One common issue with this kind of thing is the gnome session manager, (Desktop, Preference, Sessions) which sometimes saves the wrong things, or duplicates of things (e.g. with the mail-notification app), between logins. The gnome panel is not listed in the session manager (though you can kill it from there, under Current Session), so it won't help with this exact problem, but many login issues can be traced back to the session manager.

---

### Post by WW on 2005-02-12
I think the something similar just happened to me (running warty).

The first sympton that I noticed that suggested something was amiss is that I had just played a DVD with ogle, and when I had put the DVD in the drive, I didn't get the usual desktop icon and popup window.

After playing the DVD, nothing would appear when I tried selecting Computer->Home, Desktop, Disks, or Network.  I tried to Log out but nothing happened with that, either.  In a terminal, I took a look at what was running, and saw many instances of nautilus.  I tried 'killall nautilus', and then stuff started happening, including the "Logout" windows popping up (I had clicked on it at least twice), and the messages about panels.

I don't recall exactly what I did, but I eventually logged out, and when I logged in again, all I got was the plain brown desktop (usually I have a background image), and the top and bottom panels were empty.  At this point I couldn't do anything with the gui, so I switched to one of the text consoles, logged in, and rebooted (arghhh).  I was then able to log in, and everything appears to be back to normal.

There are a few other reports of screwy behavior involving gnome-panel and/or nautilus in the forum.  A quick search for gnome-panel in bugzilla turned up more hits than I had time to search, so I don't know if something like this has already been reported.

---

