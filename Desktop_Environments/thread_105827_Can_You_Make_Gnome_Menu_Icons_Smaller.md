---
title: "Can You Make Gnome Menu Icons Smaller?"
date: 2005-12-19
forum: Desktop Environments
---

### Post by adie273 on 2005-12-19
I'm relatively new to Linux and been using Ubuntu for a few months now, but i'm learning well I reckon, and Windows is close to being completely removed from my computer! :p 

But thats not the point...

Does anyone know how to make the icons on the Gnome menu smaller? (The Application, Places and System menu's) They are kinda big compared to the fonts, and I think its because of this that the menu is slightly larger than it has to be. Not a serious problem, its purely a cosmetic thing that i'd prefer, but if anyone knows if its possible and could tell me how, it'd be much appreciated. 

Its Ubuntu 5.10 if that changes how it may be done in anyway.

Thanks!

---

### Post by toya on 2005-12-19
resize the panel? (right click then properties)

---

### Post by adie273 on 2005-12-19
Its the icons in the actual menu's that I would like smaller, if its possible.

To be more specific I mean the icons beside Accessories, Internet, Games, Preferences etc, when u goto either of the Application, Places or System menu's. (If that makes any sense) :)

---

### Post by leech on 2005-12-19
I think you'd have to resize the icons in the themes that you use.  I believe they use the 24x24 icons.  Not sure if there is a gconf setting for this or not.  

Would be kind of useful, though I don't have a problem with the icon size myself.

Leech

---

### Post by arazaxirelcinellersadolur on 2005-12-25
[QUOTE=adie273]Its the icons in the actual menu's that I would like smaller, if its possible.

To be more specific I mean the icons beside Accessories, Internet, Games, Preferences etc, when u goto either of the Application, Places or System menu's. (If that makes any sense) :)[/QUOTE]

hi,
i wonder can you did that menu icons smaller? if yes, please inform me too
best regards,

---

### Post by bucik-sb on 2006-02-22
To file **gtkrc** in your thema add line:
[LIST]gtk-icon-sizes = "panel-menu=xx,xx"
[/LIST]where xx is icon's size (in pixels)

---

### Post by craig552 on 2006-07-14
> **bucik-sb said:**
> To file **gtkrc** in your thema add line:
[LIST]gtk-icon-sizes = "panel-menu=xx,xx"
[/LIST]where xx is icon's size (in pixels)

What file do I put this in?
I can't edit my index.theme file

---

### Post by otto67 on 2006-07-18
Go to the theme folder. Every gnome themes have **"gtk-2.0"** folder. Open it - there is a file **"gtkrc"**. Edit this as mentioned by bucik-sb. There can be already the line
**gtk-icon-sizes = "panel-menu=xx,xx"**. Edit this.!
If not - add this line and put an icon size you like. Reload the theme and thats it!!

---

### Post by sk545 on 2007-12-18
Anyone tell me where the "theme" folders are in gutsy?

---

### Post by craigisaloser on 2008-05-27
Ubuntu themes are in /usr/share/themes (in gutsy gibbon)

---

