---
title: "Desktop Effects work for awhile, then problems"
date: 2007-05-06
forum: Desktop Effects &amp; Customization
---

### Post by timzak on 2007-05-06
The first couple of days after my Ubuntu install the desktop effects worked fine (both wobble and cube).  Then one day I noticed I only had 1 workspace instead of 4.  So I right-clicked to preferences, set it back to 4, and they came back.  But when I clicked on any of the workspaces, instead of the cube spinning to them, ALL of my panels (upper and lower) disappeared.  This is repeatable.  I manually reboot via ALT-F2, then CTRL-ALT-DEL because all my icons in the panels are gone (so I can't access the shutdown icon), and it happens again.  Any ideas?  What confuses me is why they worked for the first couple of days, then suddenly broke.  I did not install anything out of the ordinary, and what I did install was either through Add/Remove, or Synaptic.

I'm using an nVidia Geforce 6800GS AGP (fairly new) on a new motherboard with a Core2Duo processor.  I"m using default nvidia drives that are installed automatically when enabling restricted mode drivers.  No modifications to video drivers, etc.

---

### Post by GrueTamer on 2007-05-06
I think the restricted drivers don't work with the desktop effects.  At least, that's the case with my restricted ATI drivers.  While they perform well for gaming and stuff, they don't do 3D at all.  Perhaps it's the restricted drivers that are causing your problem.

---

### Post by schnupi on 2007-05-06
see here -> [http://ubuntuforums.org/showthread.php?t=434533](http://ubuntuforums.org/showthread.php?t=434533)

---

### Post by kpolice on 2007-05-06
When you have Compiz you have to use 1 workspace and set the hsize to 4, this way you will have one big workspace divided into the 4 faces of the cube.

---

### Post by timzak on 2007-05-06
Thanks, it seems to be working so far.  BUT, the top bar on all windows is missing now.  The bar that has the min and max boxes in the upper right corner.  Weird.  This is both in the OS (ie, Synaptic) and in Firefox.  It's like someone just sliced off the top bar.  The top bar in Firefox now is the bar with File, Edit, View, History, Bookmarks, etc.

I think I will try the new nvidia drivers through Synaptic.  When changing drivers, must I uninstall the old one first, or can I just install on top while still using the old driver?

---

### Post by z0phi3l on 2007-05-06
The window borders disappearing happens to me from time to time, what I do is reinstall Beryl and the problem goes way.

---

### Post by timzak on 2007-05-07
> **z0phi3l said:**
> The window borders disappearing happens to me from time to time, what I do is reinstall Beryl and the problem goes way.

I'm talking about Desktop Effects (built into Ubuntu Feisty), not Beryl.  If I enable Desktop Effects, the window border disappears; if I disable it, it comes back.  I'm not using Beryl (yet).

I haven't gotten a chance to try a different nvidia driver, but I'm wondering if that might help me.  I'm using an AGP version of the 6800GS (came out much later than the PCI-X version, so it might require a newer driver than Restricted Mode provides).

---

### Post by blankz on 2007-11-26
> **timzak said:**
> I'm talking about Desktop Effects (built into Ubuntu Feisty), not Beryl.  If I enable Desktop Effects, the window border disappears; if I disable it, it comes back.  I'm not using Beryl (yet).

I haven't gotten a chance to try a different nvidia driver, but I'm wondering if that might help me.  I'm using an AGP version of the 6800GS (came out much later than the PCI-X version, so it might require a newer driver than Restricted Mode provides).

I have the exact same problem! any sollutions yet?? pretty annoying that when you enable effects the titlebars goes away... :confused:

---

### Post by Forlong on 2007-11-26
What type of graphics card are you using?

---

