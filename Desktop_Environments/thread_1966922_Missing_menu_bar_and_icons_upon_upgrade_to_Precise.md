---
title: "Missing menu bar and icons upon upgrade to Precise"
date: 2012-04-27
forum: Desktop Environments
---

### Post by Datana on 2012-04-27
I just upgraded my installation of 11.10 to 12.04 yesterday, and I'm running into an issue where both GNOME-Classic and Unity are unusable for me.

Logging in looks and works normally.  On logging in, regardless of interface, the top menu bar is missing, as are all of my desktop icons and the launcher in Unity.  These are not hidden; there is no way to bring them back out, and there are no invisible but clickable panels, making me doubt this is a rendering issue.  I can right-click, call up display preferences, and get into the control panel that way, but can't call up a terminal without quitting X entirely.

The first thing I tried was killing and restarting X; no go.  I went ahead and reinstalled the Nvidia drivers after that, hoping that it's some strangeness with current drivers and 12.04; nothing changed there, as well.  Strangely, going to Unity 2D brings everything back, but this is more of a stopgap measure.

What else can I try to restore a usable desktop?

EDIT:
Solved the problem by killing X, going to the terminal, and then resetting all Compiz and Unity settings to default.  This surprises me, as I haven't changed any settings from default for most desktop elements (save for installing GNOME in the first place).

---

### Post by freefallcard on 2012-04-28
I'm having the same issue. a little green in ubuntu, can you tell me how got to terminal (did you do this in 2D?) and reset the defaults? Thanks.

---

### Post by rpk94 on 2012-04-29
Try Ctrl+Alt+T to open terminal and type unity --reset. Worked for me.

---

### Post by freefallcard on 2012-04-29
thanks, i'll give it a shot

---

### Post by elnetotaca on 2012-09-29
works on Ubuntu 12.04

what you have to do is;

open Ubuntu tweak
go to; tweaks

activate the first option "show desktop Icons"

and there you go!

---

