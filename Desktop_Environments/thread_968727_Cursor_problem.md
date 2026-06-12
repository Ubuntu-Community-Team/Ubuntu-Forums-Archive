---
title: "Cursor problem"
date: 2008-11-02
forum: Desktop Environments
---

### Post by meatcar on 2008-11-02
I have searched in the forums, and on google, and have been unable to find anyone with my problem.

My cursor behaves normally most of the time, but when I attempt to use wine, or gimp, or any other GUI app that requires the cursor to change to something different (other than the text editing mode, or the hand, or the arrows), it turns into a black/white box, with the "tip" being the top-left corner.. Its really annoying if I'm trying to draw something.

I automatically blame any graphical misgivings onto my GFX card, but I do not see how that could relate to it. Could it be a missing dependency or a broken package?

Any help/advice/guidance would be appreciated...

I tried to take a screen shot, but the mouse isn't captured in it.

---

### Post by Corin-EU on 2008-11-05
I am noticing a similar problem and I have an ATI RV280 based ASUS 9250 AGP graphics card.

When the problem occurs, the cursor appears as a box with patterning dependent on the screen background.

The problem is independent of the window manager.

If no window manager is running, then the problem does not occur.

I have observed it with Metacity, Openbox, FVWM, XFCE but not Compiz or CTWM.

If the mouse is moved rapidly over a window title when the cursor problem occurs, it can be made to disappear.

Then moving the mouse slowly over a window title, the cursor problem tends to reappear.

I have also noticed that since the upgrade, that the X display shimmers, and that there are severe worry lines on simple cross hatch
backgrounds generated with

xsetroot -bg color1 -fg color2 -mod 2 2

This poor behavior was not present in Hardy Heron.

Is it all due to the change to the new version of the Xorg X server which perhaps does not provide a good as display appearance as the previous more stable version?

It goes without saying that I have been most disappointed by the presence of these basic faults in the new version of Ubuntu.

---

### Post by meatcar on 2008-12-28
I've upgraded my computer to Ibex, and the problem persisted. It seems to persist only when the cursor is forced to be rendered by something other than gtk. I believe it is a videocard problem, since it is not present when I view my display through VNC on my iphone or a friends computer, but mine  still shows teh black box with random scanlines. I have problems with compositing, where similar scanslines are present too. 

However, I have recently got a new laptop, and i have not tried whether the problem persists there too. I would glady try that now, but i am half a world away, so i will reply once i get back home.

Cheers,

---

### Post by Corin-EU on 2009-04-26
This problem is still present in Ubuntu 9.04.

Are we ever going to see it fixed?

---

