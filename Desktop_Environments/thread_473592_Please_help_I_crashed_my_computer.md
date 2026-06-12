---
title: "Please help I crashed my computer"
date: 2007-06-14
forum: Desktop Environments
---

### Post by glenngds2007 on 2007-06-14
Don't know exactly how I did it and absolutely do not know what is wrong.  When I start my computer normally--just before it gets to the log in screen it just locks up, period.  When I start up recovery mode everything goes well and comes to a terminal that says "root Glenn#" so I typed startx there and gnome started up just fine.  So I logged out and immediately it locked up just before the log on screen.  Tried to check users and groups and the crazy computer would not let me do very much of anything at all. Opened a terminal and immediately saw that I was in a root gnome session--but I have no administrative rights as a root user and that is crazy again.  

Any guesses--any help at all would be appreciated.  I will more than gladly post any files from my computer to help diagnosis the problem.

---

### Post by glenngds2007 on 2007-06-14
I filed a bug report with launchpad over this matter.  Bug number 120403

---

### Post by glenngds2007 on 2007-06-14
After reading the very end of my system log I think I found out what crashed my computer.  The log clearly states that module vmmon tainted the kernel.  Module vmmon is a part of VMware's workstation/player software package.  Be very careful about using any VMware products with Ubuntu 7.04 Feisty Fawn!!!!!!!!!!!!!!!!!!!!!!!!!

---

