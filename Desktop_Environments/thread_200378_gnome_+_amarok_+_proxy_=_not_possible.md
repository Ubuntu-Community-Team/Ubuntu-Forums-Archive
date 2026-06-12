---
title: "gnome + amarok + proxy = not possible?"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-06-20
How can I set amarok up to use the proxy set in gnome so I can use internet portions of the program?  Would I need to install KControl or some such utility?  I don't particularly want to download a load of KDE stuff if I don't need to - but I would like to get amarok working as it was intended!

---

### Post by Lunar_Lamp on 2006-06-23
I worked out a solution:

You need to install kcontrol which manages system settings in KDE. (I presume sudo apt-get install kconrol works here, but I already had it installed after installing a load of junk a while back, though not including KDE).

Then you can run "kcontrol" from a terminal, and change proxy settings in the network portion.  Simple, and it works :)

---

### Post by sorin7486 on 2006-07-08
10x.. I had the same problem

---

### Post by kkellner on 2006-09-10
thank you - that worked perfectly!

---

