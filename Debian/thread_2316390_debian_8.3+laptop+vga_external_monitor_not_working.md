---
title: "debian 8.3+laptop+vga external monitor not working on bootup"
date: 2016-03-07
forum: Debian
---

### Post by bdubawoop on 2016-03-07
thought id try this here as no luck on debian forum

thinkpad edge e550 laptop with debian 8.3, ubuntu 14.04 & win7 (also tried mint but it dont get along with my thinkpad at all).

im trying to hook up my acer 22" inch monitor thru the vga out of the laptop (just clone it).

when i boot i get black screen on laptop & gray with mouse cursor (mouse does nothing but move around) on the acer.

i found if i go to any console both monitors come up & i can startx to desktop with no trouble.

i tried putting a file for monitors in /use/share/X11/xorg.conf.d but it was a bust, not sure whatall to put in there but ive a suspicion if i can just get the right sections & lines in a conf file there it will come up..

by the way, of the 3 linux's ive put on the thinkpad, ubuntu is the only 1 without problems. but this monitor not working in debian is bugging me, especially as it works out of the box with ubuntu.

any ideas?

---

### Post by bdubawoop on 2016-03-10
update: mint is also working well now, had to drop down to fglrx driver.

debian still refuses to work with ext monitor at bootup. im currently trying an install of debian testing.

---

### Post by bdubawoop on 2016-03-10
solved problem by installing debian testing

---

