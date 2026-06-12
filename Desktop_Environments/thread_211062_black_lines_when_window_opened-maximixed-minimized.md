---
title: "black lines when window opened-maximixed-minimized"
date: 2006-07-07
forum: Desktop Environments
---

### Post by tturrisi on 2006-07-07
When I launch an app or maximize-minimize an app, black lines appear prior to the window being displayed, sort of like a "growing or reducing" box where the window will be."  How do I get rid of this effect?

---

### Post by zhoux on 2006-07-07
i think it has something to do with your graphics card and how it is rendering graphics...so either get a new, faster card or change how the card is doing graphics....

o, also, it depends on how much free ram you have and your processor power...

so i guess it mainly relates to hardware usage and problems...

but i'm no expert at this, so...

---

### Post by tturrisi on 2006-07-07
I don't believe it's hardware related.  I have plenty of ram and graphics are ok.  It's some type of animation of the window borders & I want to get rid of it.

---

### Post by angkor on 2006-07-07
This is (quite an ugly) metacity 'feauture'.

You can turn it off by going into the gconf-editor:

Apps->Metacity->General and check the 'reduced resources' key, but this has a nasty side effect when you resize windows (you get an ugly frame in stead of the windows content). Don't know what else changes with this setting enabled.

Edit: I did a search to see if anyone has been able to get rid of this effect but keep the resizing normal. No luck...I feel my old dislike for metacity coming back. Maybe I'll replace metacity with sawfish (like I did in breezy) or enlightenment.

[http://www.ubuntuforums.org/showthread.php?t=38662](http://www.ubuntuforums.org/showthread.php?t=38662)

---

### Post by tturrisi on 2006-07-07
> **angkor said:**
> This is (quite an ugly) metacity 'feauture'.

You can turn it off by going into the gconf-editor:

Apps->Metacity->General and check the 'reduced resources' key, but this has a nasty side effect when you resize windows (you get an ugly frame in stead of the windows content). Don't know what else changes with this setting enabled.

Edit: I did a search to see if anyone had been able to get rid of this effect but keep the resizing normal. No luck...I feel my old dislike for metacity coming back. Maybe I'll replace metacity with sawfish (like I did in breezy) or enlightenment.

[http://www.ubuntuforums.org/showthread.php?t=38662](http://www.ubuntuforums.org/showthread.php?t=38662)
Thank, but you are correct.  It's much worse with reduced resources check.  You get ugly black grid.

Actually I am new to Gnome.  On my deb systems I never used a desktop environment, I only used a window manager, Fluxbox, which is superfast & lightweight.  But I installed Ubuntu this time for 2 reasons:  I wanted to try to get to like Gnome & I was lazy and didn't feel like building up a system from a base install.  I really dig Ubuntu over other deb based Gnome bloated installs and I have done a lot of study & tweaking.  So far so good, except for the Metacity outlines.  Gusee I'll live w/ it for now.  Thanks.

---

### Post by aysiu on 2006-07-07
Use reduced resources and then go to System > Preferences > Assistive Technology Support and enable it. This gets rid of the shrinking/enlarging lines *and* the black grid.

---

### Post by tturrisi on 2006-07-07
> **aysiu said:**
> Use reduced resources and then go to System > Preferences > Assistive Technology Support and enable it. This gets rid of the shrinking/enlarging lines *and* the black grid.
sweet, thanks!
any drawbacks to reduced-resources or undesirable effects?

---

### Post by aysiu on 2006-07-08
> **tturrisi said:**
> sweet, thanks!
any drawbacks to reduced-resources or undesirable effects?
Only [this](http://www.ubuntuforums.org/showthread.php?t=189168), but I appear to have been one of the very few who experienced it.

---

### Post by tturrisi on 2006-07-08
> **aysiu said:**
> Only [this](http://www.ubuntuforums.org/showthread.php?t=189168), but I appear to have been one of the very few who experienced it.
I too have that _empty) listing.  What's really wierd about it is this:
It goes away after expanding each subfolder, then expanding the next, then back to previous, but ONLY for the current window.  Successive new ff windows will have (empty) again.

---

### Post by aysiu on 2006-07-08
Yeah. I reported it as a bug. It's super low priority on the developers' list, though.

---

### Post by tturrisi on 2006-07-08
ok, thanks.
however, it's a more than fair tradeoff for those wire frames!

---

