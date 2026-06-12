---
title: "customise gnome panels"
date: 2006-06-13
forum: Desktop Environments
---

### Post by delfick on 2006-06-13
hello

With my gnome desktop, i like to have one panel at the bottom, with these elements in this order
menubar -- window list -- desktop selector -- notification area -- deskbar -- clock -- shutdown button

I want to know if it is possible to have a background image for all of it except for the deskbar, clock and shutdown button, and to have a different image for these three elements.

And then change the colour of the text for the main menu and window list to white.?

screenshot of what i have at the moment is attached (i'm using xgl to make it semi transparent) 

I also want to know if it is possible to change the background for selected windows and the desktop switcher?

thnx for any help...

---

### Post by adam.tropics on 2006-06-13
The bacground for the panel, if an image is I believe unuversal for that whole panel. As far as colours go, you can do all sorts with  the panel.

To change text to white, and play with your panel element colours

Open or create a hidden file in your home directory called gtkrc-2.0

```
sudo gedit /home/<username>/gtkrc-2.0
```

Paste in the following and play away with the colours. You will have to figure out what relates to what, although I have a few marked.
```

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
```

Any parts you don't want to change, comment out with # at the start of the line.

If you want to see where you're at, save the file, and type in terminal,

```
killall gnome-panel
```

to restart the panel with your changes. Hours of fun eh!

---

### Post by adam.tropics on 2006-06-13
ps. If you still want an image background in panel, right click on the panel, go to properties-->background and select an image.

---

### Post by delfick on 2006-06-13
thnx for your help

the only problem is that the file doesn't seem to do anything :'(

what can i do now?

thnx

---

### Post by adam.tropics on 2006-06-13
did you restart the panel having saved the file?

---

### Post by delfick on 2006-06-13
yes i did

---

### Post by adam.tropics on 2006-06-13
ok plan b!

Delete that file, and try this , just for the text for now...[go here!]("http://www.ubuntuforums.org/showpost.php?p=494932&postcount=5")

---

### Post by delfick on 2006-06-13
hmmmm, that didn't seem to work either :'(

is my inability to theme this panel due to the fact that i'm running xgl and compiz, or shouldn't that affect the panel?

---

### Post by bluevoodoo1 on 2006-06-13
[QUOTE=adam.tropics]

Open or create a hidden file in your home directory called gtkrc-2.0

```
sudo gedit /home/<username>/gtkrc-2.0
```[/QUOTE]

You did mention it being a hidden file, but perhaps this will work...

```
gedit ~/.gtkrc-2.0
```

(added **.** to gtkrc-2.0 and removed sudo [don't need it])

---

### Post by delfick on 2006-06-14
still doesn't work....

edit: read the next post (i thought this one didn't go when i did it)

---

### Post by delfick on 2006-06-14
yay! works now

:D:D:D

---

