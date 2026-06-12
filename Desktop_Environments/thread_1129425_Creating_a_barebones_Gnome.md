---
title: "Creating a barebones Gnome"
date: 2009-04-18
forum: Desktop Environments
---

### Post by AndyP79 on 2009-04-18
Hi All,
 i was wondering if anyone might have an idea how to build a barebones Gnome? I want to not have to uninstall the programs I don't want, just start with the programs I want. I don't care for evolution, or vlc, or whatever else, and half the programs I don't even need. I would like to be able to start with just synap, and put only what I need. I would think this would be something people might like what with how everyone likes to customize their computers, why not have full control over packaging of programs also, without using space for things you don't want or need?

Any ideas?

---

### Post by perrti-y02 on 2009-04-18
As a possibility, but not something I would recommend if you aren't feeling up for a bit of fun, is installing a server version (or stop the normal installation at "select and install software") and then installing (using sudo apt-get install) gdm and gnome-session which will give you GNOME and almost nothing else. I had to do this with my installation but I enjoyed it.

---

### Post by benerivo on 2009-04-18
I'd download the 'alternate cd' version of ubuntu, which provides an option for a command line installation. After installation, it boots up to just a console screen. As perrti-y02 mentioned, you can then add the basic stuff as a starting point. I'd probably do ```
sudo apt-get install xorg gdm gnome-core synaptic
```
then either reboot, or i think you can then just do ```
sudo /etc/init.d/gdm start
```

---

### Post by perrti-y02 on 2009-04-18
Beware if you do do this, it gives you NOTHING. If you want to print something you need to install packages, if you want to connect to a wireless network you may well need to install packages.

However, there are few things more satisfying than a system that you have troubleshooted from the very installation.

---

### Post by AndyP79 on 2009-04-18
Hi All,
 Thanks for the advice. While it does sound like I would have that satisfaction, I think I am going to wait till I get the new computer in a month or two, then I can use this old one as my test computer. I have found that I want to do more and more as I go along, and I have the feeling that one day I might just end up creating a frankenstein! 
Thanks again, and I will try these when I can

---

