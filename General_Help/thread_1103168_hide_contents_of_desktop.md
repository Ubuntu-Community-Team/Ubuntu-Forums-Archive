---
title: "hide contents of desktop?"
date: 2009-03-22
forum: General Help
---

### Post by abhilashm86 on 2009-03-22
i've got a lot of icons on my ubuntu desktop, i really want to hide it, because icons just spreads all over the place.
How to hide it, sometimes ubuntu at start up does this, i liked it, but then i don't know to hide icons:)

---

### Post by taurus on 2009-03-22
Open a terminal and run

```
gconf-editor
```
apps -> nautilus -> desktop and remove the check mark for volumes_visible.

---

### Post by shailendra on 2009-03-22
Hi,

Please follow the below link;

[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

---

### Post by Kareeser on 2009-03-22
I'm confused... how do you both know he's referring to drive volumes?

---

### Post by prshah on 2009-03-22
> **abhilashm86 said:**
> but then i don't know to hide icons:)

Use System-Preferences-CompizConfig Settings Manager-Wallpaper.

Enabling this and specifying custom wallpapers will disable the showing of icons on the desktop.

---

