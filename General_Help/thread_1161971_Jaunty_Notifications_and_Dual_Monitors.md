---
title: "Jaunty Notifications and Dual Monitors"
date: 2009-05-17
forum: General Help
---

### Post by osarusan on 2009-05-17
Hi,

I have a TwinView monitor setup and recently something happened with my Notifications so that they display on the secondary monitor rather than the primary. This is annoying, because now they appear in the center of my Twinview environment rather than in the right corner. Is there any way to change this setting?

---

### Post by Joeb454 on 2009-05-17
Have you changed any settings recently? Either with notify-osd or your TwinView setup?

---

### Post by osarusan on 2009-05-17
I had been changing around my TwinView settings, but changing them back doesn't cause the notifications to return to the primary monitor.

---

### Post by Joeb454 on 2009-05-17
I assume it places the notifications on the top right of your monitor still, but the left-most monitor?

If so it sounds like your primary monitor settings are incorrect, and Ubuntu is seeing your left monitor as the primary monitor, rather than the right monitor

---

### Post by osarusan on 2009-05-17
Well I just figured something out about it... I had added a panel to the monitor, and that seems to be what caused the problem.

After deleting the panel, the notifications flip back to the other monitor. Strange... and kind of a bummer. I'd like to be able to have a top panel on that screen.

---

