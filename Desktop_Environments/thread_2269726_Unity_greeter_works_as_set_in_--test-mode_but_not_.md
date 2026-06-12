---
title: "Unity greeter works as set in --test-mode but not at login"
date: 2015-03-17
forum: Desktop Environments
---

### Post by ryncops on 2015-03-17
Hi! I wanted to change my background on the unity greeter and I think I bugged it up. I tried ubuntu tweak, dconfig and throught the terminal with gsettings . None made my login screen work. It does work though when I use --test-mode on it. Over there it works great, but when i usually open my pc I get a purple screen and the dotted grid. What should I do? I tried reinstalling unity-greeter and ubuntu-desktop. It didnt fix it.

---

### Post by dino99 on 2015-03-18
sudo apt-get purge unity-greeter
sudo apt-get install unity-greeter

---

