---
title: "CPU frequency scaling applet"
date: 2005-12-07
forum: Desktop Environments
---

### Post by toon on 2005-12-07
Hello,

I can't for the life of me figure out how to throttle the CPU in KDE! In gnome I use the battery applet and it works great. How do you do it in KDE?

I've searched around, [http://ubuntuforums.org/showthread.php?t=85621&highlight=cpu+scaling+kde](http://ubuntuforums.org/showthread.php?t=85621&highlight=cpu+scaling+kde) for instance, but it didn't help me..

Thanks.

---

### Post by toon on 2005-12-09
Noones uses this? In gnome it works like a charm, with the gnome-cpu-applet or whatever it was called. This works great; it lets me tune the cpu according to my needs.

I have yet to find a similar applet for KDE. Am I just a complete noob since noone else seems to request this? :(

---

### Post by viz_e on 2005-12-13
I don't use any applet. I have simply installed cpufreqd and cpufreq-utils. After that by typing (in console)

$ cpufreq-info

it tells you the current cpufreq and by

# cpufreq-set -g ondemand

you can change the governor to "ondemand", which give more power when needed. If don't have it, try

# modprobe cpufreq_ondemand (you can also add the module to /etc/modules)

Then you can play a bit with /etc/cpufreqd.conf (or whatever it is called).

I hope it helps.

---

### Post by Zaventh on 2005-12-13
klaptop? Should be included by default...

---

### Post by msak007 on 2006-02-26
My CPU doesn't support frequency scaling so I'm not sure how well it works, but I think [this]("http://www.kde-apps.org/content/show.php?content=35345") might be what you're looking for? It only shows temp and speed on my panel, but from the screenshot it looks like it has the support for scaling the frequency / speed for a CPU that supports it.

---

