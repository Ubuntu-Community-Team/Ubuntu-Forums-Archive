---
title: "Very high CPU usage upon AC adapter plugged in"
date: 2012-03-06
forum: Desktop Environments
---

### Post by xizzling on 2012-03-06
I have a new install of 11.10 32-bit with gnome classic on a brand new thinkpad L520, Sandybridge Core i5, 4GB RAM, 


Observation 1:

I was browsing through chrome when my system seemed to be seriously lagging, so I killed chrome to see if it gets any faster. But there remained no difference. Notice that CPU usage was a bit strange here. It showed no high activity, but as soon as I would click on applications in gnome panel, it would shoot CPU usage to 70, or 80 or 90 or 143% etc. depending on how quickly i clicked back and forth. At this instance I removed by AC adapter of my laptop, and suddenly system got fine. So i again clicked on gnome panel, and noticed that it now took only 7% or 12% or 13% at max, with same kind of clicks in application menu.

Observation 2:

At the other times, with AC adapter plugged in, top indicates four instances of chromium taking 90%, 60%, 47% and 2% (for example), and then once I take out the AC adapter same processes take lesser CPU all of a sudden

Intermediate conclusions: 

What does this indicate ? I cannot figure out any "other" process in "top" that is suddenly being triggered. Infact it is the same process that hogs up my CPU once AC power is plugged in !

NOTE: the problem is now CONFIRMED, as i can recreate it whenever I have power adapter plugged in !

Looking eagerly for debugging help to get going with ubuntu 11.10

---

### Post by winh8r on 2012-03-06
In that case I would suspect the ac adaptor is faulty. If possible (and i know this might not be easy) borrow another adaptor of the same spec/type and try it with your laptop.

If the problem does not occur with an alternative adaptor then it is most likely that your ac adaptor is faulty.

Unlikely to be a fault with Ubuntu if it goes away when you unplug the ac adaptor.

---

### Post by xizzling on 2012-03-14
I tried another brand new adapter but the problem remains as is !

Please note that as soon as i plug in adapter, slowly the same processes (e.g. chrome, acroread etc. that i usually use) start increasing the cpu usage. So a normal chrome process with 10% cpu usage slowly touches 90% or so. And then everything is choked, until i remove the ac adapter. As soon as I remove it everything gets fine and CPU usage drops back to 9% - 12% for chrome (for example).

Please see the two files which were captured during "top" with choked system :(

---

