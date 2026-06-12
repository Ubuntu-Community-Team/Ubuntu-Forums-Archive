---
title: "Currency symbols in OpenOffice"
date: 2009-01-16
forum: General Help
---

### Post by duott on 2009-01-16
I wonder if there is any easy way to put "€" and "£" symbols in OpenOffice without having to go all the way through the menus, much like "$"?

---

### Post by fenian on 2009-01-16
Use altgr (the alt key on the right of the keyboard) 

£ = altgr+shift+4

&#8364; =altgr+5

---

### Post by duott on 2009-01-16
It doesn't work. Should I have it configured somehow?

In case it may be keyboard or DE-specific: I'm using a standard russian keyboard (layout like [this]("http://store.aramedia.com/shopimages/products/normal/russian-keyboard_l.jpg")) and Fluxbox.

---

### Post by redseventyseven on 2009-01-16
Try using various combinations of AltGr and Shift and different keys until you find the symbol you want.

---

### Post by ajcham on 2009-01-16
You could set up a compose key.  Use the command:
```
setxkbmap -option compose:rwin
```
to map the compose key to the right super-key (Windows key). Then you can enter special symbols by first pressing the compose key, followed by the sequence for that particular character (rather than pressing the keys together as you would with shift or AltGr).

£ - enter the sequence: Compose, 'L', '='
€ - enter the sequence: Compose, 'E', '=' or Compose, 'c', '='

Take note of the capitalisation in the sequence (eg. the capital L for the £ symbol)

To avoid having to manually enter the command every time you log in, add it to the end of your **~/.fluxbox/startup** file.

Also, if you prefer, you can use an alternative to 'rwin' in the above command, such as 'menu' or 'ralt' for the Menu key or AltGr.

---

### Post by fenian on 2009-01-16
You may need to enable altgr and dead keys,to do this...

Go to the menu System>Prefrences>Keyboard

Click the layout tab

Here you can change your keyboard layout,in Intrepid it shows a graphic of the keyboard look for one with the £ and &#8364; signs (on my keyboard its US International with dead keys).

After looking around a bit altgr seems lacking on some cyrillic keyboard layouts (such as the Russian one you use).I know the Ukranian Unicode layout has support for these symbols though I don't know if there is a significant difference between the Ukranian and Russian keyboard layouts,some keys may not be in the same place.

---

### Post by ajcham on 2009-01-16
> **fenian said:**
> Go to the menu System>Prefrences>Keyboard


OP is using Fluxbox, not GNOME, so I don't think it's as straightforward as that.

---

### Post by fenian on 2009-01-16
> **ajcham said:**
> OP is using Fluxbox, not GNOME, so I don't think it's as straightforward as that.

Sorry I missed the Fluxbox part,you will need to use setxkbmap to set up compose keys as described above or to change to a different layout.

---

### Post by duott on 2009-02-23
Got back to this issue just now :)

Thanks **ajcham**, it worked like charm.

---

