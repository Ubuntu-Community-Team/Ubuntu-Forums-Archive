---
title: "Cursor in firefox"
date: 2006-08-18
forum: Desktop Environments
---

### Post by loserboy on 2006-08-18
hey I use gcursors to change out my mouse cursors, but when im moused over FF and a page is loading it changes it back to default, anyone know of any fixes, i searched and found a couple people with the same problem but no fix.

thanks

---

### Post by wachunei on 2006-08-19
I have this same annoying problem, help guys, my default cursor now is a black one, not the Human one :S

---

### Post by janhenderson on 2006-08-19
> **wachunei said:**
> I have this same annoying problem, help guys, my default cursor now is a black one, not the Human one :S

I don't know about Gnome but I switched to KDE and I don't see a problem with the cursor in firefox, it looks just like it does all over kde.

---

### Post by loserboy on 2006-08-19
well i think i see what it is, some of the icon packages don't seem to have an icon for the one it shows when FF is loading a page, as for the black cursor thing i havent seen that, but i know you can go into gconf and change cursors and its prolly more powerful than gcursor

---

### Post by mayhemt on 2006-09-10
Although you can select your favorite cursor in gnome, firefox & some other applications tend to use their own cursors or some other default cursor theme.

If you want to use your own theme, just follow this.

$cd ~
$nano .gtkrc

(you can use your own editor kate/gedit/xedit )

add this line at the end.

gtk-cursor-theme-name="Human"

Instead of Human, put your favorite cursor theme & restart firefox.

Enjoy!!

:D 

[http://tuxhelps.blogspot.com/2006/09/clean-hack-to-change-your-firefox.html](http://tuxhelps.blogspot.com/2006/09/clean-hack-to-change-your-firefox.html)

---

