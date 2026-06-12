---
title: "Need help tuning xfce/Xubuntu desktop"
date: 2012-09-11
forum: Desktop Environments
---

### Post by germanix on 2012-09-11
I am a very happy user of Xubuntu but I would like to change a few things on the desktop. I just can not seem to figure out how to do it.
1. The first problem involves the icons on the desktop. The description below the icons is surrounded by a frame. I would like to remove this frame. I would also like to be able to change the font color of the icon name and  change the name/description to something different ?
2. When ever the mouse hovers on any of the launchers on the bottom panel, an information bubble appears explaining what this launcher does. I do not like this, I know what the launcher does and would like to disable this function? 
I am new to Xubuntu and have tried all of the settings in the settings-manager but to no avail. Any help/Advice will be appreciated. Thank you.

---

### Post by Dennis N on 2012-09-11
You can fix the desktop icons by editing the file ~/.gtkrc-2.0

Set **[FONT="Courier New"]XfdesktopIconView::label-alpha = 0[/FONT]** for transparency.

My ~/.gtkrc-2.0 file looks like this:

```
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 0

    base[NORMAL] = "#808080"
    base[SELECTED] = "#808080"
    base[ACTIVE] = "#808080"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

```

You can change the text color with the remaining settings.

You can change the label under the icon by right clicking on the icon and selecting properties. There is a name box you can edit.

To prevent the tooltip appearing, see post #4 below

---

### Post by germanix on 2012-09-11
Thank you Dennis N for your help. I appreciate it. For some reason I cannot edit the name box but I will try out the rest of the tips you provided. Thank you once again and have a nice day.

---

### Post by Dennis N on 2012-09-11
> **germanix said:**
> Thank you Dennis N for your help. I appreciate it. For some reason I cannot edit the name box but I will try out the rest of the tips you provided. Thank you once again and have a nice day.

On the desktop icons, realize that if you change the text under the icon, you are changing the file or folder name (which can also be done with right-click > 'rename' or press F2).

On the launcher tooltips, I found a **much easier way to hide them**: you can right click on any launcher icon down there on the bottom, select properties, then the advanced tab, and check 'disable tooltips'. This prevents the program names **and** descriptions from appearing.

---

### Post by Buntu Bunny on 2012-09-11
Good questions Germanix. Great tips Dennis.

---

### Post by GeForce 9500GT on 2012-09-12
> 1. The first problem involves the icons on the desktop. The description below the icons is surrounded by a frame. I would like to remove this frame. I would also like to be able to change the font color of the icon name and change the name/description to something different ?
[Is this what you looking for?]("http://xubuntugeek.blogspot.nl/2012/09/how-to-make-desktop-icons-text.html")

---

### Post by germanix on 2012-09-12
Yes, thank you, GeForce 9500Gt, This will certainly help. Thank you very much for responding to my question. Have a nice day.
And also great thanks to Dennis N for all the great tips. This now solves all of my issues and I am now a happy chappy.

---

### Post by JKyleOKC on 2012-09-12
Great tip! Thanks to all of you my desktop now looks much better.

---

