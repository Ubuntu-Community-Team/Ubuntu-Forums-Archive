---
title: "gnome panels on two monitors"
date: 2010-02-27
forum: Desktop Environments
---

### Post by victor.zamanian on 2010-02-27
Hello!

My graphics card is nvidia geforce 7900 GS. It has two DVI outputs, and I have one monitor plugged into each output. I am running proprietary drivers from nvidia, thus also the `nvidia-settings' tool.

I'm running with the TwinView setting, enabling nice dragging and dropping of windows between the two monitors, but here's the problem:

**Only one of my two monitors have the gnome panels at the top and bottom of the screen. I would like the panels to show up on both screens.**

If this is possible, how would I go about enabling this?

*Bonus Question*: Once this is enabled, if possible, would I then somehow also be able to have different virtual desktops be active on each monitor? If so, how?

---

### Post by c-shadow on 2010-02-28
Have you tried "separate X screen" setup in nvidia settings?

---

### Post by asmoore82 on 2010-02-28
You have to right click the panels on Monitor #1 and choose "New Panel"
Then **hold Alt** and click and drag the new panel to Monitor #2.

"Expanded" Panels always "cling" to the edges of your physical screens and
hence are unable to span across 2 monitors, this is by design.

AFAIK all of the dual head screenshots that appear to have 2 panels stretched
across are just clever layouts of 4 separate panels :D.

---

### Post by victor.zamanian on 2010-02-28
> **c-shadow said:**
> Have you tried "separate X screen" setup in nvidia settings?

Yeah, that didn't work at all. It made a completely different X session it would seem, and I couldn't move windows between monitors and the gnome-panels would act weirdly (like I couldn't just move the mouse to navigate menus, but had to click sub-menu items for them to open. No-go on separate X screen, unfortunately.

> **asmoore82 said:**
> You have to right click the panels on Monitor #1 and choose "New Panel"
Then **hold Alt** and click and drag the new panel to Monitor #2.

"Expanded" Panels always "cling" to the edges of your physical screens and
hence are unable to span across 2 monitors, this is by design.

AFAIK all of the dual head screenshots that appear to have 2 panels stretched
across are just clever layouts of 4 separate panels :D.

Ah, so there's no way to just duplicate the panels? You have to actually create them? I was thinking I would be able to have one set of panels and changing one of them would update the other monitor, but I guess this is a feasible solution since I don't change the panels very often, and really one shouldn't have to if the gnome devs thought their design through. Which I like to think they did. :)

Thanks by the way, this is pretty much what I wanted. Gold stars for you!

PS: The Alt+dragging thing didn't really work for me, for some reason. I had to go into the properties of the panel, disable the Expand option, then drag the handle that shows on the panel's edge when it is not expanding to screen edges. Maybe because I set my Window-Dragging Key to Super? I don't know. :)

---

### Post by asmoore82 on 2010-02-28
oh yea, I think compiz has made the point moot but I don't have any experience with it...

With Compiz, I believe you can make it show 2 of your workspaces simultaneously
and really stretch the illusion to perfection.

yea, that Alt/Super thing really does follow whatever you set the window drag
key to, +50 points to Gnome-devs for that.

---

### Post by asmoore82 on 2010-02-28
I tested out the Compiz setup ~
I figured I have all the pieces around here so "Why not??"

I connect a regular desktop monitor to my laptop...
My impression was mistaken, the panels still behave the same even under compiz.

Compiz will display the "Desktop Cube" effect from 2 different Points of View
on the different monitors, but as an example of how it works,
odd numbered faces will only snap to monitor #1 and even numbered
faces to monitor #2.

---

### Post by victor.zamanian on 2010-03-02
> **asmoore82 said:**
> yea, that Alt/Super thing really does follow whatever you set the window drag
key to, +50 points to Gnome-devs for that.

It doesn't work for me unless I disable the "Expand" option in the general tab of the panel's properties dialog. But at that point I don't have to use a modifier key at all. Strange. Does it really work for you?

> **asmoore82 said:**
> Compiz will display the "Desktop Cube" effect from 2 different Points of View on the different monitors, but as an example of how it works, odd numbered faces will only snap to monitor #1 and even numbered faces to monitor #2.

Nice! :) That's the kind of feature I'm talking about! Shame it had to only be available in compiz. ;P All that's missing there for me is to be able to select an arbitrary workspace and only have visible on the monitor the part of that workspace which would be designated the monitor in question. Otherwise nice work compiz dev team!

---

### Post by mereih on 2010-06-29
> **asmoore82 said:**
> You have to right click the panels on Monitor #1 and choose "New Panel"
Then **hold Alt** and click and drag the new panel to Monitor #2.

"Expanded" Panels always "cling" to the edges of your physical screens and
hence are unable to span across 2 monitors, this is by design.

AFAIK all of the dual head screenshots that appear to have 2 panels stretched
across are just clever layouts of 4 separate panels :D.

Thanks, that worked perfectly. Exactly what I wanted. ):P

---

### Post by Motorhead Kaze on 2010-11-16
YOW!!!

```

You have to ... hold Alt and click and drag the new panel to Monitor #2.
``` Yes! This is what I wanted. I have used dual-heads on Ubuntu for a few years, and this is the first time I have ever ended up with Gnome panels on the right monitor instead of the left. Didn't want them there, and this "hold alt while you drag em" was slick! ...they should put a note saying something like that somewhere in the panel prefs.

Anyway thanks. My computer screen looks normal again.

---

