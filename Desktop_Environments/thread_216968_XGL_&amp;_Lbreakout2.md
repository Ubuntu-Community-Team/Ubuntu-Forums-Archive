---
title: "XGL &amp; Lbreakout2"
date: 2006-07-16
forum: Desktop Environments
---

### Post by Genesius on 2006-07-16
Some minor weirdness. Running Kubuntu 6.06 w/XGL, NVidia Geforce4 MX 420 video card. All my versions are up to date. Everything else runs fine, but whenever I try to run Lbreakout2 I get this:

Opacity is at 100%. Anybody else seen this one?

---

### Post by Anduu on 2006-07-16
Some OpenGL apps just don't get along with Compiz/XGL I'm sorry to say...

---

### Post by autocrosser on 2006-07-16
Yes--I see the same problem & i'm running the new 2.6 beta6 from his site on SourceForge (by the way--if you like lbreakout2--try the new beta6--it rocks!!)--I'll e him & see what he thinks--I did notice that the splashscreen for UT2004 is doing the same thing (maybe use gset-compiz & shut off mods to splashscreens? just a thought)

His website for Lbreakout2 is--  [http://lgames.sourceforge.net/index.php?project=LBreakout2](http://lgames.sourceforge.net/index.php?project=LBreakout2)

If you like the game, I suggest you check it out & help with beta testing the new version:D

---

### Post by FallenWizard on 2006-07-16
Just execute this in your console: export XLIB_SKIP_ARGB_VISUALS=1

It should work now, because the transparency is a bug of SDL.

(Beware: It is a temporary fix. I hope the SDL devs will fix the bug soon.)

EDIT: Here is a screenshot. I works like a charm.
[http://img59.imageshack.us/img59/2309/breakoutpr6.png](http://img59.imageshack.us/img59/2309/breakoutpr6.png)

---

### Post by autocrosser on 2006-07-16
Any thoughts on a script to make it stay after reboot (or will it persist?)

"Just execute this in your console: export XLIB_SKIP_ARGB_VISUALS=1

It should work now, because the transparency is a bug of SDL.

(Beware: It is a temporary fix. I hope the SDL devs will fix the bug soon.)"

---

### Post by Genesius on 2006-07-18
> **FallenWizard said:**
> Just execute this in your console: export XLIB_SKIP_ARGB_VISUALS=1

It should work now, because the transparency is a bug of SDL.

(Beware: It is a temporary fix. I hope the SDL devs will fix the bug soon.)

EDIT: Here is a screenshot. I works like a charm.
[http://img59.imageshack.us/img59/2309/breakoutpr6.png](http://img59.imageshack.us/img59/2309/breakoutpr6.png)

Nope, didn't help.:(

---

### Post by autocrosser on 2006-07-18
I've tried it too--no luck--have not heard from the developer--if I do, I'll post it here...

---

