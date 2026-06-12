---
title: "Printing problem: HP C7280"
date: 2009-04-30
forum: General Help
---

### Post by Timtro on 2009-04-30
Hi all,

Thanks in advance.

I upgraded to 9.04 from 8.04 about a week ago (fresh format and install), and love it. Today I tried to print for the first time in 9.04. I apt-get all of the hp-stuff, set up the (wireless network) printer and all went well. I can get all of the information I need, it says its idle, give my my ink levels etc.

When I try to print however, only a few pages come out. When I print in draft mode, I get one page (one side on double sided print). When I run it in regular mode, I get 2 pages (3 sides in double sided print). The HP device manager is reporting that the print job is done, and the LCD on the printer agrees. The document print status window reports each job as 'stopped'.

Can anyone suggest some trouble shooting strategy?

Thanks a bunch,


Tim.

---

### Post by cmnorton on 2009-04-30
Start by looking in the logs under /var/log/cups. You might get a hint there.

If you set this printer up before the upgrade, try updating the printer to reload the driver. It's a bit of a shotgun approach, I'll admit. 

Also, try getting a driver for the printer (Linux) from HP or try a generic driver.

---

### Post by Timtro on 2009-05-04
> **cmnorton said:**
> Start by looking in the logs under /var/log/cups. You might get a hint there.

If you set this printer up before the upgrade, try updating the printer to reload the driver. It's a bit of a shotgun approach, I'll admit. 

Also, try getting a driver for the printer (Linux) from HP or try a generic driver.

Thanks, I'll try this in a bit and let you know. Sorry for the late reply. Thanks so much for your help.

---

