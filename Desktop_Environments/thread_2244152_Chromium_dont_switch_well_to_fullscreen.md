---
title: "Chromium dont switch well to fullscreen"
date: 2014-09-14
forum: Desktop Environments
---

### Post by z-me-x on 2014-09-14
After last update, Chromium will not go well into fullscreen mode with F11. I must go over the menu of browser to get the browser in fullscreen mode. The header bar with tabs stay always there, if i do not the workaround with mouse clicks.

I have uninstalled and installed again, delete all config folders of chromium and cache. But no luck. Anyone else with the same problem out there?

---

### Post by Rob Sayer on 2014-09-14
I found chromium very problematic in lubuntu 14.04 on my netbook ... one of the reasons I installed xubuntu 14.04 instead.  Chrome worked better.

Chromium isn't as well supported as Chrome, which also has better up to date flash support.  Unless you're an open source zealot I cannot see any reason not to use Chrome.  It just works better.

---

### Post by z-me-x on 2014-09-14
I use it on an ARM based board with Lubuntu on it. Chromium is there the main browser.

---

### Post by Georgi_Mirchev on 2015-04-22
The problem is that the F11 key is taken from the system to make the curernt focused window fullscreen. You can see it here: [https://help.ubuntu.com/community/Lubuntu/Keyboard](https://help.ubuntu.com/community/Lubuntu/Keyboard)
So just go to ~/.config/openbox , backup the lubuntu-rc.xml file and edit the original one replacing the F11 shortcut for toggle fullscreen with F10 for example. 
Logout and login again and now when you press F11 in chrome or chromium it will go fullscreen, instead of using the default system shortcut.

---

