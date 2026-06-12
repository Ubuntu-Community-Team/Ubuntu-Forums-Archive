---
title: "Root themes not applying"
date: 2008-04-17
forum: Desktop Effects &amp; Customization
---

### Post by Jesuses Left Leg on 2008-04-17
Okay so I am trying to change the theme for when I run applications as root, such as synaptic. So I run gnome-appearance-properties as root and change all the settings to my desired ones and the window themes itself but no other application, when run as root are themed in this way, just in grey default looking colours.
Help!

---

### Post by spupy on 2008-04-17
I think this is because the gnome-settings-daemon, the program that "applies" these settings, is not running for root. It is not very efficient to run one for root, too, and I don't even think it is possible. However, you can put a file in the home of root, the file should be named ".gtkrc-2.0" (mind the point at the start). Its syntax should be the following:
```

gtk-theme-name="Aurora Borealis"
gtk-icon-theme-name="Tango"
gtk-font-name="Sans 13"
gtk-toolbar-style=0
```

This is the one I use (i don't run Gnome, so no settings daemon for me): it applies the "Aurora Borealis" theme, Tango icons, font Sans 13 and makes toolbars display only icons (no text under icons). Change the name of the theme and the icons to the ones you want. Of course, none of these options is obligatory. For example you don't need to set font-name and toolbar-style (i put them there just because they look good on my PC).

---

### Post by Jesuses Left Leg on 2008-04-17
Well thanks but it didn't get it working. The icon theme works fine by the way, just not the gtk theme. If that helps at all.

EDIT: I also forgot to mention that this is in Hardy.

---

### Post by tommyhakinen on 2008-04-18
Hi, I am having the same problem too. How do we fix it? Is there any other way?
thank you.

---

### Post by spupy on 2008-04-18
> **Jesuses Left Leg said:**
> Well thanks but it didn't get it working. The icon theme works fine by the way, just not the gtk theme. If that helps at all.

EDIT: I also forgot to mention that this is in Hardy.

Forgot something! Maybe try to copy your themes to "/usr/share/themes/". If you have your theme only in the theme folder for you user, root wont be able to apply it, because it is not looking for it there. Placing themes in "/usr/share/themes/" makes them visible for all users.

---

### Post by Jesuses Left Leg on 2008-04-19
Well I have the necessary themes in that folder. The thing is (I think I said in 1st post), when I apply the theme it applies it to the theme preference window I am running as root but no other root run apps change their theme.  I don't know if that points to a specific problem.

Example:
[[IMG]http://img59.imageshack.us/img59/6453/screenshotsz8.th.png[/IMG]](http://img59.imageshack.us/my.php?image=screenshotsz8.png)
Both those are running as root, but the theme preferences are how they should look and synaptic shows the problem.

---

### Post by tommyhakinen on 2008-04-21
I fixed it. Just open copy your currently applied theme to the /usr/share/themes

> 
sudo cp -r /home/<user>/.themes/<your current applied theme> /usr/share/themes


key in your password when prompt.

---

### Post by Jesuses Left Leg on 2008-04-22
> **tommyhakinen said:**
> I fixed it. Just open copy your currently applied theme to the /usr/share/themes



key in your password when prompt.

Unfortunately this doesn't work for me I'm not sure what the problem is.

---

