---
title: "[SOLVED] Removing Every Panel?"
date: 2008-02-27
forum: Desktop Environments
---

### Post by phynix on 2008-02-27
Gnome will not allow me to remove the final panel, and I wondered if there is a way other than autohiding it because it still comes up every once in awhile. thanks.

---

### Post by nanotube on 2008-02-27
refer to this thread, there are a few possible solutions offered:
[http://ubuntuforums.org/archive/index.php/t-594729.html](http://ubuntuforums.org/archive/index.php/t-594729.html)

---

### Post by phynix on 2008-02-28
Thank You this worked like a charm from the link above:

Open gconf and goto /apps/panel/toplevels and set these values:
auto_hide: yes
auto_hide_size: 1
expand: no
hide_delay: 1
monitor: 3
unhide_delay: 10000
x: 10000
y: 10000

---

### Post by nanotube on 2008-02-28
> **phynix said:**
> Thank You this worked like a charm from the link above:

Open gconf and goto /apps/panel/toplevels and set these values:
auto_hide: yes
auto_hide_size: 1
expand: no
hide_delay: 1
monitor: 3
unhide_delay: 10000
x: 10000
y: 10000

excellent! thanks for sharing your final solution :)

---

### Post by SunnyRabbiera on 2008-02-28
what are you using a terminal only or something?

---

### Post by PurposeOfReason on 2008-02-28
> **SunnyRabbiera said:**
> what are you using a terminal only or something?
Why would that matter? He could, like me, just alt+tab through everything.

---

### Post by Nythain on 2008-02-28
or he could have decided that AWN is much prettier and will accomplish near the same thing

oh yeah, thanks for the solutions... been trying to find a way other than a "standard" autohide to get that thing as gone as possible

---

### Post by phynix on 2008-02-28
If you guys are wondering why I want to know. I use awn and have three icons. I don't have any panals now thanks to the guide. I use gnome-do to launch anything I don't have such as preferences and random apps. The next step will be to make one of my extra buttons do the menu like xfce. I just really like a simple desktop. Tell me what you think and if any one wants to see what it looks like i will be happy to post a screen shot.

---

### Post by Nythain on 2008-02-28
yeah, after discovering AWN i pretty much just wanted to nix the gnome panel myself... and coming from a fluxbox environment, panels arent all that usefull to me anymore :)...

if you want, you can post a screen shot in the Community Cafe, there's a sticky for Feb Desktop screenshots

---

### Post by phynix on 2008-02-29
Ok its up. post number 27. Tell me what you think.

---

