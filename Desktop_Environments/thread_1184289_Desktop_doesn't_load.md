---
title: "Desktop doesn't load"
date: 2009-06-11
forum: Desktop Environments
---

### Post by micah on 2009-06-11
I recently updated my Xubuntu 8.10 desktop machine through the update manager. After the updates were applied my desktop crashed. It turned a pale blue color. I still had use of my mouse and hotkeys, but the menu/panel at the top and bottom were gone along with all the icons on my desktop. I could hit F2 and programs from there.  All programs worked fine. 

Instead of messing around with it i just decided up update to Xubuntu 9.4 (Jaunty). After loading it on the machine everything looked fine. After the first reboot though the same thing happened. All icons from my desktop were gone along with the top and bottom panels. The mouse still works and i can launch any from Run Program (F2). So its something wrong with my desktop. 

I reverted to 8.4 (Hardy) and its working fine (and a good bit slower).  So whats wrong?  Any ideas? I'm very new to linux, so any feedback will be appreciated. Especially if it walks me through stuff that isn't GUI based.

Thanks ahead of time!

EDIT: I found the solution:
[http://ubuntuforums.org/showthread.php?t=1160552&highlight=xubuntu+blank+screen+mouse](http://ubuntuforums.org/showthread.php?t=1160552&highlight=xubuntu+blank+screen+mouse)
(When the cursor appears press alt+f2 and run xfce4-panel to recover the panel and xfdesktop to recover the desktop. If xfdesktop doesnt work, go to the menu, settings, desktop settings and activate "allow xfce to manage the desktop". Then go to "Settings -> Sessions and Startup" and choose "automatically save sessions on logout")

---

