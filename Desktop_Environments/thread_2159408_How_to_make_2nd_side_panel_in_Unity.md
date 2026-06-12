---
title: "How to make 2nd side panel in Unity?"
date: 2013-07-03
forum: Desktop Environments
---

### Post by anpalcactus on 2013-07-03
Hey guys!
So I have 12.04LTS with left panel which is auto-hiding. I want one more panel on bottom which shouldn't auto-hide and thus i could place all my usable shortcuts there while running programs would show in the left one

Is there a way?
Some program, maybe?

---

### Post by Dozy Van on 2013-07-03
does this still work?

[http://pietervogelaar.nl/ubuntu-11-04-add-bottom-panel-to-unity](http://pietervogelaar.nl/ubuntu-11-04-add-bottom-panel-to-unity)

---

### Post by anpalcactus on 2013-07-03
It works but the other way than i want :C
It adds a bottom panel which looks like Start in windows and shows opened windows. i want the panel pinned to desktop which wouldnt hide and show me just shortcuts

---

### Post by fooman on 2013-07-03
i just installed cairo-dock (its in the repos) and that seems to work pretty well with unity.
 here is a screenshot of it running on my sysytem:

---

### Post by buzzingrobot on 2013-07-03
The Plank dock works well on Ubuntu and can be positioned to any side of the screen.

---

### Post by kurt18947 on 2013-07-03
You could look at tint2 panel as well, it's in the repositories.  I use it in conjunction with gnome-shell, I find it better for switching between windows and apps than gnome-shell's native method.  It works with unity too I believe.  You need to configure it via a hidden .config file.  I remove the clock for instance.

---

### Post by stinkeye on 2013-07-03
> **anpalcactus said:**
> Hey guys!
So I have 12.04LTS with left panel which is auto-hiding. I want one more panel on bottom which shouldn't auto-hide and thus i could place all my usable shortcuts there while running programs would show in the left one

Is there a way?
Some program, maybe?
Just use gnome-panel.
Use Super+alt+Right-click for customizing.

Super+alt+Right-click on panel and create new panel at the bottom if one is not shown.
Remove the top panel.
Remove unwanted items from the panel.
Drag n drop shortcuts from the dash to the panel.

---

### Post by anpalcactus on 2013-07-04
> **fooman said:**
> i just installed cairo-dock (its in the repos) and that seems to work pretty well with unity.
 here is a screenshot of it running on my sysytem:
Thank you so much!
I installed this panel and it does satisfy me in all the ways :)
Topic is now marked as [SOLVED]

---

