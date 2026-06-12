---
title: "How to add launcher in Gnome Shell"
date: 2012-02-07
forum: Desktop Environments
---

### Post by olwe on 2012-02-07
I've got 11.10 Gnome Shell. I need to add a launcher for a 3rd-party app and I'd like it to be in "Programming"

I found this info:

```
sudo apt-get install --no-install-recommends gnome-panel
```

then

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```

I didn't try the first, but the second worked. But I don't want it on the desktop, I want it in "Programming." Any ideas?

BTW, where would a good Gnome Shell Guide be?

---

### Post by Frogs Hair on 2012-02-07
Try adding the launcher via the main menu .

---

### Post by wojox on 2012-02-07
> **Frogs Hair said:**
> Try adding the launcher via the main menu .

+1 search for alacatre. :P

---

### Post by olwe on 2012-02-07
> Try adding the launcher via the main menu .

I'm in Gnome Shell, BTW, i.e., no "Main Menu"

---

### Post by olwe on 2012-02-08
All right, I solved it myself. I logged out. Logged back in with Gnome Classic. Added my non-standard app. Logged back into Gnome Shell. Hey, I like GS, but I wish it was better documented.

---

