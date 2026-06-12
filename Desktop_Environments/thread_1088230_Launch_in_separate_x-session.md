---
title: "Launch in separate x-session"
date: 2009-03-05
forum: Desktop Environments
---

### Post by VeeDubb on 2009-03-05
I'm sure this has been posted before, but I can't seem to wade through the search results to find something useful, and the process has changed a great deal with the new xorg.conf files that are basically empty.

What I want to do, is launch a particular program in it's own x session with a different resolution.

To be specific, my monitor is a 1440x900 widescreen LCD, which is normally run at it's native resolution of 1440x900.

I want to launch a program, from a script on my desktop, in it's own seperate x server with resolution of 640x480.

All of the how-to's and tutorials I have found so far, are based on the old xorg.conf which explicitly listed everything.  These do NOT work with the new minimal xorg.conf.

So, I either need to reconfigure my xorg.conf to list everythign explicitly, or a way to launch a new x session from the console with a selected resolution.

I have already set up permissions to allow regular users to launch a new session, and created a simple script that launches the progam in it's own session.  I just need to know how to configure things so that the new session comes up in 640x480 without messing up my regular desktop.

Why?  This shouldn't make any difference, but if you really want to know......

I have a perfectly valid, legal, etc copy of Starcraft and the Broodwars expansion pack.  These games work flawlessly with wine or Cedega, EXCEPT that the resolution is fixed at 640x480, and can't even be changed with hacked registry entries.  It's hard-coded into the game.  If you're on a 4:3 monitor, it's not such a big deal, but it causes lot's of trouble on widescreen monitors.

---

