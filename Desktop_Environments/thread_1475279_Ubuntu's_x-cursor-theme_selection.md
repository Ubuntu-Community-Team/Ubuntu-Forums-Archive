---
title: "Ubuntu's x-cursor-theme selection"
date: 2010-05-06
forum: Desktop Environments
---

### Post by mathfeel on 2010-05-06
I just apt-get comixcursor X cursor theme and set it to the small green one using gnome-appearance-properties.  However, I found that it uses the one I set to only appearance when it's over some apps and use the HUGE black one over everything else (e.g. when over the GNOME panel or desktop).

I took me a while a figure out what's going on. Apparently, what I need to do is to run:
```
sudo update-alternatives --config x-cursor-theme
```
and set the symbolic link to the desired one.  And I have to run it using sudo.

Is this the way Ubuntu is suppose to behave or something is wrong with my config?

---

