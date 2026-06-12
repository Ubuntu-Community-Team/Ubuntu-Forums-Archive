---
title: "Compiz screen error"
date: 2009-04-13
forum: Desktop Environments
---

### Post by x56sImpulse on 2009-04-13
Sorry for making a new thread for this, but I couldn't find one that addressed this problem.

Yesterday I was fiddling with my compizconfig settings (just with the cube workplace switcher I think) and my screen went all screwy.  Anywhere on the screen where I selected a window or opened a dialog box became black or a muddle of coloured pixels.  Eventually my whole screen became dark and unusable.  I rebooted and the same happened.

Figuring that this had something to do with compiz I booted off a live CD and deleted the compiz and compizconfig folders in /usr/lib  (maybe not the best way, but I couldn't thin of any other).  I booted up normally and that problem was fixed, but my window border was missing (I think I found how to fix that).  But now when I try to reinstall compiz (after completely removing it with symatic). It happens again.

Any Idea what's causing this??

---

### Post by OldManRiver on 2009-04-13
X,

Two quick Qs:
[LIST=1]
[*]What is your default screen resolution?
[*]Did you get any blacklist errors during the Compiz install?
[/LIST]

If your default resolution is not in the high res mode or you got a blacklist error, then you either need a more advanced video/graphics card, need a work around with more video RAM, or need a custom X-Win driver.

The guy who wrote the book on custom X-Win drivers, and has a online utility to test your hardware and write the driver is out of the UK and goes by the handle NeddySeagoon and you find him on IRC on the #gentoo channel.

See what you can do to further diagnose your problem and post it back here so we can help.  Also a private IM would be good.

Cheers!

OMR

---

### Post by x56sImpulse on 2009-04-14
1.  my resolution is 1024x768
2.  I didn't get any errors when I installed it.  I installed using symantic, so it might not have been the most up to date...

I'm on my laptop using a discrete video card, so very low power, but I didn't expect that to be the problem.  

Right now I'm trying to reinstall compiz with all the default settings, because it worked fine before I made the changes.  I thought I removed it all, but I can't be sure.  Know how I can make sure all my settings are removed?

---

