---
title: "[SOLVED] Deborphan"
date: 2008-12-18
forum: General Help
---

### Post by LE CHARBON on 2008-12-18
Is it a good idea to use deborphan to remove isolated libraries? Do I need these libraries for 8.10 to function properly?:confused: Would this actually help UBUNTU to speed up a little.

---

### Post by donkyhotay on 2008-12-18
I use GTKorphan (GUI version of deborphan) to clean out my libraries automatically about once a week or so. I've been doing this for over a year and in that time only twice have I ever had an issue where it removed something that broke a program. Of course once I was aware of it I just reinstalled the program through synaptic which put back the libraries and fixed it. I don't *think* it gives any extra speed to my system but it does keep my system from being cluttered up with unused files and helps with HD space.

---

### Post by albinootje on 2008-12-18
> **LE CHARBON said:**
> Is it a good idea to use deborphan to remove isolated libraries? Do I need these libraries for 8.10 to function properly?


I'm happy with the occasional "sudo apt-get autoremove" removals.

> 
:confused: Would this actually help UBUNTU to speed up a little.
Probably not.
If you want to speed up your desktop try customizing the default theme, and check the gnome-session for items that you don't need, as a start.
Also Nautilus is not really the fastest file-manager you can get, for example Thunar is faster with loading large folders.

But maybe you can tell us what is slow in your Ubuntu installation.

---

### Post by exploder on 2008-12-18
A useful command for keeping things cleaned up.

sudo apt-get clean

Just thought you might be interested in that, in case you or anyone else was not familiar with that command. I am particular myself about keeping things cleaned up on my system.

---

