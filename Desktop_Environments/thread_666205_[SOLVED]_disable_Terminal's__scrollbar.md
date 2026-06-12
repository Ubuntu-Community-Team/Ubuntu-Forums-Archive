---
title: "[SOLVED] disable Terminal's  scrollbar ?"
date: 2008-01-13
forum: Desktop Environments
---

### Post by salah_tr on 2008-01-13
Hi all :) ,
How to disable Terminal's scrollbar :?:
I tried the following procedure but it didn't work
:arrow: start **gconf-editor**  
:arrow: go to** /apps/gnome-terminal/profiles/Default/**
:arrow: set **scrollbar_position** to **disabled** 

Cheers 
salah

---

### Post by mcduck on 2008-01-13
It seems that the help text for that key in gconf-editor gives a bit of misinformation..

The right value for the key is 'hidden'. I have disabled the scroll bar through gnome-terminal's menus and that is what it set's the key's value to.

You can also just select Edit/Current Profile in Gnome-terminal, and then disable the scrollbar in the 'Scrolling'-tab.

---

### Post by Subban on 2008-01-13
I would have thought that choosing "Profiles" from the edit menu of the terminal and then hilight "Default" and click Edit button, then go to the scrolling tab and select to disable the scroll bar might be the better way :]

---

### Post by salah_tr on 2008-01-14
thank you mcduck and Subban for help :)

---

