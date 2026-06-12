---
title: "how to replace mark all upgrades icon in Feisty"
date: 2007-06-03
forum: Desktop Effects &amp; Customization
---

### Post by adohall on 2007-06-03
Does anyone know where Synaptic is pulling its 'Mark all Upgrades' icon from. I've replaced both instances that I could find in icons/hicolor/. But the icon remains the same. Is there another instance of he old one somewhere? Or an arcane process I'm not aware of?

---

### Post by Pragmatist on 2007-06-04
The way you can find it is with this command:
```
locate synaptic |grep png
```

If you've never used locate, you need to update its database first (this takes a couple of minutes to complete):
```
sudo updatedb
```

After doing this myself, I discovered that there isn't a single image for the "mark all upgrades".  It is part of a larger image for the whole toolbar.  There are a few copies of this image, but one is located at:
**/usr/share/synaptic/html/figures/synaptic-toolbar.png**

I have attached the png file.

---

