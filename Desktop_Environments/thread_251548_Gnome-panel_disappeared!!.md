---
title: "Gnome-panel disappeared!!"
date: 2006-09-05
forum: Desktop Environments
---

### Post by blueidealist on 2006-09-05
Hello - I don't know what happened, but my gnome-panel has disappeared on reboot.  I now have a very pure minimalist desktop (nothing on it) and working with keyboard shortcuts...

Possible reasons why this happened (pure guesses):
- I uninstalled evolution.  Did I uninstall necessary library packages by mistake?
- Google Earth crashed on me several times in the last session

In any case, no reboot will solve the problem.

~$ killall gnome-panel
gnome-panel: no process killed
~$ gnome-panel
bash: gnome-panel: command not found

What can I do?

Thank you for any help,

David

---

### Post by bigken on 2006-09-05
you could try booting in safe mode and type sudo apt-get install ubuntu-desktop ;)

---

### Post by blueidealist on 2006-09-05
Great help, and problem solved!
Many thanks,

David

---

### Post by David Oxland on 2006-09-05
Wonderful bigken;  :-D 

I've been searching around to fix this  problem for over a week ever since the xserver crashed me.  I managed to get the signin page back but couldn't find the commonsense to describe it to anyone as "Gnome desktop missing."

The resolutions are a bit coarse and now I'm gunshy about doing an update or using Automatix to get my nvidia driver back.

Any comments or advice or just dive in for updates?
Thanks again
David

---

### Post by bigken on 2006-09-06
> **David Oxland said:**
> Wonderful bigken;  :-D 

I've been searching around to fix this  problem for over a week ever since the xserver crashed me.  I managed to get the signin page back but couldn't find the commonsense to describe it to anyone as "Gnome desktop missing."

The resolutions are a bit coarse and now I'm gunshy about doing an update or using Automatix to get my nvidia driver back.

Any comments or advice or just dive in for updates?
Thanks again
David

just dive in and do the updates you could also run **sudo dpkg-reconfigure xserver-xorg** and select your video driver ;)

---

### Post by bigken on 2006-09-06
:confused:

---

