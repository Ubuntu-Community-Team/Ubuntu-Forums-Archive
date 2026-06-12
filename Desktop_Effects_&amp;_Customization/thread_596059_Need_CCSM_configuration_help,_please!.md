---
title: "Need CCSM configuration help, please!"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by rebbi on 2007-10-29
Hi,

There are two things I want to configure in CCSM using Gutsy, but I can't figure out how to do it.

1) In Beryl, you have a plugin (don't know what it's called) that lays out all your open windows in miniaturized form so you can select one of them; it looks just like Expose in Mac OS X. By default, it's activated by moving the cursor into the upper right corner of the screen. How can you enable this in Compiz?

2) I hate the effect where window edges are sticky and adhere to screen edges and the panels (especially with wobbly windows enabled -- ick!) #-o How do you turn the sticky edges effect off???

Thanks in advance!

SF

---

### Post by Zorael on 2007-10-29
1) Scale plugin. Action tab -> Initiate for all workspaces (or just current one) -> Screen Edge.

2a) Snapping Windows plugin. Uncheck stuff.
2b) Wobbly Windows plugin. Uncheck Snap Inverted.

2a and 2b are mutually exclusive, you can't have both running at the same time, so pick your poison.

---

### Post by DouglasAWh on 2007-10-29
This is very helpful, but mine still snaps to full screen when I move it toward the top.

And, I might start a new post, but I am having a problems with desks versus workspaces.  I know I fixed this in Feisty and I'm not sure why gutsy broke it...ugh!!!

---

### Post by Zorael on 2007-10-29
Snaps to fullscreen when you move it to the top? Hmm, weird, I haven't had that one.

Sounds like it should be something in Move Window, I know it does the opposite (restores maximized windows if moved from the edges).

As for desktops/workspaces/viewports, you'll want to start compiz with
```
$ compiz --replace --ignore-desktop-hints &
```
...which will help "a bit". I ended up disabling the applet in my KDE panel - Expo gives me a good overview when I want it.

---

### Post by DouglasAWh on 2007-10-29
I found "Snapoff Maximized Windows" and that fixed the irritating snapping.  

I am still utterly unable to find anything when  I move it within two workspaces.

---

### Post by rebbi on 2007-10-29
Oops, sorry.

---

### Post by rebbi on 2007-10-29
> **Zorael said:**
> 1) Scale plugin. Action tab -> Initiate for all workspaces (or just current one) -> Screen Edge.

2a) Snapping Windows plugin. Uncheck stuff.
2b) Wobbly Windows plugin. Uncheck Snap Inverted.

2a and 2b are mutually exclusive, you can't have both running at the same time, so pick your poison.


Wonderful, that was the ticket. :guitar:

Many thanks!

SF

---

### Post by Zorael on 2007-10-29
> **DouglasAWh said:**
> I am still utterly unable to find anything when  I move it within two workspaces.

Do you move windows between workspaces with the panel applet, or by dragging towards the edge?

Again, I've had very, very limited success with the applet, and I recommend the Expo plugin instead. I set it up to start if I move the cursor to the top-left corner.

---

### Post by DouglasAWh on 2007-10-29
> **Zorael said:**
> Do you move windows between workspaces with the panel applet, or by dragging towards the edge?

Again, I've had very, very limited success with the applet, and I recommend the Expo plugin instead. I set it up to start if I move the cursor to the top-left corner.

I can do both ways of moving, but the problem with moving by dragging toward the edge is I still all the taskbar items in every meaning, which defeats the point to me.  In the past, using the applet and dragging did the exact same thing, which would be nice now!!

Expo is nice, but it doesn't show items that are minimized which is less than ideal.

---

### Post by Zorael on 2007-10-29
I'm not sure there is a solution, beyond perhaps finding another applet/widget that is Compiz compatible.

And the Scale thing shows minimized windows, I guess, but it's still not a direct replacement.

You could try this - tell me if it works.

[http://www.kde-apps.org/content/show.php?content=46021](http://www.kde-apps.org/content/show.php?content=46021)

---

### Post by DouglasAWh on 2007-10-29
> **Zorael said:**
> 
You could try this - tell me if it works.

[http://www.kde-apps.org/content/show.php?content=46021](http://www.kde-apps.org/content/show.php?content=46021)

Will the KDE app work on GNOME?

---

### Post by Zorael on 2007-10-29
Oh, hum, my bad - I strayed and somehow assumed you were running Kubuntu. :>

---

