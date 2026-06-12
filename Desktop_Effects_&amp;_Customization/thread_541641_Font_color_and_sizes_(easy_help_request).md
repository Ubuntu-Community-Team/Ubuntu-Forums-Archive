---
title: "Font color and sizes (easy help request)"
date: 2007-09-03
forum: Desktop Effects &amp; Customization
---

### Post by Rylin on 2007-09-03
I recently managed to get my desktop to look very similiar to Vista, which was actually pretty easy being as I'm new to Linux. ;)

My question is how to change the text down in the taskbar to a lighter color as I can't see the text illustrated in the picture. 

My second question is the size of my text that you can see in my browser window and just in general. Wondering how I lower the font size of everything as a whole.


[[IMG]http://imagenerd.com/thumbnails/th_mydesktopzNjB.jpg[/IMG]](http://imagenerd.com/show.php?_img=mydesktopzNjB.jpg)


Much appreciated

---

### Post by ayoli on 2007-09-03
You need to edit the gtkrc file corresponding to the theme you're using. It is located in :
```
/home/<YOUR_USERNAME/.themes/<THEME_NAME>/gtk-2.0/gtkrc
```
or here (if it is a wide installed theme):
```
/usr/share/themes/<THEME_NAME>//gtk-2.0/gtkrc
```

edit this file with gedit, find a block like this (the ex is from my theme, yours should differ a bit):
```
#panel stuff
style "panelbg" 
{
  xthickness                    = 0
  ythickness                    = 0
  bg_pixmap[NORMAL]             = "panel-bg.png"
  fg[NORMAL]                    = "#ffffff" 
  fg[PRELIGHT]          = "#ffffff"
  fg[ACTIVE]                    = "#353535"
  fg[SELECTED]          = "#353535"

}
```
and for the text color you have to put/edit these to lines:
```
fg[NORMAL]                    = "#ffffff" 
  fg[PRELIGHT]          = "#ffffff"
```
#ffffff is white
#000000 is black;
#CCCCCC is a gray

---

