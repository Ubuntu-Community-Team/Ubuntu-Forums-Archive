---
title: "Workspace problem"
date: 2013-07-19
forum: Desktop Environments
---

### Post by paulb42 on 2013-07-19
Hi all,
I have a problem with using multiple workspaces on Ubuntu 12.04 with Gnome (and indeed Unity).
I have been playing with Compix to enable some effects, while using Gnome session fallback.
Previously I had 4 workspaces and could navigate between them with no problem.

Now, when logging on to gnome I can see the 4 workspaces in the bottom right but can't switch to anything.
When logging on to Unity I don't get any multiple workspaces, just the one.

I have tried changing the workspace configuration via Compiz and Ubuntu Tweak etc etc but still can't reenable anything other than 1 workspace.

Any offers? Not a major issue but I like using multi-workspaces and wish I'd never touched Compiz now!

Thanks
Paul

---

### Post by dino99 on 2013-07-19
the system is very (too) sensitive to that instable compiz; so reset it to default using dconf
[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by paulb42 on 2013-07-19
Thanks for the reply. That link refers to 12.10 and 13.04; is it still valid for 12.04?
I think tyhat dconf reset command is one of the thing's I've tried (had to use sudo) but it didn't seem to have any effect

---

### Post by r_avital on 2013-07-19
I've had the exact same problem.  I don't know what this will do for you in unity (which I consider a virus and won't use it), but try this in the fallback session:

In compiz settings manager, go to the General Options item, and in it there should be a tab called Desktop Size.  Only three settings.  They should be:

Horizontal Virtual Size = 4
Vertical Virtual Size = 1
Number of Desktops = 1

Yeah, confused me too, but it works.

---

### Post by paulb42 on 2013-07-19
Thanks for the suggestion. I tried that and I can see the ws config being changed to 1 row of 4 spaces, but I still can't select anything other then the first one!

---

### Post by paulb42 on 2013-07-19
Hmm, well I've half fixed this, I used My Unity to set the numer of workspaces to 4 horizontal times 1 vertical and it now works OK on Unity but not on Gnome. I'll keep searching.

---

### Post by mc4man on 2013-07-19
In 12.04 set ccsm as desired, see screen
Also right click on the workspace applet in bottom panel > Preferences & make sure it's set to 1x1, also in screen

If that doesn't work maybe set up a new user to test, login & set up as in screenshot, see if it works there

---

### Post by norville on 2013-10-05
> **r_avital said:**
> I've had the exact same problem.  I don't know what this will do for you in unity (which I consider a virus and won't use it), but try this in the fallback session:

In compiz settings manager, go to the General Options item, and in it there should be a tab called Desktop Size.  Only three settings.  They should be:

Horizontal Virtual Size = 4
Vertical Virtual Size = 1
Number of Desktops = 1

Yeah, confused me too, but it works.

Many thanks r_avital, this solution works fine for me (Ubuntu 13.04 - Gnome Classic)

---

