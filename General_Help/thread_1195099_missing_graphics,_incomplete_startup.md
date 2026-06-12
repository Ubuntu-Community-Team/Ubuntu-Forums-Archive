---
title: "missing graphics, incomplete startup"
date: 2009-06-23
forum: General Help
---

### Post by cong06 on 2009-06-23
On startup every window shows up without any decoration. User specified keyboard shortcuts don't work (ie: alt-f2 and super L don't, whereas crtl+alt+f1 do). Also the network doesn't work and the panels are missing.

After running compiz --reload &, the network returns, my user specified shortcut for super L returns, but alt-f2 still doesn't. Network access is returned, but the panels are still missing.

This all happens on the restart after the full program upgrade right after a fresh install, but continues...

On my install I had parse problems with scrollkeeper, which caused problems with dpkg, but eventually these were resolved to the point that dpkg could complete (but scrollkeeper-reloaddb still threw a few errors)

[Initially I thought it was a missing program in startup, but I gave up on that approach.]("http://ubuntuforums.org/showthread.php?t=1193049") Instead I tried re-installing, only to have the same problem, except this time having made no changes to the startup list.

---

### Post by cong06 on 2009-06-25
I rebuilt the install disk, and re-installed. It's working now.

Who knows what happened the first time. I'm afraid I'm going to do it again...

---

### Post by jake16424 on 2009-06-26
linux is rather edgy when it comes to install and stability.

you get it right the first time, its no problem , strong as steel, it installs wabbly all h3ll breaks loose =D

---

### Post by loomsen on 2009-06-26
Did you enable the gnome compatibility plugin?

CCSM -> Main -> Gnome Compatibility

Further, you should either alter the gconf key
desktop->gnome->session->required components-> window manager

to fusion-icon

Or add fusion-icon to your startup apps. Both will do the trick if you have the window decorator plugin enabled.

---

### Post by cong06 on 2009-06-26
I didn't install ccsm because I wasn't interested in the extensive results. Running on a netbook means I have very limited graphics.

My best guess is what jake16424 said, even though that really doesn't explain the problem.

By this point I've done exactly the same changes as I did initially, just slower, and over more re-boots.

My problem on the first two installs may have been that I try to install and configure on the same boot. It's a terrible explanation, but I guess it could make sense...

---

### Post by cong06 on 2009-06-26
ugh.

I just realized what the problem was. I had uninstalled evolution, and with it the whole gnome-desktop.
the package manager "recommended" evolution, which I figured meant it was ok.

---

