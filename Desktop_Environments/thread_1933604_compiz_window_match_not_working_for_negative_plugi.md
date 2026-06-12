---
title: "compiz window match not working for negative plugin"
date: 2012-02-29
forum: Desktop Environments
---

### Post by drammock on 2012-02-29
I'm running 10.04 32bit with gnome2 and compiz.  Yesterday I set up a window matching parameter for the "negative" plugin in compiz (I think it's part of the extended "fusion" plugin set).  Here is the window match condition I used:
name=nautilus | (name=rkward & role=MainWindow#1) | (title=Zotero & role=browser) | title=<Student Version> MATLAB  7.10.0 (R2010a)
In other words, automatically invert colors on all nautilus windows, and on the main RKWard window, and on Zotero Standalone and Matlab.  This worked great during the session in which I set it up.  In each session since then, it is no longer working.  The plugin still works, in that I can manually invert colors on any window using a keyboard shortcut, and the window match condition for excluding certain windows from the "invert everything" command also still works:
type=Desktop | type=Dock
In other words, the keyboard shortcut that is supposed to invert everything correctly inverts everything *except* the desktop and dock.  All other aspects of compiz seem to be working normally.  I do have RegEx Matching plugin enabled.  I tried reducing the neg_match string to just "name=nautilus" to see if there was something about the way I was identifying the other windows that was causing it to choke, but even that doesn't work.  Any ideas what is going on?

---

### Post by Krytarik on 2012-02-29
Actually, the "Neg Windows" setting doesn't have *any* effect in my Lucid 10.04; plus, considering that the default setting for that is "any", that thing doesn't make sense at all! :P - as this would mean that *all* windows are color-inverted per default setting, and you are currently trying to except those windows you are actually trying to have color-inverted by default. :D And don't conclude now that it might work the other way around; I've also tried that. :P

Good luck with that!

---

### Post by drammock on 2012-02-29
I noticed before I started that the default was "any", which puzzled me a bit.  Regardless, when I first implemented the window match settings, they worked beautifully for the duration of one session, and were updating "on the fly" as I made changes...  for example, at first every rkward window was getting inverted colors (including graph windows) so I added in the "role=MainWindow#1" argument and the graph windows instantly flipped back to normal colors.  The point being, I know that it works in principle, and that something is getting in its way.  I just don't know what.

---

