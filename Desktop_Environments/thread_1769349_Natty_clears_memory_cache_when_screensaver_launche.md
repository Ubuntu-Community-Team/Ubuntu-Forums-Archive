---
title: "Natty clears memory cache when screensaver launches"
date: 2011-05-27
forum: Desktop Environments
---

### Post by glennric on 2011-05-27
It seems that something is causing the memory cache to be cleared when the screensaver launches.  Then when moving the mouse or hitting a key to stop the screensaver it takes forever for the already launched and minimized applications to redisplay.  I am using the ubuntu classic desktop.  Any ideas on what could be causing this, or how to fix it?

Now time to rant.

Natty has so many bugs it is impossible to work around them all.  This memory issue is one of the worst.  The dead zone caused by the static application switcher, and the application switcher plugins for compiz (and probably any override redirect window) is another big one.  There is not a single window decorator for compiz that works right.  I have encountered two packages with binaries that won't even run (emerald and xpdf).  The nvidia drivers seem to have issues (this may be related to this memory clearing issue).

Without a doubt more bugs than any other release of Ubuntu to date.  I have worked around most of them by recompiling, and etc., but this is a real pain.

This is all aside from the idiotic switch to unity, when it is clearly not ready for release.  The general direction of Ubuntu is really starting to look bad.  By the way, what is up with the decision to uglify the desktop with gray scale icons (I know this is an old one, but I haven't really ranted on Ubuntu yet).

Looks like I will have to revert to Maverick.

---

### Post by kostkon on 2011-05-27
> **glennric said:**
> It seems that something is causing the memory cache to be cleared when the screensaver launches.  Then when moving the mouse or hitting a key to stop the screensaver it takes forever for the already launched and minimized applications to redisplay.  I am using the ubuntu classic desktop.  Any ideas on what could be causing this, or how to fix it?
Are you sure that your system doesn't go into suspend (or hibernate) mode (instead of just activating the screensaver)?
> **glennric said:**
> Now time to rant.

Natty has so many bugs it is impossible to work around them all.  This memory issue is one of the worst.  The dead zone caused by the static application switcher, and the application switcher plugins for compiz (and probably any override redirect window) is another big one.  There is not a single window decorator for compiz that works right.  I have encountered two packages with binaries that won't even run (emerald and xpdf).  The nvidia drivers seem to have issues (this may be related to this memory clearing issue).

Without a doubt more bugs than any other release of Ubuntu to date.  I have worked around most of them by recompiling, and etc., but this is a real pain.

This is all aside from the idiotic switch to unity, when it is clearly not ready for release.  The general direction of Ubuntu is really starting to look bad.  By the way, what is up with the decision to uglify the desktop with gray scale icons (I know this is an old one, but I haven't really ranted on Ubuntu yet).

Looks like I will have to revert to Maverick.
No such bugs here :neutral:

---

### Post by glennric on 2011-05-27
The computer does eventually suspend, but this happens before that.  Even if the computer did suspend the cache should not be cleared.  You are completely missing the point.  It is the activation of the screensaver that is causing the cache clearing.

As to the bugs I listed.  Look around.  Do a little Google searching.  They are confirmed bugs for Natty.  Whether you are affected by them or not is beside the point.  Look, I know what I am talking about when it comes to computers.  I could delve into the code and find and fix many of the bugs I listed if I had that kind of time.  However, my time is devoted to developing other applications.  Not to mention my real job.

---

### Post by glennric on 2011-05-28
I have discovered that this doesn't happen with all screen savers.  In fact the only screen saver that I can verify that this happens with is the GLText screen saver, although there may be other OpenGL screen savers that cause this.  I have also noticed that on another computer this screen saver causes a complete lock up instead of just causing the memory flush on this computer.  A third computer seems to be unaffected by this issue.  The affected computers both have nvidia graphics cards, and the unaffected computer has an intel graphics chip.

---

### Post by glennric on 2011-05-28
Apparently a bug has already been filed on this (bug #768032 in Launchpad).  So I will just have to await the upgrade.  Unfortunately, as these things go, it will probably not be until the release of Ocelot.

---

