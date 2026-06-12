---
title: "Changing Nautilus icons?"
date: 2005-07-08
forum: Desktop Environments
---

### Post by Grunt on 2005-07-08
Hello all,

Does anyone know how the Nautilus icons can be changed (icons like forward, up, backward). I've been trying to find a thread about this, but unfortunately I've had no succes so far. I do know, that when I change a Gnome icon theme, the "Home" icon in Nautilus changes, but the other icons stay the same. This happens both with newly installed icon themes and with standard Gnome themes.

Merci!

---

### Post by varunus on 2005-07-08
These icons are called "stock" icons, and they are changed by certain gtk2 themes, not icon themes.  (Yes, I know, confusing.)  Some icon themes include stock icons, but to use them, you have to copy or symlink a folder into the gtk2 theme you want to use, and then add the line "include iconrc" (varies for different themes) to the gtkrc.  An example of a theme that has stock icons would be the MunjaRemix theme, which uses stock icons from GNANT.  (Examples taken from [www.gnome-look.org](www.gnome-look.org))

---

### Post by Grunt on 2005-07-08
Thanks for the reply! I will give it a try as soon as possible.

---

### Post by Grunt on 2005-07-10
Well, I've been trying to change it but no success so far. Is there maybe a good tutorial out there that works out a few examples? (to be honest I'm not too sure what I'm exactly doing)

Thnx!

---

### Post by Morimando on 2005-07-10
In Gnome's System Menu under "Settings" select the Theme Settings. The themes will change nautilus' look and also the colours of your Gnome-DE.
More themes available on the Gnome project homepage

---

### Post by Grunt on 2005-07-10
Hi, I have already tried that but with no luck. The only icon that changes in the Nautilus window is the "Home" icon. All the other icons (like forwared and backward) stay the same. 

I have no real luck finding a decent tutorial about stock icons. The configuration files are pretty complex.

---

### Post by frodon on 2005-07-11
Ok
I haven't tested it but, find a theme which change the nautilus icons (look at gnome-look.org), install the theme. The icons of the theme are located in /home/user_name/.icons/theme_name, so I think you just have to replace the icons by those you want and use this theme and it will work.

---

