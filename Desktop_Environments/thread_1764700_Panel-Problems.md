---
title: "Panel-Problems"
date: 2011-05-22
forum: Desktop Environments
---

### Post by MartinMAP on 2011-05-22
I have no idea what happend, but my "Panel-Tools" in the top right (with the watch, the Chat and Mail shortcut and te shutdow-button etc.) is one! The right side of the top-panel is empty. How i get it back? And there is also a problem with the panel on the bottom. I gues my Desktop Environment is crashed! How to reinstall?

Thanks!
Martin

---

### Post by thohms on 2011-05-22
What system do you use?

---

### Post by MartinMAP on 2011-05-22
Sorry, 11.04 using classic ubuntu

---

### Post by thohms on 2011-05-22
Delete your folder ~/.gconf/apps/panel and re-login. That should do it.

Regards,
Thomas

---

### Post by MartinMAP on 2011-05-22
Sorry, I dont have that folder...

---

### Post by manicol on 2011-05-22
it's a hidden folder, just press ctrl-h on your home folder and you will find it.

---

### Post by thohms on 2011-05-22
Or use the terminal:
> 
rm -R ~/.gconf/apps/panel


---

### Post by Copper Bezel on 2011-05-22
Or you can manually add those items back to the panel - they're the Clock, Notification Area, Indicator Applet, and Session Indicator Applet.

---

