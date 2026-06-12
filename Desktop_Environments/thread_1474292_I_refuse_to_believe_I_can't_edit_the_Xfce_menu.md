---
title: "I refuse to believe I can't edit the Xfce menu"
date: 2010-05-05
forum: Desktop Environments
---

### Post by directedition on 2010-05-05
Everywhere I search is full of people saying that it's impossible to edit the xfce menu. How could this be?! Somewhere on my machine is a file that maps the label "Disc Usage Analyzer" to "baobab". I must locate this file and destroy it! Sadly, I just can't find this mapping file for the life of me. Where could it be hiding?!

---

### Post by kerry_s on 2010-05-05
/usr/share/applications holds the menu items, you can edit them with a text editor as root.

to remove from menu add-> **NoDisplay=true**
Categories=* is where it go's in the menu

it's actually very simple.

---

### Post by zflyer on 2010-05-06
here is the guide to customize the xfce menu:
[http://wiki.xfce.org/howto/customize-menu](http://wiki.xfce.org/howto/customize-menu)

---

