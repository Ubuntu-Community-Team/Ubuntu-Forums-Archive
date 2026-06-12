---
title: "revert to default resolution????"
date: 2009-03-16
forum: General Help
---

### Post by jellylogix on 2009-03-16
OK, so my nvidia drivers were being messy so I tried to update them. Sure enough, just my luck, this made it worse and I had to go into  "low graphics mode" on Ubuntu. This mode is in a really high resolution, so I tried lowering it down to a smaller resolution but instead of making it better, my entire screen is now chopped into small sections and mixed up a lot making it unreadable. 

I need a way to revert the screen resolution back to normal (either through keyboard shortcuts, or the command prompt (by pressing CTRL + ALT + 1 OR 2 OR 3 etc.. ) (what is that called?)

Anyways, can u help?

---

### Post by anlag on 2009-03-16
Try

sudo dpkg-reconfigure xserver-xorg

to reconfigure your X server which should also (re)set resolution settings.

---

