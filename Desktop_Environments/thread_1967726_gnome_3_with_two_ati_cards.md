---
title: "gnome 3 with two ati cards"
date: 2012-04-28
forum: Desktop Environments
---

### Post by now4 on 2012-04-28
hi

i have a computer with 4 monitors and two ati graphic adapters ( ubuntu 12.04 lts, fresh install ). i didnt install the proprietary ati drivers because that fails. in order to activate both adapters i executed the following command: 

aticonfig --adapter=all --initial

after that i was able to configure all 4 monitors using the Catalyst Control Center and to activate xinemara. everything is fine except that not gnome 3 but gnome classic is running even if i select gnome shell @ the login screen. gnome classic does also load every panel 3 times, so i have 3 clocks, 3 menus, ...


glxinfo ->> [http://pastebin.com/Endfshcb](http://pastebin.com/Endfshcb)
syslog ->> [http://pastebin.com/eSqNprRA](http://pastebin.com/eSqNprRA)
Xorg.failsafe.log ->> [http://pastebin.com/yxcDnQBe](http://pastebin.com/yxcDnQBe)
xorg.conf ->> [http://pastebin.com/7Jp9JqqS](http://pastebin.com/7Jp9JqqS)

screenshot ->> [http://img225.imageshack.us/img225/9454/screenshotfrom201204281.png](http://img225.imageshack.us/img225/9454/screenshotfrom201204281.png)

can someone help me to get gnome 3 running ( it worked as long i didnt use both adapters )?

---

