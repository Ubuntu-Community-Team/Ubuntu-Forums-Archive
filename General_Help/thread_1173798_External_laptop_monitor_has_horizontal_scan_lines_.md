---
title: "External laptop monitor has horizontal scan lines in Ubuntu but not in XP."
date: 2009-05-30
forum: General Help
---

### Post by matthew1471 on 2009-05-30
When I use an external 19" widescreen monitor with my Dell 1501 (Jaunty), I get very fine horizontal scan lines and flickering.

When it's set to 1440x900 75hz the scan lines are really noticeable [bad enough to not use the monitor] , if I set it to 60hz, the scan lines are less noticeable [still bad enough to not use the monitor].

If I dual boot into XP, the monitor is absolutely fine and useable at both settings.

The laptop has a ATI 200m integrated card, so I'm wondering if it's to do with having the open-source drivers [since ATI stopped supporting 200m in Catalyst :( ].

Has anyone got any ideas or pointers [or fixes!] before I install Ibex to see if the same happens with the Catalyst drivers?

---

### Post by QIII on 2009-05-30
What do you see in System -> Administration -> Hardware Drivers?

---

### Post by matthew1471 on 2009-05-30
The Broadcom wireless network driver.

I'm sure there used to be the option to install an ATI driver when I was using Ibex.

---

### Post by QIII on 2009-05-30
Hmmm...

I realized something.

Your screen on the laptop is working swimmingly, right?

This may be somewhat along the lines of a solution.  Take a look at the second post.  You may have to modify your xorg.conf to fiddle with the characteristics of your second screen.

[http://ubuntuforums.org/archive/index.php/t-21600.html](http://ubuntuforums.org/archive/index.php/t-21600.html)

---

