---
title: "Upgraded to 11.10, Unity menu bar/panel missing on second monitor"
date: 2011-11-26
forum: Desktop Environments
---

### Post by greggatghc on 2011-11-26
I have a two monitor setup.  I upgraded to 11.10 and the menu bar/top panel, whatever you want to call it, is missing.  It appears for about half a second and then disappears.  I dont see any error messages anywhere.

How do I figure out whats going on here?  I need my menus.

---

### Post by greggatghc on 2011-11-27
I still haven't been able to figure this one out, any help would be really appreciated.

---

### Post by toddles on 2011-11-29
This is just a shot in the dark:

you might have a conflict with the unity plugin in compiz which is causing it to be disabled (not your fault probably).

Try opening a terminal (ctrl + alt + t since your unity bar is not working).

type ccsm

if it is not installed: sudo aptitude install compizconfig-settings-manager

search for the unity plugin and check the box next to it.

ignore conflicts if prompted.


I think there was a recent update that broke this. If ubuntu unity does not get a lot more stable in the not too distant future I am switching to Linux Mint.

---

### Post by greggatghc on 2011-11-29
Thanks for the tip, tried it, but it didnt fix it.  Any other ideas?

---

### Post by Mark Phelps on 2011-12-05
Sorry for the delayed response ... but this is how Unity is designed to work.  I have a dual-monitor setup and see much the same thing -- single display on both monitors for a few seconds, then the same backgound on both (no sidebar or menus), then the sidebar on the main screen.

Don't know of any way to get (1) the sidebar on both screens, with (2) separate usage of each screen.  Mirroring doesn't appear to do that for you.

---

