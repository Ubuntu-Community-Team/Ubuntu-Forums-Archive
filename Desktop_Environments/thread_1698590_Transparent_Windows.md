---
title: "Transparent Windows"
date: 2011-03-02
forum: Desktop Environments
---

### Post by davidy0 on 2011-03-02
Sup, long time windows user recently switched to Ubuntu due to XP's lack of customisation and general ease.

So I Have compiz installed and I'm currently on the Opacity, Brightness and Saturation setting. I've set it to Shift Up to increase opacity and shift down to decrease. However it doesn't effect multiple windows and I would like it to be like this at startup.

TLDR: How can I make compiz opacity settings affect all windows and run at startup?

thanks guys!

---

### Post by nilarimogard on 2011-03-02
I think you want [RGBA transparency]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html").

---

### Post by davidy0 on 2011-03-02
I managed to make it work myself in Compiz after some more research.

I added a new Window Specific setting with the text:

```
Tooltip | Menu | PopupMenu | DropdownMenu | Dock |  type=Normal
```

and set the value to 95.

---

### Post by Copper Bezel on 2011-03-03
You could also just use "any", which is a wildcard. I'd suggest putting in a rule for 

state=fullscreen 

at 100% opacity, for Flash videos, Movie Player, etc.

If you get annoyed with the practical side effects of having all windows transparent, look into Trailfocus instead, which can be set to keep the focus window opaque while unfocused windows become transparent. Another (practical) use of the opacity settings is in Move Window, which allows windows to turn transparent while you're dragging them, useful for keeping track of what you're doing. 

I personally use transparent menus and tooltips because the desktop feels painfully flat without them, but as cool as it looks, even 5% transparency can become a pain in the ***, especially when working with images.

RGBA transparency looks cool for the five things it actually affects, but it's visually inconsistent and doesn't work with more than a handful of themes, anyway, so I wouldn't recommend it. If you're interested in something like that, I'd take it halfway with an Emerald theme or just switch to KDE.

---

### Post by TylerBraun on 2011-07-13
> **Copper Bezel said:**
> You could also just use "any", which is a wildcard. I'd suggest putting in a rule for 

state=fullscreen 

at 100% opacity, for Flash videos, Movie Player, etc.

Thanks for that. The grab tool doesn't have state as an option and for some reason I keep on remembering it as "all" and with no syntax guide for it online (as far as I could find) I was struggling. You're a big help. :)

---

