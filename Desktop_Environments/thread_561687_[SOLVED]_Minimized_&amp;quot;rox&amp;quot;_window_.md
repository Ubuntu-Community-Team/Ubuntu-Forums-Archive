---
title: "[SOLVED] Minimized &amp;quot;rox&amp;quot; window flashes when IceWM loads"
date: 2007-09-27
forum: Desktop Environments
---

### Post by BuilderQ on 2007-09-27
I use IceWM, with ROX-filer to handle the desktop. Therefore, I have a "startup" file in my ~/.icewm folder, containing this command: "rox --p=1 &". This works as expected, except for a minor annoyance: when IceWM loads, a minimized window labelled "rox" is flashing in the taskbar. Clicking on "rox" makes it disappear, but I'd like a way to stop it showing up. Googling my problem, I found what I think is the same issue mentioned at [http://www.nabble.com/--icewm-Bugs-1646042---rox---flashing-tab-in-taskbar-t4155520.html](http://www.nabble.com/--icewm-Bugs-1646042---rox---flashing-tab-in-taskbar-t4155520.html), but no solution.

---

### Post by kerry_s on 2007-09-27
what happens if you use the long 1?
**rox --pinboard Default &**

isn't it suppose to be 1 dash?
**rox -p=1 &**

---

### Post by BuilderQ on 2007-09-27
Thanks for the reply.

> **kerry_s said:**
> what happens if you use the long 1?
**rox --pinboard Default &**
The same as before happens (except of course I don't see the icons that were on my desktop). I'm not quite sure what the difference between p and pinboard is.
> **kerry_s said:**
> 
isn't it suppose to be 1 dash?
**rox -p=1 &**

-p seems to work the same as --p

I should add that running any of these commands from the terminal also produces the flashing rox window. What else can I try?

---

### Post by kerry_s on 2007-09-28
what do you have for the compatibility option's?

i don't remember it doing that when i was running icewm and rox. i've since switched all my computers to xfce4 as it uses the same amount of resources as a full icewm setup, but is alot easier to work with xfce4.

---

### Post by BuilderQ on 2007-09-28
> **kerry_s said:**
> what do you have for the compatibility option's?
Ah ha! Thanks for pointing me in this direction; checking "Override window manager control of the pinboard and panels" corrects this problem. > **kerry_s said:**
> i don't remember it doing that when i was running icewm and rox. i've since switched all my computers to xfce4 as it uses the same amount of resources as a full icewm setup, but is alot easier to work with xfce4. I've tried xfce4 (indeed, since I'm running Xubuntu, I started with it), but I find IceWM is faster (at least when first loading).

---

