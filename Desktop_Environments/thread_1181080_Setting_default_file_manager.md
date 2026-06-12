---
title: "Setting default file manager"
date: 2009-06-07
forum: Desktop Environments
---

### Post by Nevon on 2009-06-07
Back when I first installed Ubuntu 9.04, Nautilus would crash on me pretty much constantly - causing me to have no real desktop. In an attempt to at least be able to browse my files normally, I removed Nautilus and installed Thunar instead. After that, I tried to reinstall Nautilus (because I really love nautilus). Too my surprise, it seemed to work just fine. I even got my desktop back. But for some reason Thunar is still set as my default file manager. So whenever I use the Places menu, Thunar pops up. However, if I plug in a USB memory - Nautilus takes care of it.

I've already tried removing Thunar, but then the Places menu just gives me an error when I try to open something. 

Is there any way I can set Nautilus to be the default file manager?

---

### Post by benerivo on 2009-06-07
You could check out the bottom of [this page]("http://www.psychocats.net/ubuntu/nonautilusplease"), as well as removing thunar.

---

### Post by Nevon on 2009-06-07
> **benerivo said:**
> You could check out the bottom of [this page]("http://www.psychocats.net/ubuntu/nonautilusplease"), as well as removing thunar.

Already tried both of those things. The script provided there actually only restores Nautilus if you used one of the scripts provided there to remove Nautilus in the first place.

---

### Post by benerivo on 2009-06-07
It may be a configuration file that causes the problem. I would try creating a new user to see if they have the problem as well. If not, then the problem might be solved by deleting something from your home folder. Don't know what, but hope it helps...

---

### Post by Orfintain on 2009-06-07
I have a similar issue rhythum box has hyjacked some nautalis functions and now none of my bookmarks work or any places for that matter other than computer I have removed ryhum box. the above script does nothing and a guest user dose not have this problem...

---

### Post by Nevon on 2009-06-12
> **benerivo said:**
> It may be a configuration file that causes the problem. I would try creating a new user to see if they have the problem as well. If not, then the problem might be solved by deleting something from your home folder. Don't know what, but hope it helps...

I tried making a new user, and it worked just fine. But I don't want to lose all my settings and stuff from my old user, so I need to find out what folder it is that's mucking everything up. I tried removing .gnome2, .gnome, .gconf and .nautilus without any luck. Any ideas on what folder to remove?

---

