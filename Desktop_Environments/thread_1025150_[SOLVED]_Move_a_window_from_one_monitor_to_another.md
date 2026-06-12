---
title: "[SOLVED] Move a window from one monitor to another"
date: 2008-12-29
forum: Desktop Environments
---

### Post by art_s on 2008-12-29
Hi all,

My experience with X and dual monitor setup wasn't pleasant, but in the end I got it working. 

Now I have other issue: there seems to be no way to just move a window from one monitor to another. Yes, I know I can move a window to a different workspace, but that's within the same monitor.

Things are getting even more ugly: for instance, if I click on a link in Thunderbird, which is on monitor A, and Firefox happens to be opened on monitor B - no luck, Thunderbird gives me 'Firefox is already running but not responding' message.

Is there a way to solve/get around these issues?

Thanks!

---

### Post by art_s on 2008-12-29
There's some additional details: when using Xinerama I can move windows from one monitor to another, but there's no panel at athe top/bottom of second monitor, and they both share same workspace.

I'd rater have them working independently but with the ability to exchange windows/pass on control.

Thanks

---

### Post by art_s on 2009-01-02
Up. There must be people here who hit the same wall.

---

### Post by Navarre on 2009-01-02
When I first tried Ubuntu (too many versions ago) with my ATI card, The only way I could get dual monitors working was with 2 X managers.  They didn't share very well so I was in the same boat as you.

I've since left and come back to Ubuntu, this time installing 8.10.  I downloaded, installed and activated the ATI drivers, used catalyst to enable both monitors, set my resolution  huge (3360x1050) and I now I have the ability to move things from screen to screen.

---

### Post by jbruced on 2009-01-02
My 2 cents.

I worked hard with an nvidia card to get dual monitors working. Hacking xorg and all that crap, after reading tons of posts. Finally someone suggested installing nvidia-settings.

I ran it as sudo, chose twinview, clicked and dragged the monitors shown to position them where I wanted (2nd monitor to the right), clicked save, and voila now I just drag windows where I want.

In this setup I can add a panel and drag it to the 2nd monitor and put what I want on it.

This is a twinview setup, and is kind of a hybrid. It is one big desktop, but programs can recognize the screen number. 


Just a suggestion for nvidia setup.

---

### Post by art_s on 2009-01-02
> **jbruced said:**
> In this setup I can add a panel and drag it to the 2nd monitor and put what I want on it.

This is a twinview setup, and is kind of a hybrid. It is one big desktop, but programs can recognize the screen number. 


Thanks for the tip, eventually I ended up with setup like yours. However that breaks some programs down - for instance, Workrave stops giving you notifications. It's a workrave's problem, though.

Is there a way to have programs panel on both screens is such setup?

---

### Post by jbruced on 2009-01-02
Not sure what you mean by "programs panel", but if it's the regular gnome main menu or apps-places-system menus that you want, the answer is yes you can put that on the new panel, or anything else allowed on gnome panels for that matter.

You can keep adding panels to you desktop, right click on your present panel and choose new panel. Once you've got the new panel, right click it, allow it to be moved, then drag it to the second screen.

You can choose what you want on the new panel just like any other panel.

Hope this helped.

Bruce

---

### Post by art_s on 2009-01-02
> **jbruced said:**
> You can keep adding panels to you desktop, right click on your present panel and choose new panel. Once you've got the new panel, right click it, allow it to be moved, then drag it to the second screen.

You can choose what you want on the new panel just like any other panel.

Hope this helped.

Bruce

That's exactly what I need, thanks!

---

### Post by art_s on 2009-01-03
> **jbruced said:**
> You can choose what you want on the new panel just like any other panel.

Actually, is there a way to add another panel where all the running tasks are listed, like the one at the bottom of first screen?

---

### Post by art_s on 2009-01-03
> **art_s said:**
> Actually, is there a way to add another panel where all the running tasks are listed, like the one at the bottom of first screen?

Found it:

!) Create new panel, drag it to the bottom of the screen
2) Right click on it, 'Add to panel"
3) Select "Window selector"

Awesome!

---

