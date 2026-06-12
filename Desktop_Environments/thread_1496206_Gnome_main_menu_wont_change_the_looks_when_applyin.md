---
title: "Gnome main menu wont change the looks when applying a new theme"
date: 2010-05-29
forum: Desktop Environments
---

### Post by Zireth ZH on 2010-05-29
Whenever i try to apply  a new theme .. everything seems to be ok except the gnome menu ... sometimes when applying icons, depending on the theme you can see it has applied almost everywhere except when u go to "Places" the icons there in the gnome menu is still on default.. have a look at the screenshot here.. sorry for my bad english [IMG]http://i221.photobucket.com/albums/dd168/hilderith/Screenshot.png[/IMG]

---

### Post by UberStudent on 2010-05-29
Changing your theme from the graphical tool *should* make the changes show immediately.

To troubleshoot, make sure you have read permissions into the folder and all the files of your theme, then try to change the theme again. If they still fail to show, open a terminal and run

```
killall gnome-panel
```Do the changes show then?

Also, some themes do not override certain gnome-panel settings so there may not be any changes beyond the icons, if you also change them.

---

### Post by hok00age on 2010-05-29
> **Zireth ZH said:**
> Whenever i try to apply  a new theme .. everything seems to be ok except the gnome menu ... sometimes when applying icons, depending on the theme you can see it has applied almost everywhere except when u go to "Places" the icons there in the gnome menu is still on default.. have a look at the screenshot here.. sorry for my bad english [IMG]http://i221.photobucket.com/albums/dd168/hilderith/Screenshot.png[/IMG]

You might consider read this article:
[http://www.webupd8.org/2010/05/script-to-fix-panel-for-all-themes-at.html]("http://www.webupd8.org/2010/05/script-to-fix-panel-for-all-themes-at.html")

Hope it helps you
Regards :)

---

### Post by hictio on 2010-05-30
> **Zireth ZH said:**
> 
~snip~
... sometimes when applying icons, depending on the theme you can see it has applied almost everywhere except when u go to "Places" the icons there in the gnome menu is still on default.. 
~snip~


The icons on the "Places" menu entry -the default ugly grey Gnome folders for directories- sometimes don't change when you apply a new theme, it usually helps to logout and back in.

---

