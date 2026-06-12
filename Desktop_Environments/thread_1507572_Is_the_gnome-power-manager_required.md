---
title: "Is the gnome-power-manager required?"
date: 2010-06-11
forum: Desktop Environments
---

### Post by SIGTERMer on 2010-06-11
Hello everyone,

Is the gnome-power-manager required for a stable gnome environment? or, to rephrase my question, what are the tasks that this daemon handles?

I intend to remove this and any other useless process to free up memory (it take up roughly 30MB). it seems that even 1GB RAM doesn't cut it anymore. so any side advice you can give on this issue would be appreciated. 

Thank you.

---

### Post by JustinR on 2010-06-11
My Ubuntu installation only uses 384MB of ram at normal use so I don't know how only 1GB is cutting it. And Gnome will not start without Gnome-Power-Manager. If you succeed in getting it off your system I'm not sure if there is a way to put it back correctly without reinstalling your system. Feel free to tell us otherwise if it works with you.

---

### Post by SIGTERMer on 2010-06-12
> **JustinR said:**
> My Ubuntu installation only uses 384MB of ram at normal use so I don't know how only 1GB is cutting it. And Gnome will not start without Gnome-Power-Manager. If you succeed in getting it off your system I'm not sure if there is a way to put it back correctly without reinstalling your system. Feel free to tell us otherwise if it works with you.

I killed it, removed it from "strat up" list, did a reboot, then left the system running for about 6 hours. it seems that gnome-power-manager not a integral part of the gnome desktop! 30MBs free :)

From what i observed so far, the power-manager is in charge of dimming/turning off the screen (inactivity, or when on battery power), and displaying battery status. it also handles the actions taken when a laptop is folded. This is not a problem for me since there are many other ways of getting battery information.

About the 1GB issue, it's just weird :|
I use my system for development work, and usually have at least two browsers running at once (most of the ram gets wasted here). I also use thunder-bird which also eats its share of memory. along with gedit and a couple of terminals opened, the systems slows down to a crawl (too much swapping). that's why i'm hunting for useless processes (i didn't even install the update manager).

Any other information regarding useless daemons/processes will be appreciated!

---

### Post by jvin248 on 2011-09-28
Good to know the gnome-power-manager can be removed.

I have a runaway gpm that is using 56% of all ram (listed in htop).

Killing it now.  Maybe remove it from startup as suggested above too.

There are some references to bugs/memory leaks in gpm that I saw on search.

---

