---
title: "Speedstep like applet in ubuntu?"
date: 2005-06-16
forum: Desktop Environments
---

### Post by holr on 2005-06-16
Hi!
   I have, in my best efforts read many articles already on speedstep with centrino (pentium-m) processors and the magic known as speedstepping. What I am trying to do is get an applet / application that will allow me to change the cpu's speed and keep it at that speed e.g. when Im working on batteries I would like to change the cpu down to 600mhz and keep it like that (i.e. not increase to 1.7gig when something demands it).

   I have read a lot about powernowd, I believe this is up and running on my system, as when I am using cpu-monitoring applets they do say Im running at 600mhz when its quiet, but then shoots back up to 1.7gig when im running something more intensive.

   I also tried something called cpufreqd but without much luck!

   I did find an applet installed by default (when you right click on the gnome-panel area) called something like "cpu frequency monitor" and reading the help in that suggests that the tool can let you change the speed of your cpu permanently, but when I click on it, no drop down menu appears to do this. This applet does report my cpu speed changing from 600 to 1.7 when im running intense apps though.

   So what im trying to do is keep the cpu running at a certain frequency. It already does go up and down depending on the need, but I would like it to run slow and stay slow when on the batteries!

   Hope someone can give me some advice!

Huw

---

### Post by holr on 2005-06-16
[QUOTE=holr]Hi!
   I have, in my best efforts read many articles already on speedstep with centrino (pentium-m) processors and the magic known as speedstepping. What I am trying to do is get an applet / application that will allow me to change the cpu's speed and keep it at that speed e.g. when Im working on batteries I would like to change the cpu down to 600mhz and keep it like that (i.e. not increase to 1.7gig when something demands it).

   I have read a lot about powernowd, I believe this is up and running on my system, as when I am using cpu-monitoring applets they do say Im running at 600mhz when its quiet, but then shoots back up to 1.7gig when im running something more intensive.

   I also tried something called cpufreqd but without much luck!

   I did find an applet installed by default (when you right click on the gnome-panel area) called something like "cpu frequency monitor" and reading the help in that suggests that the tool can let you change the speed of your cpu permanently, but when I click on it, no drop down menu appears to do this. This applet does report my cpu speed changing from 600 to 1.7 when im running intense apps though.

   So what im trying to do is keep the cpu running at a certain frequency. It already does go up and down depending on the need, but I would like it to run slow and stay slow when on the batteries!

   Hope someone can give me some advice!

Huw[/QUOTE]
 any ideas, anyone? Help much appreciated!!

---

### Post by sbassett on 2005-06-16
Holr, you may want to take a look here:
[http://linux.com.hk/PenguinWeb/manpage.jsp?name=cpufreqd.conf&section=5](http://linux.com.hk/PenguinWeb/manpage.jsp?name=cpufreqd.conf&section=5)

It even shows some good examples. I believe this will give you what you are looking for as you can setup different profiles, such as "plugged in" or "battery" and it allows you to setup the maximum frequency of the chip.

---

### Post by holr on 2005-08-11
[QUOTE=sbassett]Holr, you may want to take a look here:
[http://linux.com.hk/PenguinWeb/manpage.jsp?name=cpufreqd.conf&section=5](http://linux.com.hk/PenguinWeb/manpage.jsp?name=cpufreqd.conf&section=5)

It even shows some good examples. I believe this will give you what you are looking for as you can setup different profiles, such as "plugged in" or "battery" and it allows you to setup the maximum frequency of the chip.[/QUOTE]
 Found emifreq , this is exactly what i was looking for!

---

