---
title: "Easy Panel Question"
date: 2008-03-25
forum: Desktop Effects &amp; Customization
---

### Post by BRFC on 2008-03-25
I've set the panel at the top of my screen to be almost transparent but as my background is black is there any way to change the panel text colour, Applications, Places etc to white.

---

### Post by alenis on 2008-03-25
I had a similar problem and I found a solution on this forum. Unfortunately,  I can no longer find a link to that thread  but I saved the relevant information, which follows:

```
To change text to white, and play with your panel element colours

Open or create a hidden file in your home directory called gtkrc-2.0
Code:
sudo gedit /home/<username>/gtkrc-2.0
Paste in the following and play away with the colours. You will have to figure out what relates to what, although I have a few marked.
Code:
style "panel"
{
  fg[NORMAL]               = "#ffffff"#panel txt normal
  fg[PRELIGHT]            = "#ffffff"
  fg[ACTIVE]               = "#ffffff"
  fg[SELECTED]            = "#ffffff"
  fg[INSENSITIVE]            = "#ffffff"
  bg[NORMAL]               = "#85897F" #Background of switcher and wl fine outline
  bg[PRELIGHT]            = "#000000"#Mouseover wl
  bg[ACTIVE]               = "#000000"#Selected wl
  bg[SELECTED]            = "#000000"#Mouseover outline
  bg[INSENSITIVE]            = "#FAFF00"#??
 base[NORMAL]            = "#5D605A"#Background of things like deskbar or 'add to panel'
  base[PRELIGHT]            = "#ffffff"#fine outline on windowlist items
  base[ACTIVE]            = "#ffffff"
  base[SELECTED]            = "#ffffff"
  base[INSENSITIVE]         = "#ffffff"

  text[NORMAL]            = "#ffffff"
  text[PRELIGHT]            = "#000000"
  text[ACTIVE]               = "#000000"
  text[SELECTED]            = "#ffffff"
  #text[INSENSITIVE]            = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
Any parts you don't want to change, comment out with # at the start of the line.

If you want to see where you're at, save the file, and type in terminal,
Code:
killall gnome-panel
to restart the panel with your changes. Hours of fun eh!
```

---

### Post by applehead on 2008-03-25
my advise would be to use a lighter back ground or a picture

---

### Post by wxnker on 2008-07-13
use gnome-color-chooser :)

---

