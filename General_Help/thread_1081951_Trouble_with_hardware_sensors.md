---
title: "Trouble with hardware sensors"
date: 2009-02-27
forum: General Help
---

### Post by sMash! on 2009-02-27
How do I figure out what motherboard my older Toshiba A75 laptop is running? I installed lm-sensors so that my conky could monitor my cpu temps (the Tosh was notoriously a hot runner even under Windblows) but it fails to detect any sensors when i run sensors-detect, and directs me to check the lm-sensors wiki for my board.
Unless someone has an alternative bit of script/applet/program that I should try?

---

### Post by justleen on 2009-02-27
you can use hwmgr to get system info, or lspci

---

### Post by sMash! on 2009-02-27
Thanks, lspci worked for finding the info. Now to find a working script for lm-sensors......

---

