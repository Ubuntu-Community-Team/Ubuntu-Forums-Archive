---
title: "ET Punkbuster"
date: 2006-06-17
forum: Gaming &amp; Leisure
---

### Post by jISh on 2006-06-17
I CANNOT get this to work. I've tried running as sudo, gksudo, modifying the shell scrpt, chmodding the folders, write-protecting the config file, everything.

Wtf? How do people manage to enable this? :(

---

### Post by markmark on 2006-06-19
[QUOTE=jISh]I CANNOT get this to work. I've tried running as sudo, gksudo, modifying the shell scrpt, chmodding the folders, write-protecting the config file, everything.

Wtf? How do people manage to enable this? :([/QUOTE]
This happened to me, I seem to remember the problem was that if you install with sudo it creates your settings directoy (~/.etwolf) with root as the owner. Try doing```
sudo chown -R username:username ~/.etwolf
```Replacing username with your username obviously.

The other thing to try with PB is to manually update it using the stuff on the punkbuster website.

---

