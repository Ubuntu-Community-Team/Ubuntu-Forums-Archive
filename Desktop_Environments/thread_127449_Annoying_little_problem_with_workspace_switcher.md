---
title: "Annoying little problem with workspace switcher"
date: 2006-02-08
forum: Desktop Environments
---

### Post by Piggah on 2006-02-08
This is sort of petty, but it's really annoying me. 

Anytime I try to add a workspace switcher to a panel and have it show more than one workspace, I get an error that says "An error occured while loading or saving configuration information for wnck-applet. Some of your configuration settings may not work properly."

I've poked around a bit, and I managed to get it to display more than one space, but I can't have it display them in more than one row. I'm being forced to use a desklet in place of it, and it's starting to get annoying. :p

---

### Post by mikeyrb on 2006-02-26
I fixed this issue on my system by reinstalling packages libwnck18 and libwnck-common.  Don't really know which one fixed it as I did both at the same time, but oh well.

---

### Post by Wilb on 2006-03-03
Argh! I had this same problem last night so removed both packages as suggested using:

sudo apt-get remove libwnck18 libwnck-common
sudo apt-get install libwnck18 libwnck-common

After a reboot, every time I log into GNOME I have no panels at all. Combine this with the fact that I've got Nautilus set to not draw a desktop, this means I login to a screen with which I can do absolutely nothing! Luckily theres the failsafe shell login - anyone any suggestions of how I can restore my panels? (The default ones would do...)

---

