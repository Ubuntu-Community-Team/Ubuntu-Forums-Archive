---
title: "Toshiba P105-S6024 problems with Jaunty"
date: 2009-05-03
forum: General Help
---

### Post by pvhoward on 2009-05-03
everything is running fine except desktop animations aren't running as smoothly as they should. I know its not a big deal, but it is annoying. Opening and closing/minimizing windows isn't nearly as smooth as it should be. I believe it to be a problem with the graphics drivers, but i'm not sure. Anyone have a similar problem and a solution? Thanks

---

### Post by tjwoosta on 2009-05-03
it most likely is a graphics driver issue

what graphics card do you have?

---

### Post by pvhoward on 2009-05-03
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

I believe that is it

thats what I get when i type lspci into the terminal

---

### Post by tjwoosta on 2009-05-03
yep, thats the problem

i also have intel graphics


the problem is that the newer intel graphics drivers performance has regressed

what happened is that a while back intel released a bunch of new information about how the hardware works

ever since then linux devs have been hard at work trying to incorperate this new information (mainly GEM and UXA)

[http://www.phoronix.com/scan.php?page=news_item&px=NjUyMQ]("http://www.phoronix.com/scan.php?page=news_item&px=NjUyMQ")

[http://www.phoronix.com/scan.php?page=article&item=intel_uxa&num=1]("http://www.phoronix.com/scan.php?page=article&item=intel_uxa&num=1")

when they are done performance will be far better then before, but for now we are dealing with much regression although i have heard its getting better with the latest releases

i know in arch its easy to downgrade to the old (more stable) version of intel drivers while keeping the new xorg-server but im not sure how easy it is in ubuntu or if its even possable

EDIT:

i just found this thread that might help, but i havn't tried it myself

[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by pvhoward on 2009-05-03
hey thanks man...

---

