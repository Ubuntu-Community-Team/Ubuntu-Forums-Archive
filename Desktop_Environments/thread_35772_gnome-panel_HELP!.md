---
title: "gnome-panel HELP!"
date: 2005-05-20
forum: Desktop Environments
---

### Post by Boomgawd on 2005-05-20
Hi,

I've really messed my gnome-panel up!. I added a CPU monitor and a MEM monitor to the panel and that worked ok. Then I added a disk monitor to it and the panel froze. I CTRL-ALT-BACKSPACE thinking its gonna restart and for get I asked for the disk monitor but apprently not cuz not the panel wont even load! How do I modify its config config file to stop loading the disk monitor.. I've tried the killall gnome-panel as well and that doesnt help.. 

I'm really stuck, anything will help..

thanks,

Boomgawd.

---

### Post by Xian on 2005-05-20
[QUOTE=Boomgawd] How do I modify its config config file to stop loading the disk monitor.. I've tried the killall gnome-panel as well and that doesnt help..[/QUOTE]
I really don't know, but you could rename the hidden gnome folders (.gnome, .gconfd, etc) in /home/<your_name> and then log back in to a default desktop. Then just configure again but this time without that panel applet.

---

