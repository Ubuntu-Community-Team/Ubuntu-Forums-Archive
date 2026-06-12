---
title: "Gnome vs XFCE memory usage"
date: 2008-07-08
forum: Desktop Environments
---

### Post by weese on 2008-07-08
All the research I have done says that XFCE has a smaller memory footprint than Gnome. However, I have 2 systems with both environments loaded and both systems show Gnome using less memory than XFCE. For example, on the tower system with 1 gig of memory I fired up Firefox, OpenOffice, and Gimp. Under Gnome, top reports 616 megs of memory being used, while it says that I am using 667 megs when running XFCE. Gnome is 2.22.2 and XFCE is 4.4.2. Am I missing something here? Have there been some major changes to Gnome recently that now lets it use less memory than XFCE?

---

### Post by pytheas22 on 2008-07-08
I think you need to look at how much memory is being used by processes specifically related to Gnome.  It's not accurate to look at total system memory usage in general, because there are a lot of other variables--there could be stuff going on in the background unrelated to the desktop environment that's causing the system to be using more memory when you're logged in to Gnome.  There's no conceivable way that modern Gnome could be using more memory than xfce, unless there's a major problem with the latter.

---

### Post by zackf on 2008-07-08
I find Gnome and XFCE work about the same on my Dell Laptop from like the 90's with 256MB of RAM. I don't know if there's a process that hangs up in XFCE or what but from my experience there's not a huge appreciable difference.

---

### Post by weese on 2008-07-08
I don't think that looking at just the DE specific processes is a real world comparison. When you look at a DE, you have to take into account all the cruft that comes with it. I did my install with a standard 8.04 install disk. Then I used Synaptics to get the xubuntu-desktop package. Is there a ton of unnecessary crap that comes with the desktop package? When I do a "ps" and look at the process count, Gnome with the apps has 115 processes running and XFCE has 123. Is Xubuntu a bad distro to use for comparative purposes?

---

### Post by Inxsible on 2008-07-08
download the ps_mem.py and run tha as root to know what processes are using memory. Google it, it will most likely be the first link.

its a python script.

---

