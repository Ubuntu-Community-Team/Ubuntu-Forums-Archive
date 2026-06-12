---
title: "Trying to get panel working in Openbox"
date: 2006-02-18
forum: Desktop Environments
---

### Post by garren on 2006-02-18
I have been trying to mess around with various windows managers, and right now I'm trying to figure out Openbox.  This all happened partially because I seem to have, like, totally uninstalled Metasticy (is that right?) or something.  Basically, I was trying to find an alternative, and accidentally broke it--so when I try to login to Failsafe Gnome, it says it doesn't work and then it gives me a blank brown screen with a terminal imbedded into the desktop.  

But this is no big deal to me if I can get Openbox working.  

Here is something I've discovered: if I open a "terminal emulator" from Openbox's right click menu, and then enter "xfce4-panel" and hit return, a panel starts up on the bottom of the screen.  However, the terminal then stays "focused" on running that panel.  By this I mean that the curser moves to the next line, but it doesn't say "[user]@ubuntu:~$" and nothing I type in does anything.  So I have to open another terminal if I want to do anything else in a terminal.  And by "focused" I also mean that when I close that terminal, the xcfe panel that I started through it closes as well.  

This, obviously, is very problematic.  How do I get the panel to just start without relying on an open terminal.  And how do I get the panel to be open next time--I have heard something about "saving the session."  I assume that once I get the panel open properly that will work, but how do I save the session.  

One more thing--when I minimize windows, I assume they go to a taskbar somewhere, but I don't seem to have a taskbar.  How do I get one?  Xfce doesn't seem to come with one.  

Thanks

---

### Post by Wallakoala on 2006-02-18
Ok, well I can sort of help you. If you do ```
xfce4-panel &
```(notice the "&") it will make the panel run in the background, but if you close the terminal, the panel will close. I know in gnome you can press alt+f2 and you get a run dialog, which would be handy in this situation. If anyone knows how to get a run dialog in openbox, then it would help a lot.

---

### Post by moore.bryan on 2006-10-19
*for openbox, i prefer pypanel... but that's really a personal preference.  you can create an "autostart" script for openbox in which you specify it to start the panel and then exec openbox... is that what you're looking for?*

---

### Post by K.Mandla on 2006-10-20
I used pypanel for a while, then decided to take the plunge and go panelless. I actually like it a lot better ... but to each his own.

---

