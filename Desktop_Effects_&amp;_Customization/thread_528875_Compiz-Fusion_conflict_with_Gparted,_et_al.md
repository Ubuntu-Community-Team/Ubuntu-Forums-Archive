---
title: "Compiz-Fusion conflict with Gparted, et al"
date: 2007-08-18
forum: Desktop Effects &amp; Customization
---

### Post by jimbo99 on 2007-08-18
Well, a strange thing.  First, we all know there are very annoying problems with USB external drives.  Mostly with the fact that the OS doesn't always mount them.  When there's an entry in the FSTAB file it should mount it EVERY TIME and be CONSISTENT about doing so.  In fact, if you just do a reboot of the system the current set up will change the device upon which the USB drive is mounted, for example.  If you do a cold boot, by powering down the device used to mount on my system is /dev/sdd.  But if I do a warm boot without powering down then the device it uses to mount on my system is /dev/sdh.  NO WAY SHOULD THIS BE HAPPENING.  Not at this stage in the game.  This should have been perfected to the nth degree long ago.

Anyway, that's not what I writing about and I only discovered the gparted conflict with compiz-fusion while trying to resolve the issue with the /dev/sd?.  Anyway, what happens is that if you have the OpenGL desktop active then load gparted it won't allow you to select any menu item from within gparted.  Essentially, all gparted functionality becomes nullified.  You can't do anything other than really just drag the window around on the screen, minimize and close it.

When I turn off the OpenGL desktop and then launch gparted it works.  I've tested this backwards and forwards.  There's a serious oddity in how they are doing the OpenGL desktop (compiz-fusion).

There are also many other very odd issues with compiz-fusion.  For instance, the resizing of windows is wrong when you grab the window boarder size and then let go in a fluid motion.  The window is sized incorrectly by having the opposite side of the window border that you are trying to size size out the wrong direction.  If you do this slowly, and artificially; grab the window border, size it out, wait for a second then let go, it sizes properly.  If you turn off the resize feature of compiz-fusion off it makes it nearly impossible to size the window at all.

I've also noticed some serious slow down on selecting a large area on the desktop.  Holding the mouse button down and dragging over a small portion is fast but when you drag it over a larger portion the whole thing becomes extremely choppy.  This doesn't happen all the time.  But it does it enough to make it very annoying.

I've also noticed that the CPU utilization of the compiz-fusion consumes significantly more cycles to complete tasks.  Before you couldn't tell at all but now it is obvious when because the CPU utilization can skyrocket.

The desktop rotate using the mouse wheel has slowed down incredibly.  Yeah, it flips the cube but you have to spin the mouse wheel considerably more to get it to flip to the next side of the cube.  In Beryl this was incredibly fast and fluid.

The screen saver conflicts with the power management features, but that isn't saying too much because the power management features of Feisty were horrible to begin with.  So was the built in screen saver feature.

I know there's more but I don't want have to list them all.  Might turn some people off to using Linux.  Just with these guys would view fixing their bugs as important as adding new features.

---

