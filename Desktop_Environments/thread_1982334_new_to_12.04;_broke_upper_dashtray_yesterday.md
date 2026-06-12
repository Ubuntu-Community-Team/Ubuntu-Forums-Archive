---
title: "new to 12.04; broke upper dash/tray yesterday"
date: 2012-05-18
forum: Desktop Environments
---

### Post by zapriori on 2012-05-18
I've been using 10.04 on a couple of laptops for a long time and really love it. Set them up with the various Mac4Lin kind of stuff and they are extremely convenient now.

A few days ago I decided to start to bag out of M$ on the desktop downstairs and installed Lubuntu 12.04 on a second partition with dual-boot. 

I tried playing with Unity before and just cannot deal with it, so I began switching things over to Gnome/Gnome Shell based on some Howtos. It's now running Gnome 3.4 (I think).

Yesterday I was trying to clean things up a little bit and I accidentally blew away the little Wireless Connection Status, Bluetooth Status and Audio Settings Status controls in the upper corner of the screen. <argh!> I can't find a menu or configuration control anywhere that I can restore what I accidentally blew away :-(

Can someone point describe how I can restore the original features of that status area? Thanks in advance...

---

### Post by kansasnoob on 2012-05-18
> **zapriori said:**
> I've been using 10.04 on a couple of laptops for a long time and really love it. Set them up with the various Mac4Lin kind of stuff and they are extremely convenient now.

A few days ago I decided to start to bag out of M$ on the desktop downstairs and installed Lubuntu 12.04 on a second partition with dual-boot. 

I tried playing with Unity before and just cannot deal with it, so I began switching things over to Gnome/Gnome Shell based on some Howtos. It's now running Gnome 3.4 (I think).

Yesterday I was trying to clean things up a little bit and I accidentally blew away the little Wireless Connection Status, Bluetooth Status and Audio Settings Status controls in the upper corner of the screen. <argh!> I can't find a menu or configuration control anywhere that I can restore what I accidentally blew away :-(

Can someone point describe how I can restore the original features of that status area? Thanks in advance...

That looks like 'gnome-panel', and that it's missing 'indicator-applet'. I recently posted a comparison of indicator applets here:

[http://ubuntuforums.org/showpost.php?p=11900657&postcount=12](http://ubuntuforums.org/showpost.php?p=11900657&postcount=12)

If you're running a Gnome classic session - which uses Compiz - you must now press both the Alt & Super keys at the same time while right-clicking on the panel/applet you wish to edit, move, or remove. (The Super key is typically the one with the Windows logo).

If you're running Gnome classic (no effects) - which uses Metacity - you need only hold down either Alt key while right-clicking on a panel or applet to be able to edit panel preferences or to add/edit/move/remove more applets.

---

### Post by zapriori on 2012-05-18
:grin:

Thanks, Kansa - I poked at this yesterday and didn't stumble on the right stuff. I think I must have seen a similar posting you may have made elsewhere; on my system, it's the "Windows"+Alt+right-click to bring up the menu I needed.

Even though I was futzing around with it yesterday to no apparent relief, I looked more carefully at the menu today and noticed one item that seemed to be the key:

(Add to Panel) -> Indicator Applet Complete

That seems to bring up the original status bar (before I screwed it up, haha). When I did this to fix things, I ended up two sets of stuff because I had been adding a couple of things back that I knew i "needed" - clock+calendar, e.g. But the magic seemed to be to choose the "Indicator Applet Complete".

Thanks mucho for your patience, and for sticking around and helping everyone!

---

Since I blew away the task-bar at the bottom to do the OS X-like dock, do you know of a way to make part of the top panel behave like a task bar as well?

---

### Post by kansasnoob on 2012-05-18
> Since I blew away the task-bar at the bottom to do the OS X-like dock, do you know of a way to make part of the top panel behave like a task bar as well?

Add Window List :confused:

---

### Post by grahammechanical on 2012-05-18
@Zapriori

There are a couple of things in your first post that I do not understand.

You say this:

>  Lubuntu 12.04 on a second partition with dual-boot.

and this:

> I tried playing with Unity before and just cannot deal with it, so I began switching things over to Gnome/Gnome Shell based on some Howtos. It's now running Gnome 3.4 (I think).

This is what I do not understand, Lubuntu does not use the Unity desktop user interface. It uses the LXDE desktop user interface.

[http://lubuntu.net/]("http://lubuntu.net/")

So, what are you modifying exactly? Ubuntu/Unity or Lubuntu/LXDE?

Regards.

---

