---
title: "Deskbar-applet"
date: 2010-05-01
forum: Desktop Environments
---

### Post by svenskmand on 2010-05-01
How do I get the [deskbar-applet]("http://projects.gnome.org/deskbar-applet/") in one of my gnome panels? It used to be possible to add it to a panel in 9.10, but now it is not to be found in the menu where I can select which item to add to a panel :S

---

### Post by nerohc on 2010-05-01
Same here. How can I do to make the deskbar applet to show on the "add to panel" menu?
Thanks

---

### Post by wojox on 2010-05-01
Go here, scroll down to the bottom and select which version 32 or 64. Then download the .deb file and install with GDebi

---

### Post by svenskmand on 2010-05-01
> **wojox said:**
> Go here, scroll down to the bottom and select which version 32 or 64. Then download the .deb file and install with GDebi

Go where? There is no link :S

By the way why is deskbar-applet removed from Gnome/Ubuntu or whatever it is normally part of?

---

### Post by wojox on 2010-05-01
Sorry about that [http://packages.ubuntu.com/karmic/deskbar-applet](http://packages.ubuntu.com/karmic/deskbar-applet)

---

### Post by nerohc on 2010-05-02
I've already installed it through apt-get. When I downloaded the .deb and opened it with GDebi, it showed a warning saying there's a later version installed, and it disables the "install package" button.

What I did to fix this is to download the package from here: 
[http://packages.ubuntu.com/lucid/deskbar-applet](http://packages.ubuntu.com/lucid/deskbar-applet)

And then reinstall it, overriding the previous apt-get install. Now it shows on the "Add to panel" menu.
Hope it helps somebody

---

### Post by svenskmand on 2010-05-04
I just saw that you can install it from apt-get it is called deskbar-applet, so you just type
```

sudo apt-get update
sudo apt-get install deskbar-applet

```
Then you should be able to add it in you Gnome panels :)

---

