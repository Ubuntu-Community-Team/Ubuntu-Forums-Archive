---
title: "Gnome event sounds not working on Feisty"
date: 2007-04-27
forum: Desktop Environments
---

### Post by raman15217 on 2007-04-27
Hi.. I upgraded to Feisty Fawn and noticed that the Gnome login/logout sounds were missing. The other users on the system don't have this problem. I figured out that ESD wasn't starting up at all when I log in even though I select ESD under sound preferences. How can I fix it?

The other problem I noticed was that the whole system took for ever to show the Gnome desktop after login (for all users on the system). I even created a new user to see if that made a difference.

Thanks!
Raman

---

### Post by rickycodie on 2007-04-28
i don't know about the slow system, but try to use the sounds manager in the admin tab, and see if changing the sound helps.

---

### Post by LDRoamer on 2007-04-29
Sound is broken on my old laptop and there is definitely a hardware conflict causing slow loading of the desktop.  If I comment out my sound card driver the desktop loads normally.  Check dmesg and see if you can spot any errors (I had a whole bunch of DSP errors and an error unable to grap port 0x220 - that is one of the ports my sound card uses). I am thinking your problem might be similar but possibly your hardware conflict, if there is one, is with some other piece of hardware.

---

