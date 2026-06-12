---
title: "Freeciv panel"
date: 2010-08-16
forum: Gaming &amp; Leisure
---

### Post by 1/0 on 2010-08-16
I've played freeciv for a long time but something happened a month ago. The panel (view and messages) that is usually at the bottom of the window switched to the right side of the window. It's demanding much more space and is irritating when you're not used to it. 

Anyone know how to move it back? I've tried to find an option in the preferences and I've also tried to drag and drop it but no success. Help would be much appreciated.

---

### Post by 1/0 on 2010-09-18
After uninstalling (and purging) a few times and erasing the .freeciv* files in home I almost gave up. But then I purged all and started to look at what was left and I believe it might have been the file */etc/alternatives/freeciv* that caused it. I erased that one and a few others, such as */usr/share/app-install/desktop/freeciv-gtk.desktop*. Then I got the message panel as full screen.

Hence, I changed the full screen setting under the interface settings. No change. Then I realized you might have to restart the game. I did and got the panel on the left. By changing the small display arrangement setting and restarting the problem went away. So if you get this problem, change that setting and RESTART.

---

