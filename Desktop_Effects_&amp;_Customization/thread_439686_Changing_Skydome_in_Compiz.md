---
title: "Changing Skydome in Compiz"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by wayne8 on 2007-05-10
Does anyone know how to change the skydome of compiz through gconf-editor?

---

### Post by Ateo on 2007-05-10
```
$ gconftool-2 -t bool /apps/compiz/plugins/cube/screen0/options/skydome "1"
$ gconftool-2 -t string /apps/compiz/plugins/cube/screen0/options/skydome_image "/path/to/image"
```

// EDIT

Oh. Wait. Hehe.. Sorry..

Just open up gconfi-editor and make your way over to:

/apps/compiz/plugins/cube/screen0/options

Click on 'skydome' (check the box) and double click 'skydome_image' to open up the dialog to edit the image to use.

---

### Post by wayne8 on 2007-05-11
ill do it through terminal cause it will be alot quicker.
thanks

---

### Post by ReapeX on 2007-05-23
Did it work?

The terminal commands aren't working for me in feisty I get an 'Value type is only revelant when setting a value" for the first terminal command.   When I specify a wallpaper for the second line I get the same error.

---

### Post by ReapeX on 2007-05-23
In Fiesty, COmpiz seems to only recognize png files when I browse through my jpg collection...

---

### Post by ReapeX on 2007-05-23
Awesome, ok if I change the backgroup picture from GL Desktop the color of the skydome wallpaper changes to a color of the background image.

Is that what it is suppose to do?  I wanted to put a wallpaper image for my background.

---

