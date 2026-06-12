---
title: "click_to_focus and raise_on_click seem to be broken"
date: 2008-08-23
forum: Desktop Environments
---

### Post by diobrando on 2008-08-23
I'm suddenly having a very strange issue with window focus. I've tried just about everything I can think of and only managed to make it worse. I can't seem to pinpoint exactly when it started, but it may have been after an update.

I had it set up so I could click anywhere in an inactive window and it would move focus to that window as well as raise it to the front. Suddenly this stopped working (I am using gnome with compiz) and I would have to click on the title bar in order to raise the window, however I could click in the window contents and get focus for keyboard input, etc. 

So far I've tried turning off compiz and using metacity (didn't work) along with various suggestions from other forum threads with similar issues (like turning on the mouse focus/restarting x/turning it back off, etc) I tried various combinations of settings in ccsm with compiz reenabled. I also tried editing the settings for both compiz and metacity in gconf-editor. Finally, I tried using KDE (same issue there)

Somewhere along the line I've actually broken it worse, as now when I click on the title bar I can raise a window and move it around, but to actually get focus on it I have to click the window title in the taskbar or use alt-tab. Turning off click_to_focus and raise_on_click in gconf-editor switched it back to mouseover focus and that works, but it seems like when I reenable those options I lose mouseover focus but don't get normal click focus back.

Suggestions, anyone?

---

### Post by ankle on 2009-02-07
I'm seeing the same kind of thing - I have 'raise_on_click' enabled in /apps/metacity/general, but windows will only raise by clicking on their title bar, not on the window contents.

---

### Post by ankle on 2009-02-07
It looks like it must have been a setting in ~/.gnome, ~/.gnome2, ~/.gconf/apps/compiz or ~/.gconf/apps/metacity, as moving those out of the way restored 'click to raise' to its proper state.

---

### Post by babounours on 2009-04-08
I would remove .gnome or .gnome2 folder to get the default behaviour. But as a extensive linux user I find the hability to raise the window only when I wnat it to raise very usefull when working with several of them.
for information "raise_on_click" and "focus behavior" are accessible through the gconf-editor in app->metacity->general and it is too bad that it is not accessible in the gnome-control-center

---

