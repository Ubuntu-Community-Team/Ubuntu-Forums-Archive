---
title: "re isntallment of ubuntu"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by StevenEpic on 2007-08-16
i installed ubuntu lastnight hoping to have some good effects, cause i heard it came with ubuntu. someone told me that i needed to install ati drivers and stuff so i did. then its started having problems like, composite extension not available. i cant seem to fix it and no one in this forum has offered to help me out. is there a way to re install ubuntu, the whole /, /home, and swap areaas? i want to start from scratch because i am getting very frustrated looking around the web and not finding what i need.

---

### Post by sdowney717 on 2007-08-16
easiest way to get driver working is by using ENVY program

You have to use the XGL desktop with ATI cards and compiz -- fusion
you have to edit some files to make it work.

[https://help.ubuntu.com/community/Beryl/ATI/Feisty](https://help.ubuntu.com/community/Beryl/ATI/Feisty)

you can ignore the beryl stuff, you realy want compiz-fusion which is beryl and compiz come together again.

setup XGL, then when you reboot select the XGL session from left corner options.

use synaptic to install compiz, emerald and themes

to run compiz -fusion type compiz --replace
to run emerald themes, type emerald --replace

run emerald theme manager, select your theme, then in terminal run emerald --replace to change the desktop.
why they dont have an apply button is beyond me.


or 
compiz --replace -c emerald

---

