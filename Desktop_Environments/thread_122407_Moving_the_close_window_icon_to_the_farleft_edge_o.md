---
title: "Moving the close window icon to the farleft edge of the window"
date: 2006-01-27
forum: Desktop Environments
---

### Post by Amon_Re on 2006-01-27
Is it possible to have the "close window" widget on the left of a window's top bar, instead of on the right?

---

### Post by kaamos on 2006-01-27
go into *Applications > System Tools > Configuration Editor* and change *apps > metacity > general > button layout* to ":minimize,maximize,close" (without quotation). 

pasted from: [http://gnome-look.org/content/show.php?content=32768&forummode=2&forumpage=1&forumexplevel=all&PHPSESSID=a9de4463cb76110fe036864c74acad2e](http://gnome-look.org/content/show.php?content=32768&forummode=2&forumpage=1&forumexplevel=all&PHPSESSID=a9de4463cb76110fe036864c74acad2e)

---

### Post by Amon_Re on 2006-01-27
[QUOTE=kaamos]go into *Applications > System Tools > Configuration Editor* and change *apps > metacity > general > button layout* to ":minimize,maximize,close" (without quotation). 

pasted from: [http://gnome-look.org/content/show.php?content=32768&forummode=2&forumpage=1&forumexplevel=all&PHPSESSID=a9de4463cb76110fe036864c74acad2e](http://gnome-look.org/content/show.php?content=32768&forummode=2&forumpage=1&forumexplevel=all&PHPSESSID=a9de4463cb76110fe036864c74acad2e)[/QUOTE]

Hmm... I take it it's not normal that i don't have that Configuration Editor? :D 
I'll have to go & see what package that contains it....

Edit: Seems gconf-editor is installed, but not listed in the menu, go figure :D

---

### Post by kaamos on 2006-01-27
If it is installed, you can type "gconf-editor" in a terminal to start..

---

### Post by art on 2006-01-27
Or in the command line

gconftool-2 -s -t string /apps/metacity/general/button_layout close:minimize,maximize

or whichever order you want...

---

