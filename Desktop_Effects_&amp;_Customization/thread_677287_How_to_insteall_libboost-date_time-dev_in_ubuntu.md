---
title: "How to insteall libboost-date_time-dev in ubuntu"
date: 2008-01-24
forum: Desktop Effects &amp; Customization
---

### Post by yinglcs2 on 2008-01-24
Hi, 
I am trying to install 'libboost-date_time-dev' in ubuntu 7.10:

When I try it, i get the following error:

$ sudo apt-get install libboost-date_time-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libboost-date_time-dev

Thank you.

---

### Post by stephanwehner on 2008-04-17
Seems to be a typo -- replace _ / underscore by - / dash as in


[SIZE="7"] apt-get install libboost-date-time-dev[/SIZE]


Stephan

---

