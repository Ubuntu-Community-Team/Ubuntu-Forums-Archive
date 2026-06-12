---
title: "Problem with Virtual Desktop in Ubuntu 9.04"
date: 2009-08-16
forum: Desktop Environments
---

### Post by stefansz on 2009-08-16
I was trying to enable extended desktop onto second monitor/TV in "standard" Gnome-ubuntu 9.04 on my Toshiba A100 laptop (Intel 945 chipset) when I got a prompt to enable Virtual Desktop in order for it to work. Saying "yes" to that prompt and then re-logging in causes my desktop to go blank, while nothing is getting displayed on my TV. (Windows XP works just fine in that respect!). I have to manually remove the
               Virtual 2080 800
line that's been added to section "Screen" subsection "Display" of my /etc/X11/xorg.conf in order for my desktop to start working again.
I'd like to mention that the resolution of my laptop's display is 1280x800, while that for my TV is 800x600, hence the 2080x800 virtual resolution.

I'd like to know if this is caused by a known problem and if a fix has been identified.
Thankssss!

---

