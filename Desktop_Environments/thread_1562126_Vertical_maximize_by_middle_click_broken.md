---
title: "Vertical maximize by middle click broken"
date: 2010-08-27
forum: Desktop Environments
---

### Post by DonEsteban on 2010-08-27
Hi,
until recently I could vertically maximize windows by middle-clicking the maximize button (using ClearLooks theme). This doesn't work any more, I'm not sure what caused it. I think I opened a ComboBox with a really long text in it in eclipse. Then some screen flickereing and suddenly I had only one workspace instead of 2x2. Well, I could fix that (although there order seems to have changed: 1,3,2,4 instead of 1,2,3,4). But I still can't vertically maximize. It just puts the window to the background now. 

I know this sounds really strange, maybe there is an entirely different reason, it might have been caused by some recent update?

How can I get my middle click maximizing back?

---

### Post by DonEsteban on 2010-09-02
Bump! Any ideas anyone? Please? Can anyone at least confirm that vertically maximizing by middle-clicking the maximize button still works for them (or not)?

---

### Post by amanessinger on 2010-09-15
When you have enabled 3D effects, you use the compiz window manager, and without 3D effects it is the brain-dead Metacity window manager. Metacity was created by people who know much better than you what you want, and they know that you don't want to maximize vertically using <Button-2>. Oh well!

As much as I like the slickness of Gnome in Ubuntu 10.04, this is one of the reasons why I use Xubuntu. But then, in the good old days I had not only virtual desktops, I had also viewports. Sadly no current window manager supports that. Windows users don't have it, so, how could anybody want it, huh?

I suppose what happened to you was, that somehow Compiz broke, your system fell back to Metacity (thus the different workspace configuration as well), and because everything looked the same, you didn't recognize it. Re-enable desktop effects or use another window manager.

Andreas

---

### Post by DonEsteban on 2010-09-25
This actually helped! I wasn't aware that I had the "Normal" Visual Effects activated previously. Don't need them. But switching them back on solved my problem. Thanks!

---

### Post by fabianofcarlos on 2011-05-15
It worked just fine! Thanks!

This is one simple feature I've come to use a lot since I switched to Linux from Win.
And I screwed it up while messing with Compiz and desktop animation. And now you've helped me get it back :P

---

