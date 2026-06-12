---
title: "Help:deleted default menu by mistake"
date: 2010-06-08
forum: Desktop Environments
---

### Post by stefcep on 2010-06-08
Hi,

I accidently deleted the default top menu bar (I wanted to delete an applet, but instead deleted the entire menu bar.  D'oh!!)  How can i get it back?

Ubuntu 9.04

---

### Post by bigsmitty64 on 2010-06-09
Not sure about 9.04, but in 9.10 and forward, you right click the panel, choose "add to panel" then choose "main menu" from the list.

---

### Post by stefcep on 2010-06-10
Thanks.  That worked.  Now i need to get the little internet connection applet back, the one that looked like the 4 bars in the corner, think its called networkmanager applet?

---

### Post by stefcep on 2010-06-10
OK to get the network connection applet back I did some searching and found:

I had to go into /etc/NetworkManager/ and then right click on "nm-system-settings.conf"->properties->open with->text editor.

I then sudo gedit /etc/NetworkManager/nm-system-settings.conf and then changed "managed=false" to "managed=true" and then save it.  Reboot.  To get the applet to appear on the top panel, I had to put mouse pointer over top panel, right click->add to panel->Notification Area.

---

