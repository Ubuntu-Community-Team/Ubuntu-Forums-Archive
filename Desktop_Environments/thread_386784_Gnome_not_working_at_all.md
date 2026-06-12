---
title: "Gnome not working at all"
date: 2007-03-17
forum: Desktop Environments
---

### Post by profXavier on 2007-03-17
Recently, I added KDE into my ubuntu release.  I have been switching back and forth between the two daily.  But in the past day, I have found that I am not able to get into Gnome.  I have changed lots of settings, constantly, so it is difficult to pin point what I feel the issue is. And that is why I am asking for your help.

What can I do (from my login menu) to troubleshoot what is happening in Gnome, as I am logging in? From the login menu, I just get a background, no icons, no menus, nothing.  I know that I can utilize ctrl-alt-f* keys, to leave from X, but no sure if thats the best solution. Then maybe I can check some log file?

Please post any questions/concerns/comments, as I will be working on this throughout the day.

profX

---

### Post by ardchoille42 on 2007-03-17
> **profXavier said:**
> Recently, I added KDE into my ubuntu release.  I have been switching back and forth between the two daily.  But in the past day, I have found that I am not able to get into Gnome.  I have changed lots of settings, constantly, so it is difficult to pin point what I feel the issue is. And that is why I am asking for your help.

What can I do (from my login menu) to troubleshoot what is happening in Gnome, as I am logging in? From the login menu, I just get a background, no icons, no menus, nothing.  I know that I can utilize ctrl-alt-f* keys, to leave from X, but no sure if thats the best solution. Then maybe I can check some log file?

Please post any questions/concerns/comments, as I will be working on this throughout the day.

profX

Nautilus is responsible for drawing the background, managing the desktop icons and the desktop right click menu. When you log in, try and do ALT+F2, if that gives you a Run Application dialog, type in nautilus and click the 'Run" button to start nautilus. If your desktop icons and wallpaper appear, the problem may be that nautilus isn't starting up normally when you log in, as it should. If that all goes well, try running 'gnome-panel', without quotes, and see what happens.

---

