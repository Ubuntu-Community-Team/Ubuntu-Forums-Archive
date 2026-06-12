---
title: "How To Get A Transparent Panel In 10.04"
date: 2010-06-29
forum: Desktop Environments
---

### Post by Jakiejake on 2010-06-29
This is for the Ambiance Theme (Default for 10.04)
Here's How To Make It transparent
Run This In Terminal
> gksu gedit /usr/share/themes/Ambiance/gtk-2.0/gtkrc
If it asks for your password, enter it!
You should get a gedit window like this
[IMG]http://img199.imageshack.us/img199/702/screenshotgtkrcusrshare.png[/IMG]
Now search for this line
> bg_pixmap[NORMAL] = "panel_bg.png"
Once You Have Found it insert a hash (#) in front of it
It should look like this now
> #bg_pixmap[NORMAL] = "panel_bg.png"
Now save and close
Log Out And Log Back In
Now you can set it as transparent
[IMG]http://img444.imageshack.us/img444/9380/screenshotpanelproperti.png[/IMG]
Enjoy!
[IMG]http://img149.imageshack.us/img149/7829/screenshotya.png[/IMG]

---

### Post by ubunterooster on 2010-06-29
Cool! Thanks.

---

### Post by gingivere0 on 2010-06-29
This is cool, but how would I do it with the Tropical theme?  Thanks for showing how to make it transparent, I've been trying for a while. :D

---

### Post by bigsmitty64 on 2010-06-30
**Thanks!**   Now, to get rid of that pesky leftover shadow? :(

---

### Post by nilarimogard on 2010-06-30
There's also a [script]("http://www.webupd8.org/2010/05/script-to-fix-panel-for-all-themes-at.html") that fixes the GNOME panel background for most of the themes at once. "Most" because it doesn't work for all due to some themes not having the panel declared as bg_pixmap[NORMAL].

---

### Post by Jakiejake on 2010-06-30
Glad I could help
I found it on a blog a day or so ago
I just changed the code command a bit to make it easier and posted it on here!

---

### Post by mcduck on 2010-06-30
> **bigsmitty64 said:**
> **Thanks!**   Now, to get rid of that pesky leftover shadow? :(

The shadow isn't created by the panel, or your GTK theme, it's made by Compiz just like all the other window shadows you have.

So, to remove it, you need yo edit your Compiz settings. To do that install CompizConfig Settings Manager (if you haven't got it already), browse to "Window Decoration"-plugin's settings and change the "Shadow windows"-field from "any" to "!(class=Gnome-panel)"

---

### Post by celldweller1591 on 2010-06-30
Good one there :)
One can also try RGBA transparency effect in ubuntu to make Drop down menus and window borders look transparent to your choice.

---

### Post by ubunterooster on 2010-06-30
> **celldweller1591 said:**
> Good one there :)
One can also try RGBA transparency effect in ubuntu to make Drop down menus and window borders look transparent to your choice.
Please elaborate.

---

### Post by steveneddy on 2010-06-30
To make the panel and the menu's TRULY transparent:


## make gnome bar true transparent

> if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->compizconfig settings manager
Click on Opacity, Brightness and saturation under the Accessibility options settings, and add the following entry at bottom of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you dont have the Compizconfig Settings manager, just install it:
sudo apt-get install compizconfig-settings-manager

this will make entire panel transparent

If it is truly transparent you can see the windows behind it when you move a window behind it. The way described in the original post is pseudo transparency.

EDIT:

TO make the menus transparent, add a line and in the field add:

```
Tooltip | Menu | PopupMenu | DropdownMenu
```

and start with a transparency number of 80 and tweak from there to taste.

---

### Post by bigsmitty64 on 2010-06-30
> **mcduck said:**
> 

  edit your Compiz settings. To do that install CompizConfig Settings Manager ,change the "Shadow windows"-field from "any" to "!(class=Gnome-panel)"

nice! (I Had ccsm already)

---

### Post by celldweller1591 on 2010-06-30
> Please elaborate.see [this page]("http://www.webupd8.org/2010/05/enable-rgba-transparency-in-ubuntu-910.html") fore details .. can write that much ATM :D

---

### Post by ubunterooster on 2010-06-30
Another fun project to do, thanks. :D

---

### Post by gingivere0 on 2010-06-30
steveneddy I found that using both yours and the OP's methods because yours offers true transparency, but it also lowers the color quality on the icons in the panel.  Jakiejake's method keeps the color quality in the panel, but it doesn't interfere with the true transparency that you suggested. Thanks for showing me how to make my panels look better

---

### Post by celldweller1591 on 2010-06-30
i just tested it if it works and then removed it coz it caused screen flickers @ /1024*768 res or higher, 60hz, intel dual core(2.0 GHz) 2gb ram and 128 mb Vram. Thats why i swicthed it off.

---

