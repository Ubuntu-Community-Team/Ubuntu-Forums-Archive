---
title: "Display difficulties......."
date: 2007-06-09
forum: Desktop Effects &amp; Customization
---

### Post by jaw175 on 2007-06-09
Hi All,  This is my first post. I'm using Feisty 7.4 on Compaq Athlon AMD 64, 512mb mem. 80GB HD. Somewhere I've gone wrong with the screen resolution display. No problem in accessing the menu item for setting this; however, I'm restricted to only having a size of x800 or that of x600, both of which are restrictive of providing a large enough display space. Is there a way I can get around this to utilise at least 1024 or poss higher setting?  I'm still getting to - slowly - know the OS and would be most grateful for any help to sort this out. Thanks in anticipation.  :)

---

### Post by muximus on 2007-06-12
open /etc/X11/xorg.conf as root or do 
gksudo gedit /etc/X11/xorg.conf

in the file you should see a line which lists all the resolutions.. add the resolutions you want manually and restart X (or reboot). it should give you the new resolutions now

---

