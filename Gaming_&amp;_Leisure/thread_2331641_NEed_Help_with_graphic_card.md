---
title: "NEed Help with graphic card"
date: 2016-07-24
forum: Gaming &amp; Leisure
---

### Post by tiago16++ on 2016-07-24
Hello guys, i'm a little newbie in ubuntu, actually i'm using Xubuntu distro, xubuntu 16.04 Xenial, and i can't install drivers for graphic card, i'm using laptop asus, and i have ATI MObility Radeon HD 5730 Graphics, you have any sugestion? 
[h=3][/h]

---

### Post by TheFu on 2016-07-24
Welcome to the forums.

Thought older Radeon support by AMD was dropped last year or the year before that. That means you have to use the F/LOSS drivers with 16.04. It should be possible to load 14.04.5 and load older Radeon drivers, but I wouldn't and many of the GUI applications don't have support anymore under 14.04 (use **ubuntu-support-status** to see how bad it really is on your system).  System stability is more important than gaming to me.  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) has more information.

---

### Post by mastablasta on 2016-07-25
chip is supported by 14.04 version with fglrx drivers.
on 16.04 only rdeonopensource driver is available . for now at least. this may change later in the year, however it will probably still not support the chip you have.


i have similar issue with 6xxx series. i know for sure that on laptop Radeon drains a lot more power, heats up more and mkaes the fans run louder than fglrx. System and hardware stability over gaming would suggest to install fglrx on 14.04 even for office work.

---

