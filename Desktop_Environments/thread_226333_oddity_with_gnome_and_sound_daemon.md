---
title: "oddity with gnome and sound daemon"
date: 2006-07-31
forum: Desktop Environments
---

### Post by &amp;)ky#)^ on 2006-07-31
I'm working on a desktop system of Ubuntu Dapper amd64 that I've had little to no problems with.  I've made no major changes in the past 24 hours.  However, about ten minutes ago I had the strangest system anomaly.  I was shutting down for the night and I used the standard power down button in the top right corner of the screen.  Hit shut down just like normal.  However, my gnome session froze.  I couldn't do anything except move the mouse.  I tried going to the terminal with CTRL+ALT+F1 and I tried using the shutdown command, but I put the wrong flags on it, so it just logged me out, but then the system stopped responding to my keyboard.  WTF!?  So, I used the system's reset button and it started again without a problem.  I told Ubuntu to Restart and it did so, but then I had some weird messages in my .xsession-errors file about the sound daemon trying to restart or something but a previous and stale UNIX daemon was already running or left running or something.  Sorry.  I was starting to get a little panicked.  Everything is working alright now.  What happened?  Has this happened to anyone else?  Could I have some virus or worm?

---

### Post by &amp;)ky#)^ on 2006-07-31
Okay, I did a full scan of my system with ClamAV and I'm relieved to report that my system is clean.  My question remains, what would cause these strange happenings on my system.  I think that the odd message in .xsession-errors may have been because I starting using XMMS way before the Ubuntu boot-up/log-in sound had finished playing.  So, what about this gnome/x glitch?  What could have caused this?  I believe it was a gnome problem because it eventually acted like gnome had stopped.  Kind of like if you run a GTK program without Gnome going and it's the window without a border and heading.  It kind of looked like that.  And there was no kernel panic or anything.  It just kinda froze or something.  Any ideas?

---

