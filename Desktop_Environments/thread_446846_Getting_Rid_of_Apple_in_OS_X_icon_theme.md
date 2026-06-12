---
title: "Getting Rid of Apple in OS X icon theme"
date: 2007-05-17
forum: Desktop Environments
---

### Post by grogger13 on 2007-05-17
[IMG]http://i177.photobucket.com/albums/w214/grogger13/Screenshot-2-1.png[/IMG]

I just got this theme and i like all the icons but i hate that the ubuntu logo got replaced with that stupid apple.  I dont own an apple and i never want to.  I still have the .tar and i couldn't fing the apple image in there,  the icon theme is called OSX_MOD from the Real Minimal widgets style 2 beryl theme.

---

### Post by testube_babies on 2007-05-17
The icon you need to remove is probably called distributor-logo.  So, to find it:
```
sudo updatedb
locate distributor-logo
```

Take note of the distributor logo file or files that are in the OSX_MOD folder and then you can delete or rename them as you wish.

---

