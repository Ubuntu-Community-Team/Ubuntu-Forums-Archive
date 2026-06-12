---
title: "Lock Screen and Xscreensaver FAIL"
date: 2009-04-29
forum: Desktop Environments
---

### Post by rayde on 2009-04-29
Before I leave work at night, I often leave my progams and windows up, and just select Lock Screen.  My screensaver pops up and off I go. But for the past several days I've come into work and noticed that my Ubuntu 9.04 box is showing the following:

[LIST]
[*]screensaver in the background.
[*]firefox window open in the foreground (with Gmail open).
[*]Gnome's menus visible.
[/LIST]

When I move the mouse i cannot see the cursor.  When I type a key, the screensaver returns focus and I am asked to log in.  If that times out, I then return to the screensaver in the foreground.

This severely reduces the usefulness of the screen locking functions in Xwindows, since the screen that was open is on display on top of the screensaver.  I have a feeling that because I had Gmail open and it auto updates itself, perhaps it somehow gained focus.  This should not be possible though.

Can anybody suggest a solution that I may be missing, or does this sound like a bug?  Would this be a Firefox issue or an issue with Gnome?

---

### Post by g-clef on 2009-04-30
I'm seeing the same thing.  I just yesterday did an in-place upgrade from intrepid to jaunty, and the screensaver/window lock is not working properly.  

I suspect this is related to the indicator applet, but I can't reliably reproduce that right now (sometimes my screensaver dies a few seconds after I get a notification, sometimes not).

---

