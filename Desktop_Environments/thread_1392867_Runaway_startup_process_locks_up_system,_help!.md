---
title: "Runaway startup process locks up system, help!"
date: 2010-01-28
forum: Desktop Environments
---

### Post by watchpocket on 2010-01-28
As of last night, when I boot up, a gnome-terminal opens, then another and another, ad infinitum.

This just continues, creating more and more and smaller and smaller icons along the bottom panel.  The system locks up and the runaway process continues til I shut down.

How can I stop this from happening as soon as I log on?  I tried hitting COMMAND-Q a bunch of times to no avail.

(What's happening is that I put "Terminal" in the startup items, and for its command I put to launch a script that opens 7 terminals, but once terminals start to be opened, this doesn't stop.)

I'm running 64-bit karmic on a system76 Wild Dog desktop unit.

---

### Post by eltonw on 2010-01-28
Suggestion: REMOVE the terminal from your startup items. It's clear that by having it start up with the system, you have put into an (infinite) loop. Why, If I may ask do you want or need the terminal to start at bootup anyway? :confused:
Since you cannot shut it down properly, by doing a dirty shutdown, you are actually compounding the problem.

HTH,:-|

---

### Post by Robster2 on 2010-01-28
If you want a Terminal quickly can I suggest that you link the terminal to a short cut key.  I always set up F12 to call up the terminal.

System>Preferences>Keyboard Shortcuts.

---

### Post by Megafag on 2010-01-28
> **Robster2 said:**
> If you want a Terminal quickly can I suggest that you link the terminal to a short cut key.  I always set up F12 to call up the terminal.

System>Preferences>Keyboard Shortcuts.

I have a terminal on my desktop :P
its very snazzy.

However i suggest you should follow this advice OP

---

