---
title: "compiz fusion on debian without internet connection?"
date: 2008-02-06
forum: Desktop Effects &amp; Customization
---

### Post by zzzPOOHzzz on 2008-02-06
ok for one of my classes we had to set up a dualboot xp/debian-etch pc... i have it all set up, but i want to install compiz-fusion on the debian-etch install, but we don't have internet connections available.  so i was wondering if there was a .deb out that would work to install all of what i needed for it to run properly so i can download it to a flash drive and install it.

i've googled and haven't come up with anything that i know will work for sure.

and i figure since ubuntu is based off of debian, someone could probably help me out here.

---

### Post by Kateikyoushi on 2008-02-06
Never used them as I consider it to be a useless waste of resources but a lenny with gnome-desktop installed would pull in the following packages for compiz.

> compiz compiz-core{a} compiz-gnome{a} compiz-gtk{a} compiz-plugins{a} libdecoration0{a} mesa-utils{a} 

I found the following  packages related to fusion.

>  sudo aptitude search fusion
p compiz-fusion-bcop - Compiz Fusion option code generator                              
p compiz-fusion-plugins-extra - Compiz Fusion plugins - extra collection
p compiz-fusion-plugins-main - Compiz Fusion plugins - main collection
p compiz-fusion-plugins-unsupported - Compiz Fusion plugins - "unsupported" collection 

Of course you could try to install it and see what packages it needs on that installation.

P.S.: Long live the deb.

---

