---
title: "Menus no longer showing in gnome"
date: 2007-11-26
forum: Desktop Environments
---

### Post by ghstridr on 2007-11-26
:confused:
I don't know if it happened because of an update or not.
Suddenly, after leaving the laptop off for a week, when I log in, neither of the strips at the top or the bottom are showing up now.  What process do these run as?  I'd like to check the ps output to see if they are running.
When I log in to failsafe gnome, they come back.
Follow up: Upon second thought, something might be corrupt in one of the '.' config directories that gnome uses upon login.  I'm also noting that compiz isn't running when using the failsafe gnome session.

---

### Post by qqzhenyi on 2007-11-26
maybe you want to try something like:
killall gnome-panel

---

### Post by ghstridr on 2007-11-26
> **qqzhenyi said:**
> maybe you want to try something like:
killall gnome-panel
Thank you! I was trying to remember the process name for the panels.
It wasn't running at all.  Just restarted it.
I've noticed that ever since i've moved to 7.10 that there have been some new errors.
Things like the gnome-panel not starting and the gnome-preferences (I think that is what it is called) not starting.  They seem to be failing while compiz is starting.

---

