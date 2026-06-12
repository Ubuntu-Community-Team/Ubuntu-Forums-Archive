---
title: "GDM fails to load!"
date: 2006-08-19
forum: Desktop Environments
---

### Post by yojdork on 2006-08-19
Hi,

I've got a fresh install of Dapper with all the updates, and GDM fails to load about 3/4 of the time.  It goes through everything on the usplash and then it seems like it attempts to start GDM and it just hangs there with a black screen.  I've left it for more than 20 mins and it doesn't change.  I also don't hear a sound like GDM has started.  I thought maybe it was vid. driver related so I installed fglrx driver, but no luck.  So I did a dpkg reconfigure for my xserver and went to an older kernel , 2.6.15-23-386.  Still no luck.  1/4 of the time everything works just swell.  It plows on through and loads up GDM.  This is the second time I've installed Dapper on this computer and it has been happening to me both times.  Any suggestions??  Thanks.

---

### Post by yojdork on 2006-08-20
It seems I was getting quite a bit of "...too much work for irq..." in my syslog.  So adding "acpi=noirq" to my boot parameters seems to do the trick.

---

