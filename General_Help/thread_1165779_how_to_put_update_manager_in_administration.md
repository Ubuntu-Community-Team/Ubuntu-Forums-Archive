---
title: "how to put update manager in administration"
date: 2009-05-21
forum: General Help
---

### Post by agel1 on 2009-05-21
i installed ubuntu using this guide ([http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)) and now (update manager) isn't in the administration menu, can somebody tell me how to put it there.

thanks

---

### Post by jrox717 on 2009-05-21
Rightclick anywhere on top of the menu that's on the panel and click "Edit Menus". A popup box should open.
On the left go to System > Administration
Then on the right, check the box next to Update Manager

I don't know anything about the minimum install, but I assume this should work.

---

### Post by agel1 on 2009-05-22
> **jrox717 said:**
> Rightclick anywhere on top of the menu that's on the panel and click "Edit Menus". A popup box should open.
On the left go to System > Administration
Then on the right, check the box next to Update Manager

I don't know anything about the minimum install, but I assume this should work.isn't there, thanks

---

### Post by michy99 on 2009-05-22
My guess would be that it wasn't installed. If you want it enter this in a terminal:```
sudo apt-get install update-manager
```

---

### Post by agel1 on 2009-05-22
> **michy99 said:**
> My guess would be that it wasn't installed. If you want it enter this in a terminal:```
sudo apt-get install update-manager
```thanks, now is in the menu

---

