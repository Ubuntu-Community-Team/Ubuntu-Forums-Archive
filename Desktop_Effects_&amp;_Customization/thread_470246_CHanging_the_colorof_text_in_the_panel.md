---
title: "CHanging the colorof text in the panel"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by k420 on 2007-06-10
I cannot figure out how tuo change the color of the text in the panel from black to white i have a dark wallpaper and can not see the time here is a screenshot [IMG]http://fs03n3.sendspace.com/dl/eba38a22372674a1b22f71d243534a7a/466c92437a274aa6/garby0/Screenshot.png[/IMG]

---

### Post by crimesaucer on 2007-06-11
Do you mean the panel where your menu, trashcan, and launchers are at?

...if so, you can make a .gtkrc-2.0 and put it in your home directory.

this is mine: 
```
style "panel"
{
  bg[NORMAL] = "#E9B9D3"
  bg_pixmap[NORMAL] = "panel89.png"
  fg[NORMAL] = "#000000"
  }

widget_class "*Panel*"      style "panel"
widget "*Panel*"            style "panel"
class "*Panel*"             style "panel"

```


the bg[NORMAL] is the color of the panel
the fg[NORMAL] is the text color for the menu and names of open apps...
the bg_pixmap[NORMAL] is for adding an image for my panel, which is like a glossy image

...this is for xubuntu...I think there is an easier way in ubuntu but I don't know it.


.....now....if you mean you have a dark theme that has the wrong font color for your apps, then you will need to change it in you gtkrc in the gtk-2.0 folder of your theme in your /usr/share/themes/THEME_YOU_ARE_USING

in there is a gtk-2.0 folder and in there is your gtkrc, open it in root and then change your fg[NORMAL] and even your text[NORMAL] if you have too...

fg[NORAML] is for Firefox browser and all menubars and toolbars

text[NORMAL] is for your File System and other things like your notepad text color...

---

### Post by k420 on 2007-06-11
hey thanks your fix worked

---

