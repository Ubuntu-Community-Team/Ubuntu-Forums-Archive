---
title: "Menu icons"
date: 2011-10-15
forum: Desktop Environments
---

### Post by lovinglinux on 2011-10-15
Anyway to get the menu icons back on 11.10?

I used to edit the *desktop/gnome/interface/menus_have_icons* entry on gconf-editor, but that doesn't seem to work anymore. I am not sure if this didn't work since Natty because I was using KDE until now.

---

### Post by Krytarik on 2011-10-15
> **lovinglinux said:**
> I used to edit the *desktop/gnome/interface/menus_have_icons* entry on gconf-editor, but that doesn't seem to work anymore.
Is this setting even still in GConf, or instead in DConf, like many other settings now?
I don't remember where I've found it in Oneiric, and I can't check it myself right now.

But I do know that you can also change those setting via "Gnome Tweak Tool", and that it's still affecting the usual in-app menus, but *not* the Global Menu, annoyingly.

Regards.

---

### Post by lovinglinux on 2011-10-15
> **Krytarik said:**
> Is this setting even still in GConf, or instead in DConf, like many other settings now?
I don't remember where I've found it in Oneiric, and I can't check it myself right now.

But I do know that you can also change those setting via "Gnome Tweak Tool", and that it's still affecting the usual in-app menus, but *not* the Global Menu, annoyingly.

Regards.

It is still present on GConf, but Dconf works. Thanks.

---

### Post by liufu_ty on 2011-10-26
Hi there, but can you please show me how to do it in details?
I have to same needs and I am new to Ubuntu, thanks :)

---

### Post by lovinglinux on 2011-10-27
> **liufu_ty said:**
> Hi there, but can you please show me how to do it in details?
I have to same needs and I am new to Ubuntu, thanks :)

Install Dconf from the Software Center, then search for it on your Dash and launch it. Then click "org >> gnome >> desktop >> interface", then tick the option **menus-have-icon**s.

---

