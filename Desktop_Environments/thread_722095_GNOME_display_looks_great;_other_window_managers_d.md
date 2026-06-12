---
title: "GNOME: display looks great; other window managers: display looks awful"
date: 2008-03-12
forum: Desktop Environments
---

### Post by jejones3141 on 2008-03-12
System: AMD Athlon 64, running Ubuntu Studio (Gutsy); nVidia 5200 graphics card using the proprietary nVidia driver, HP w1907 LCD monitor.

I have KDE installed, because this is my wife's computer and she likes KDE.. but, while the display looks very good under GNOME, under any other window manager, and even on the GDM screen, it looks wretched--it's most noticeable in text, or for that matter in the sides of the Google favicon in a browser window. As you move a window horizontally, narrow vertical lines oscillate between being very wide and nearly nonexistent.

Both GNOME and KDE are using the LCD monitor's "natural" resolution of 1440 x 900, which I added to xorg.conf. I have antialiasing and subpixel rendering turned on for both... though since the effect shows up for graphics like the favicon, text-specific settings can't be the problem, can they?

A friend recommended that I try another distribution's LiveCD and see whether KDE looks as bad, and see what they set up differently. Tried PCLinuxOS 2007, and sure enough KDE looked fine. Same screen resolution, antialiasing and subpixel rendering for text. The differences I saw in xorg.conf were that it was using the "nv" driver rather than "nvidia", the DPMS option was set to false, and there were old-style "ModeLine" entries.

This is the first LCD monitor I've used on a computer at home and thus been responsible for configuring, and I'm at a loss to figure out what the difference between GNOME and everything else is. How can I make the display look good whatever window manager/windowing environment I'm running?

---

### Post by jejones3141 on 2008-03-30
OK... I now have some more information.

My wife loved the LCD monitor so much that I got another one so that she could have the dual head display she wants with matching LCD monitors. So... we got another one, hooked it up, logged her in again with KDE, and fired up Thunderbird.

To my surprise, how the Thunderbird window looked depended on which monitor I dragged it to!

The difference: the graphics card has one VGA connection and one DVI. The DVI connected monitor looked fine; the VGA connected one looked wretched.

Alas, the only AGP graphics cards I can find with two DVI connections are ATI. So, my question now is: what the heck is GNOME, or probably more accurately GTK, doing that hides the lower quality of the VGA connection, and how can I get that to happen in general? (Or is it a difference in settings, e.g. font size?)

---

### Post by jejones3141 on 2008-05-17
Problem solved; I did a clean install of Hardy Heron, and both monitors now look good.

---

