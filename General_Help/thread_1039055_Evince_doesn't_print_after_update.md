---
title: "Evince doesn't print after update"
date: 2009-01-14
forum: General Help
---

### Post by bixejo on 2009-01-14
After updating to kernel 2.6.24-23.46 in 8.04, Evince doesn't print PDF files any more. I don't get any problems to print them with Acroread. No problems either to print from other programs like OpenOffice.

Any time I try to print with Evince, it takes 100% of one CPU and does nothing else till I close it. I tried to launch it from a terminal to see whether it issues some error message, but nothing appears.

There is only one line in the file /var/log/cups/access_log that seems to be related to my attempt:

> localhost - - [14/Jan/2009:11:57:15 +0100] "GET /ppd/HP_DobleCara_Dpto.ppd HTTP/1.1" 200 65813 - -
Nothing else in other files in /var/log/cups/*

I'd appreciate any help or suggestion on this. I really love the option of printing two pages per sheet, that seems to be missing in Acroread printing dialog.

Thank you in advance,

***Edit:** "Print preview" shows the same behaviour. 100% of one CPU eaten and nothing else till I close it.*

---

### Post by bixejo on 2009-01-15
Looks like it's a "cairo" issue, not related to Evince nor "cups":

[https://bugs.launchpad.net/ubuntu/+source/evince/+bug/227186](https://bugs.launchpad.net/ubuntu/+source/evince/+bug/227186)

Did Anyone find a way to fix this issue in 8.04?

Thank you in advance,

---

### Post by bixejo on 2009-01-15
Trying to upgrade 8.04 => 8.10 I've been warned that there were no NDIVIA driver wroking on Intrepid, so upgrading to Intrepid is a non-solution to me.

I still appreciate if someone could give me a workaround for this, please.

---

