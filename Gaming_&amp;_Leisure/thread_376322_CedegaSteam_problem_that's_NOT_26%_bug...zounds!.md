---
title: "Cedega/Steam problem that's NOT 26% bug...zounds!"
date: 2007-03-04
forum: Gaming &amp; Leisure
---

### Post by keithjr on 2007-03-04
Hello all,
Because I've gotten such great response from this forum, I'm going to start my communal troubleshooting efforts here.

**The Setup**
I'm attempting to run Steam (with the hope of playing Source mods) in Cedega.  Downloaded the latest SteamInstaller.exe, loaded it up with Cedega (and their GDDB settings for Steam-Source), and installed the program.

**The Problem**
After installation, Steam automatically updates.  When it hits the pivotal 26%, the window does close, but then it comes right back up and keeps going, all the way to 100%.  Then, it disappears and....nothing happens.  Confounded, I try to start Steam from Point2Play, and when I hit Play...nothing happens.  No console errors, nothing pops up.  

I need the help of the forums mostly because I am given no information as to why this program won't even start.  I've tried a few re-installs, and enabling/disable Pthreads.  No dice.

**Vital Stats**
Ubuntu 6.10 (Edgy)
Cedega Version 5.2.3 
Cedega Engine 5.2.7
Video Drivers: 2.1.0 NVIDIA 97.46 (dunno why this might be the problem but...)
I use Beryl but I HAVE disabled it for the purposes of these endeavors.  Yes, I've read the sticky.

If there is any other information that might be useful just ask and I'd be happy to provide it.  And, of course, thanks in advance.

---

### Post by keithjr on 2007-03-05
I just upgraded the Cedega engine to version 5.2.10, still does the same thing.

---

### Post by keithjr on 2007-03-05
**Problem Resolved!**

Well, I don't quite get it, but apparently it is important to re-install after turning off Beryl.  Also, upgrading the engine couldn't have hurt.  Either way... I did those two things and Steam now starts up.  *shrug* 

Sorry for the inconvenience.

---

### Post by chocomoojuice on 2007-03-12
> Well, I don't quite get it, but apparently it is important to re-install after turning off Beryl. Also, upgrading the engine couldn't have hurt. Either way... I did those two things and Steam now starts up. *shrug*

I have this exact same issue, except I don't use Beryl, and I'm relatively sure I've got the newest version of the engine...however now that I say that I'm questioning myself.  When I go to Help > About, it tells me in the About tab "TransGaming Cedega Version 5.2.3".  However, when I go to Edit > Global Settings, the Engine Version is 5.2.9.  Could this be the reason why it won't start...?  Help :confused: :confused: :confused:

---

### Post by chocomoojuice on 2007-03-12
Ok, turns out I wasn't using the newest version, and that was indeed the issue.  Hurray! (I believe the newest version is 5.2.10)

---

