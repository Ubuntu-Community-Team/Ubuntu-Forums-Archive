---
title: "Kiba dock"
date: 2006-08-04
forum: Desktop Environments
---

### Post by distroman on 2006-08-04
I installed the kiba dock with compiz. 
> When a launcher not works, there is an error in the .desktop file!
modify the desktop file and all should be fine, make sure u have the icon in /usr/share/pixmaps, and look to the Exec line
I think I got this problem, but I am to much of a newbie to fix it with the instructions above, if that's even the problem.

The thing is that some apps wont stay on the dock after reboot, they just disappear. 
Any chance someone can help me?

---

### Post by distroman on 2006-08-05
Simply didn't get that I had to sudo gedit /usr/share/applications/XMMS.desktop
XMMS.desktop
vlc.desktop
kate.desktop
and so on..
and add "Comment="Put whatever comment u want here"

---

