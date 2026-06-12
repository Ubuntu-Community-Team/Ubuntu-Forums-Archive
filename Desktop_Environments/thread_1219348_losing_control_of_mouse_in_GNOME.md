---
title: "losing control of mouse in GNOME"
date: 2009-07-21
forum: Desktop Environments
---

### Post by aeron-x on 2009-07-21
I'm having some issues with my mouse in GNOME, certain elements (namely the main menu in the top panel and much of the chrome in firefox, and other random controls) seem to "break" my mouse after trying to click on them. The click doesnt register properly and my mouse focus locks. For instance, if I click the sound mixer icon, the volume bar shows, but if I try to change the slider, the click event is sent to the panel icon, making the mini-form disappear. All subsequent clicks are sent back to the sound icon until I somehow break its focus. The pointer responds (moves and changes, etc.) but I can't click anything on the screen.

One fix that sometimes works is launching the terminal with alt-f2 and clicking its icon in the top left. That menu (sometimes) fixes the problem, but sometimes it doesn't and I have to reset completely just to use the mouse again.

These symptoms started after resetting my gnome panels back to their defaults. (Normally you'd think that'd FIX a problem like this, but nope. It started it)

Any help?


EDIT:
I solved it by completely resetting my gnome configuration. Works well enough for me :)

---

### Post by cb2410 on 2009-07-21
Hi there,  I had the same problem. 

Make this:

Restart and run recovery mode; Fix package AND X-Server

This helped me and its done in just 2 minutes.
Let me know if this helped


:popcorn:

---

