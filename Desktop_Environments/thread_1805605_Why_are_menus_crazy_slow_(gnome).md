---
title: "Why are menus crazy slow (gnome)?"
date: 2011-07-16
forum: Desktop Environments
---

### Post by Luke M on 2011-07-16
I'm using gnome on ubuntu 11.04. Something that bugs me is how crazy slow pull down menus are. It's really noticeable on an old PC. You move the mouse up and down and the menu selection changes with a large lag.

Is there any fix (besides the obvious - don't use gnome)?

---

### Post by koleoptero on 2011-07-16
> **Luke M said:**
> I'm using gnome on ubuntu 11.04. Something that bugs me is how crazy slow pull down menus are. It's really noticeable on an old PC. You move the mouse up and down and the menu selection changes with a large lag.

Is there any fix (besides the obvious - don't use gnome)?

I've noticed that using a "lighter" gtk theme will improve responsiveness. To verify if that's the case try the "mist" theme that comes preinstalled and see if there's any improvement.

---

### Post by Luke M on 2011-07-16
Thanks for the tip. Actually Mist was not preinstalled; I had to get the gnome-themes package.  Yes, it's better. Not fast, but a definite improvement.

---

### Post by koleoptero on 2011-07-16
> **Luke M said:**
> Thanks for the tip. Actually Mist was not preinstalled; I had to get the gnome-themes package.  Yes, it's better. Not fast, but a definite improvement.

If it's still not as fast as it should be try disabling shadows or transparencies for menus from compiz.

Details:

[LIST=1]
[*]Install compizconfig-settings-manager from the software center or by opening a terminal and typing ```
sudo apt-get install compizconfig-settings-manager
```
[*]Open it from whatever menus you have or by pressing alt+f2 and running "ccsm" without the quotes of course.

[*]Look for the window decoration plugin somewhere in there, click it and on the page it opens, at the line it says "shadow windows" add ```
& !(type=Menu | PopupMenu | DropdownMenu)
```
[*]Then click back and go to the "Opacity, Brightness and Saturation" plugin and make sure there's no rule for the same values as above.
[/LIST]

That's the only thing that I can think of you can do.

---

### Post by Luke M on 2011-07-16
I'm starting ubuntu in classic-no effects mode, so I'm using metacity, not compiz. Is there a configuration tool for metacity? Some of the compiz settings seem to affect metacity, while others don't. Confusing. I would like to disable the annoying window zoom effect.

---

