---
title: "Gnome panel to the side _with_ multiple columns"
date: 2007-06-23
forum: Desktop Effects &amp; Customization
---

### Post by dve on 2007-06-23
Hi,

How can I move the default gnome-panels (top and bottom) to the sides _and_ have a window list (also the default menu bar) in 5cm wide column. I have a "widescreen" laptop and I think I have too little space vertically and too much space horizontally. 

The icons should be arranged in a square lattice or in multiple columns, but with reasonable window list. 
The problem is that the window list scales the height of the items when the panel is vertical (c.f. width in horizontal panel). This is not good. Also the icons are aligned in single column in the center of the panel. Also not good.

Is it possible to stop the height scaling of the window list and give the icons in the panel arbitrary locations (square lattice is also ok)?

Also, how do you rotate the text in the gnome default menu?

I prefer haxoring the configuration files (I am a noob with ubuntu _not_ with linux), but also a solution through ubuntu menus is welcome.

Cheers,

Juha

---

### Post by BillyBuerger on 2007-06-30
I've been thinking the same thing.  I've got Windows on my current laptop with the taskbar along the right side.  Makes sense with a widescreen monitor.  I plan on eventually putting ununtu on it or my next laptop purchase.  But it seems that gnome and Xfce both weren't designed for certain things to be in the side panel.  I just loaded kubuntu on a spare PC and that does better with the side panel.  But I can't say I care for KDE that much.  I'm still trying to figure out what would work the best.  I keep jumping between ubuntu, xubuntu and kubuntu.  If anyone knows of a way to make gnome of Xfce do side panels better, that would be great!

---

### Post by DeadPanDan on 2007-07-03
I've also been wishing for this ability. I've been wondering if there might be a way to display window list titles 
[CENTER]
L
i
k
e

T
h
i
s
[/CENTER]

Doesn't GNOME have the capability to display text vertically in the Chinese and Japanese versions?

[http://www.gnome.org/start/2.18/notes/C/figures/figure-verticaltext.png]("http://www.gnome.org/start/2.18/notes/C/figures/figure-verticaltext.png")

---

### Post by BillyBuerger on 2007-07-04
I've been playing with this the last couple days.  Found a few things and I'm pretty happy with what I've got now.....

1) Right click->Properties on the top panel.  Set orientation to left and set size to 96.  Now it looks like crap.

2) Moved window list from the bottom panel to the side.  (All panels are locked by default so you have to unlock most of them to move forward.

3) Removed bottom panel.  This includes show desktop and workspace switcher.  I don't use these really.  Although I may add the desktop selector back sometime.

4) Removed the Menu Bar (Applications/Places/System) and added Main Menu.  The Menu bar does not work at all in a side panel.  The Main Menu button is more "Start Menu" like and is just a single icon.  Still ends up being kinda big.  But it's not too bad.

5) The clock also looked like crap.  But removing it and re-adding seems to have fixed it.  Looks good now.

6) Installed quick-lounge-applet.  Let's you have a bunch of launchers that wrap around the side panel.  This was the biggest thing I was looking for.

7) I had the trash on there at first.  But it resizes to the full width of the panel.  So it was huge.

8 ) System tray type thing are still vertical and take up more room then they need too.

The results look like this....

[[img]http://www.billybuerger.com/external/Ubuntu_Side_Panel_thumb.png[/img]](http://www.billybuerger.com/external/Ubuntu_Side_Panel.png)

---

