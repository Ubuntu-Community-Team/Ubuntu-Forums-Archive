---
title: "Ubuntu 18.04 Gnome shell screen power saving"
date: 2018-05-24
forum: Desktop Environments
---

### Post by rklauco on 2018-05-24
Hi, all.

I have a bit of a problem.
I have ubuntu 18.04 with Gnome shell installed.
When I let the computer alone, the DPMS power saving kicks in and turns off the monitor.
The problem is, after wakeup, instead of showing desktop, there is some "welcome" screen displaying time and waiting for me to press Enter.
I would like to get rid of it - the screen has extremely short timeout settings and my monitor is too slow in waking up, therefore the screen usually just sends the monitor back to sleep before it manages to even show it...
Can someone, please, advise how to do it?
I have already disabled password lock after wake up and similar settings, but it seems to have no impact and the screen is persistent.

---

### Post by rklauco on 2018-05-29
Really? Nobody else is bothered by this "feature"?

---

### Post by kerry_s on 2018-05-29
dconf-editor-> lockdown-> disable screen-lock

[ATTACH=CONFIG]279920[/ATTACH]

---

