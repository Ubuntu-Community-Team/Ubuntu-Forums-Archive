---
title: "saved session no longer restores xterms' geometries"
date: 2017-03-10
forum: Desktop Environments
---

### Post by jim_osborn on 2017-03-10
After a routine apt->full-upgrade, I did my usual procedure of bringing all eight of my xterms to foreground, and, using the xfce4 settings mgr Session and Startup->Session->Clear saved sessions, then ...->Save Session, I clicked the Restart Action button on my panel to complete the upgrade.  This procedure has always restored all my xterms to their desktop geometries, sizes and locations, but this time I was left with eight xterms, all 40x80, on top of each other in a single location.  Is this a bug in some package in this latest "upgrade?"

I had been thinking of asking if someone knew of a way to save/restore the names of the xterms, to avoid my having to manually set them each reboot.  But that's a trivial problem compared to having to resize and relocate all of them.

Anyone have any ideas?

TIA, jimo

---

### Post by ajgreeny on 2017-03-10
I have never saved sessions in my Xubuntu installations so I am not sure if that is affecting your problem.
Which terminal do you use, xterm itself, or xfce4-terminal

For xfce4-terminal you can get the size you want by using the Edit-Preferences menu, Appearance tab or by editing the command used in launchers to
**xfce4-terminal --geometry 120x41** or whatever size you want.
For xterm it is
**xterm -geometry 120x41**

Window placement can be changed, though I have never used it, in the **Settings manager -> Window manager tweaks -> Placement tab**

Play with that to see if it helps.

---

### Post by Hakachukai on 2017-03-10
You can also use a boot up script using wmctrl to manipulate the windows if nothing else works

---

### Post by jim_osborn on 2017-03-10
Thanks, ajgreeny.  I'm using plain old xterm (/usr/bin/xterm), but I'll try xfce4-terminal and see if it acts differently.  I generally use five different sizes for my xterms, several the standard 40x80, some much smaller and one much larger, all with different placements, so a global size and/or placement setting would not help.  The ~/.cache/sessions/xfwm4-<nnn>.state file has geometry (and name) info, so perhaps there's a way to manipulate that file on the way down, or during bootup, and solve both my problems.

The fact that my session started with the correct number of xterms, as well as Qjackctl (placed correctly), implies that some of my session was, indeed, saved.

---

### Post by jim_osborn on 2017-03-10
Thanks, Hakachukai.  That looks like the tool I need.

---

