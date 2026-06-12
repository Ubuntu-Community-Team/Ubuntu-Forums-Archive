---
title: "Screen Resolution problem .... new to linux"
date: 2008-08-25
forum: Gaming &amp; Leisure
---

### Post by its_jon on 2008-08-25
I installed Quake Arena, set the rez to a setting that blanked the screen.....

Had to reboot as no way to get out or back ..... uninstalled quake, installed Alien Arena .... on first start the screen rez was also blanked and I had to reboot....

I guess both games are sharing a setting somewhere that has not been reset ????

Im new :)

whats went wrong and how do I fix it .... many thanks
john
scotland

---

### Post by eragon100 on 2008-08-26
open a terminal and type in:

sudo displayconfig-gtk

enter password (it is not supposed to show asterisks)

In the box that appears, your monitor will  be identified as "Generic Monitor". Click on that word and select your monitor make and model.

Select the highest refresh rate it offers that gives a good view, even if it looks "strange" (like 64 Hz). Confirm that you want to keep it.

logout, login, and be happy because the problem should be solved now! :wink:

(if it turns out to be another problem, feel free to ask for more help, offcourse :))

---

