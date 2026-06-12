---
title: "Running a 4k and 2k monitor"
date: 2014-10-16
forum: Desktop Environments
---

### Post by paulisdead on 2014-10-16
So I just got my 4k Samsung, and it's freaking beautiful.  Thing is, I'm also using a 2k (1080p) monitor, for a secondary display.  I tried enabling the gnome-staging ppa, and installed gnome 3.12 on my 14.04 install, and I've already tried
set org.gnome.desktop.interface scaling-factor 2
and that just makes everything huge on the secondary monitor.  With the scaling back to 1, and with the nosquint extension in firefox, it's closer to where I want things, but not perfect.  I suppose I can manually adjust the fonts in some of my apps, based on which monitor I use them on the most, but that seems sloppy.  I've googled around quite a bit, and so far not come up with anything better.  So, I was just curious if anyone's figured out a better way to run 2 monitors with really different resolutions.

---

### Post by tgalati4 on 2014-10-17
Multiple monitors are displayed on something called a "Super Desktop".  Imagine an 8k by 8k pixel grid.  Your monitors can move around that grid so that the relationship between the physical layout and the virtual layout can be established.  Your mouse should travel smoothly between the two displays if you have them placed correctly.

Using this Super Desktop framework means that if you have two monitors with vastly different resolutions, you will get what you expect.  The Super Desktop is a one-to-one pixel relationship.  There is no framework to handle different resolutions.  You can set a scale factor--and that does exactly what it does, expand the Super Desktop pixel ratio.  But all displays pinned to the Super Desktop get the same treatment.

You would need a new Super Desktop framework (perhaps based on vectors, not pixels) and a graphical transform engine to go from vectors to pixels.  Then you could have multiple monitors with multiple resolutions, all happily living together.  Writing such a framework is non-trivial.

So, either get another 4K monitor (and a bigger video card to support 2 4K displays), or set up an xorg.conf file with your 4K monitor defined as a 2K monitor.  I'm sure your 4K monitor has a decent scaling engine to handle 1/2 resolution.

---

### Post by paulisdead on 2014-10-17
Thanks for the good write up, and clarifying the situation.

Since 4k monitors aren't cheap, I don't think I'll be getting another one soon.  At least the Geforce 980 I got before this monitor should be able to handle a second 4k monitor down the road.  I just dumped a lot of cash into getting my system ready to handle 4k, so another monitor is not in the budget in the near term.

Scaling seems like a less than optimal solution, as well.  But I may look into it.

All that being said, does anybody have any hacks or workarounds they'd like to share?  I have found a better firefox extension, [https://addons.mozilla.org/en-US/firefox/addon/autohidpi/?src=api](https://addons.mozilla.org/en-US/firefox/addon/autohidpi/?src=api) so my text in firefox is better, but the menus and tab text is still small.  I figure people have been working on hidpi laptops and using a secondary monitor for awhile, so they might have some workarounds.

Things aren't terrible with the way I've currently got things running, but they could be better.  For now, I guess I'll just tweak the font settings for apps based on which monitor I use them on.

---

### Post by paulisdead on 2014-10-19
I had some luck tweaking with the interface and Window Titles fonts in gnome tweak tool.  Fonts are bigger without making absolutely everything too huge on the secondary monitor.

Also in the advanced settings for thunderbird, I set layout.css.devPixelsPerPx to 2.

---

