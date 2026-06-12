---
title: "Synaptic crashing when resolving dependencies"
date: 2005-01-07
forum: Desktop Environments
---

### Post by Drek on 2005-01-07
Hey there.  I did some searching but I couldn't necessarily find anything that matches what's been going on with my system.

I've been running Warty for a couple of months now (and absolutely love it).  For the last couple of weeks, anytime I'm running Synaptic and pick a package that has dependencies, as soon as I tell Synaptic to select the dependencies it crashes with no message, no error - just bang, back to desktop.  Everything else seems to work fine, just this one thing kills the program.

I've tried running Synaptic from a command line to see if I'd get any sort of error messages, but nothing - I just get right back to the shell prompt.  I've also tried forcing a reinstall of the program using apt-get but it didn't fix the problem.  I can't think of anything I've installed that would cause this - anything I didn't grab directly from apt-get I've installed in my /home directory.  And finally, the ONLY Hoary packages I've installed are for Firefox 1.0 - and this problem occurred at least a month after that.

It's not a major issue being that I can always use apt-get to get the stuff I want but it is a bit annoying.  Anyone have any ideas as for what to look for or how to fix it?

---

### Post by Drek on 2005-01-10
A hopeful bump 'cause only 14 people looked at it.  :rolleyes:

---

### Post by wallijonn on 2005-01-10
maybe clean out /var/cache/apt ?

Actually, you never want to do that, you never want to just delete system stuff. It would be better to create a /home/directory and mv all the files over or move it to another part of /var.

---

