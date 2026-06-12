---
title: "Broke control themes while adding new skins"
date: 2008-01-29
forum: Desktop Environments
---

### Post by drewcoon on 2008-01-29
Hey, I was downloading and adding some new looks from gnome-look.org and I think that I might have done something that I shouldn't have (I was dragging and dropping themes to the theme manager, in retrospect it was probably a bad idea). I tweaked something and now a small part of my theme is no longer possible to modify.

Basically, this image sums it up,
[http://i16.photobucket.com/albums/b23/Drewc2k5/problem.png](http://i16.photobucket.com/albums/b23/Drewc2k5/problem.png)
(warning, large image of desktop)

The text on the menu bar in the mist control scheme used to be black, it's now white and I can't seem to be able to change it with the theme manager. The separators on the panels used to integrate in quite well, but they're now ugly black lines and dots. Also, the workspace switcher no longer follows system colors and defaults to an ugly black color.

Is there a quick solution to my mistake? I'm not sure where the installed theme packages went so I don't know how to access them. I've also tried reinstalling a few gnome panel-related packages but it didn't help anything. Are there configuration files somewhere for the control schemes that I can edit?

I'm sorry if I'm too vague about what happened, because I'm not too sure what happened myself. if anyone can help out it would be great, if not... Thanks anyways :)

---

### Post by drewcoon on 2008-01-29
UPDATE -- I figured out where my themes are stored (.themes in my home folder... d'oh!). I erased some of the themes I installed and amazingly enough it made a difference. The text at the top menu bar has now returned to it's black state, although the desktop switcher and separators are still ugly.

I'll keep tweaking :)

---

### Post by drewcoon on 2008-01-29
Another update... I've figured out that the reason the separators and switcher are black is because the panels are actually black. When I change the colors around in the theme manager, the panels stay black for some reason, regardless of what theme I apply (if you set them to "use system theme" in the panel properties it's more apparent).

Any ideas?

---

### Post by Anduu on 2008-01-29
Have you tried rebooting so the panel reloads?? You can also try a killall gnome-panel from the terminal...it will automatically reload itself.

If that fails set your theme back to the default Human theme and move ALL the themes out of your /home<username>/.themes folder and restart.

If that solves the problem you can then move the themes back one by one and check them out until you find the culprit.

---

### Post by drewcoon on 2008-01-30
Rebooting did nothing, and killall just made the panels disappear (they didn't restart on their own :p). I also tried moving all the themes out and no solution.

What I'm thinking is that a control scheme is the culprit (buttons, etc). The .themes folder only has my custom themes that I made in it, not the extra skins that I got off gnome-look (I downloaded a few control schemes and icon sets). Where are these things stored?

I cleared out my .icons folder of all my cursors and icon themes, I want to next find out where the controls are that I downloaded and delete those, too.

---

