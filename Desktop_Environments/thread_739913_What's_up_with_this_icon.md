---
title: "What's up with this icon?"
date: 2008-03-30
forum: Desktop Environments
---

### Post by Rhapsody on 2008-03-30
I've been using a [Gnome Green Icon Pack](http://www.kde-look.org/content/show.php/Gnome+Green+Icon+Pack+for+KDE?content=66989) (which is quite good BTW) on my KDE desktop for a while now, but got bored of it and went back to Crystal SVG, which Kubuntu seems to use by default. But this brought me back to a strange problem that I had before switching icon sets.

The attachment to this post shows my top KDE panel, with K Menu, Lock/Logout Buttons, System Menu, and Quick Launcher. The problem, as may be obvious, is with the Quick Launcher. While most icons are big and chunky, the KTorrent icon is a tiny thing crammed in the top left of its area! The icon itself actually works fine (clicking anywhere between OpenOffice.org Word Processor and Konqueror will launch KTorrent, as it should work), so the flaw is purely cosmetic.

The Quick Launcher has 'Allow Drag and Drop' on, 'Icon size' set at 24, 'Conserve space' off, and 'Add/remove applications based on their popularity off'. Setting 'Conserve space' on, enlarging the 'Icon size' above 32, or setting 'Icon size' to automatic solves the problem, but at the expense of making all of the icons much smaller, which isn't what I want. The panel is set to a custom size of 50 pixels (long story) but changing it seems to make no difference.

---

### Post by kerry_s on 2008-03-30
have you tried changing just that icon? (right click the icon> properties> click the icon pic)

---

### Post by Rhapsody on 2008-03-30
I can't change the icon directly (Quick Launcher doesn't give me that option) but I did remove KTorrent, change the icon for KTorrent (to the one for KVIrc), then re-added KTorrent to the Quick Launcher, and that icon worked fine. But then I removed KTorrent again, changed the icon back, and put KTorrent back in the Quick Launcher. The problem promptly reappeared. It just doesn't like that icon for some reason.

---

### Post by kerry_s on 2008-03-30
it's most likely that icon has a set size.

here's a 128x128

---

### Post by Rhapsody on 2008-03-30
I've no idea why, but that seems to fix it. Something must be wrong with the system icon. Is there any way to replace the system's KTorrent icon rather than using that PNG from /home?

---

### Post by kerry_s on 2008-03-30
yeah just swap it with the stock ktorrent icon. use synaptic to find out where the icon was put, in synaptic right click on ktorrent> properties> installed files.

i'm not going to tell you to use whereis or locate, because you might get a very long list. better to just see where the installer put the icon. if it's a different format, such as .xpm just link it to the ktorrent.png.

---

