---
title: "menu bar applet problem"
date: 2009-06-24
forum: General Help
---

### Post by biasquez on 2009-06-24
hi, recently i have menu bar changed  (system -> personal,look and feel,etc...) and i don't have nvidia settings like icon, i tried to add nvidia-settings again but i have error "folder exists".
i attached screenshot with new menu bar.can i restore old menu bar? if yes, how?

---

### Post by zvacet on 2009-06-24
> can i restore old menu bar?

Yes.Turn off gdm with command

```
sudo /etc/init.d/gdm stop
```

after that

```
rm -rf .gconf* .gnome* .nautilus*
```

```
sudo reboot
```

---

### Post by ajgreeny on 2009-06-24
It would be simpler to just rename ~/.gconf/apps/panel as a backup, and that will mean all your other desktop configuration will remain as it was, surely.  If you know which one it is, you could even navigate down to the .gconf/apps/panel/objects/object_# and just rename that.  You can see which object it is by opening the xml file for each and looking for the name in the text.

---

### Post by biasquez on 2009-06-24
i removed .gconf/apps/panel dir and rebooted but nothing changed..

---

### Post by ajgreeny on 2009-06-24
I am surprised about that, so now try zvacet's suggestion and see if that helps, though I have to tell you that it is not easy to see what your problem is, the screenshot is far too small to see any detail of what you mean.

---

### Post by biasquez on 2009-06-25
> **ajgreeny said:**
> I am surprised about that, so now try zvacet's suggestion and see if that helps, though I have to tell you that it is not easy to see what your problem is, the screenshot is far too small to see any detail of what you mean.

old menubar has this:

system -> preferences and administration


new menubar has this:

system -> personal, look and feel, internet, hardware, administration, preferences

---

### Post by ajgreeny on 2009-06-25
Where did this new menu-bar come from?  I don't use the menu-bar at all, just the main gnome menu, so I have not seen what you are talking about, but perhaps it is just part of a theme you have decided to use.  If so you may need to choose another theme.

---

### Post by biasquez on 2009-06-26
> **ajgreeny said:**
> Where did this new menu-bar come from?  I don't use the menu-bar at all, just the main gnome menu, so I have not seen what you are talking about, but perhaps it is just part of a theme you have decided to use.  If so you may need to choose another theme.


ubuntu from 5.04 version, it uses this menu bar ( "Applications Places System") and it is an applet called "menu bar" (a custom menu bar)...it doesn't depends on theme.

---

