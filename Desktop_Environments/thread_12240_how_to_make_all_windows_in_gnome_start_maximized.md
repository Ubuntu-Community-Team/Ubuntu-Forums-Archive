---
title: "how to make all windows in gnome start maximized?"
date: 2005-01-23
forum: Desktop Environments
---

### Post by jerome bettis on 2005-01-23
hi

this always bugs me.  everytime i open terminal, file manager, etc etc i get a little window about 1/4 the size of the screen and i'm tired of having to maximize it everytime.

yes i am really that lazy :p

is there a way to set it up so that all windows open maximized?  i looked through most of the settings and didn't see anything.  perhaps i missed it or i can edit some file ?

thanks

---

### Post by jerome bettis on 2005-01-25
bump

---

### Post by ow50 on 2005-01-25
I don't know about maximizing, but at least you can play around with the window sizes and positions. For both nautilus and gnome-terminal you can use the "--geometry" switch.

For example, I have my terminal launcher command set to 
```
gnome-terminal --geometry=95x40+230+205
```
which will open a window with width 95, height 40 (I think the unit is characters) 230 from the left side of the screen and 205 from top (I think these units are pixels).

Similarly i have in my .bashrc the line
```
alias nautilus='nautilus -g 800x570+240+195'
```

The size always works but the position seems to work only for the first window opened.

---

### Post by Jose Catre-Vandis on 2006-05-14
Thanks ow50, useful to know

---

