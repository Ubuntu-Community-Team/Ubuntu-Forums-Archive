---
title: "GNOME Panel trouble"
date: 2005-12-13
forum: Desktop Environments
---

### Post by rado_london on 2005-12-13
Hi 
I just installed KDE 3.5 on my laptop. When I saw all gnomesh stuff in their menu bar i just removed. but when i went back to gnome all removed entries wheren't there as well. then i tried to reinstall the panel but this crashed my trash icon, the wether broadcast, CPU usage etc. For example my System>Administartion menu has only Device Manager, Printing and Synaptic Package Manager.

My question is: How can I get my panel with all default menus and applets.

Thanks in advance

/offtopic
BTW KDE 3.5 is more eyecandy than gnome but it's rubbish. It's also slower than gnome and just doesn't do the job:p :p :p :p :p 
/offtopic

---

### Post by teaker1s on 2005-12-13
depending what you have done run 'smeg' it's the panel editor

---

### Post by dickohead on 2005-12-13
While a lot of people are saying that KDE is the way to go, i'm one of the opposite view, I've been with KDE for YEARS, and only since Ubuntu 5.04 have I been using Gnome - it makes more sense, everything is consistent, and it's response time is fantastic!

As for what you did to your menu, HAHAHAHAHAHAHA.... ahhh that's gotta suck!

Have you tried: sudo dpkg-reconfigure ubuntu-desktop
or: sudo dpkg-reconfigure gnome-panel
?

---

### Post by rado_london on 2005-12-13
sudo dpkg-reconfigure ubuntu-desktop solved the problem with the broken applets. I also enabled all programs via smeg. But still Administation has only a few entries.

Any ideas?

---

### Post by dickohead on 2005-12-13
ummmmmmm..... i'm not to  sure on that one! But if you do a search through synaptic for something like: gnome menus, ubuntu menus, ubuntu base, ubuntu blah blah. I;m sure you'll find the package you're after. Note the name of it and do an:
sudo dpkg-reconfigure package-name

Good luck!

---

### Post by rado_london on 2005-12-23
Well I still remember the little Windows tips (restart,reinstall etc). Well, I finally reinstalled Ubuntu and now eerything works well.

---

