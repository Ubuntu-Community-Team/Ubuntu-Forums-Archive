---
title: "Disable login drums!"
date: 2011-05-12
forum: Desktop Environments
---

### Post by GlennW on 2011-05-12
It appears that a lot of us have had to struggle with the fact that the usual disable login sounds from drop down menus will not prevent those funky drums from blasting their beat at login.

After searching for days, I found this bit of code. Open a terminal and enter: ```
sudo -u gdm gconftool-2 --type=bool --set /desktop/gnome/sound/event_sounds false
```
This has worked for me on both my laptop and my desktop boxes. 

I will mark it solved.

---

