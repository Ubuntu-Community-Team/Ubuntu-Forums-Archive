---
title: "installing own emblem to a folder"
date: 2007-03-16
forum: Desktop Effects &amp; Customization
---

### Post by Sbarton on 2007-03-16
Hi all! Is it possible to add my own emblem to a folder. Example: Folder is called PDF' s. I have a 'Acrobat' logo (.jpg) that I would like to use as the emblem for that folder. Can this be done. I don't see any way to import into the 'Emblems' box.
regards

---

### Post by Sbarton on 2007-03-17
Sorry to bump this! If there is a way I would like to know as there are other emblems I would like to add. The ones available do seem limited.
regards

---

### Post by Redeyes_Gambit on 2007-03-17
Well I found where the icons are kept. If you go to usr/share/icons and then pick a theme, then look under the various resolutions you can see "emblem" folders with emblems in them. My guess is you could create a custom icon theme with emblems in it. Thing is I'm not sure how to create an icon-theme.cache or an index.theme file.

Maybe [www.gnome-look.org](www.gnome-look.org) forums have information on icon theme file creation. Or, maybe they have an easier way to add emblems. Chances are the answer is there. :)

---

### Post by Sbarton on 2007-03-18
SOLVED!!
Thanks for the reply R_G! I created the icon simply by copying the Acrobat icon, resizing it to 48x48 pixels and saving it to the desktop. I then found the following worked. 
* In Nautilus File Browser, I went to 'view' and selected 'Show  Hidden Files'
* Scrolled down to ( .icons) single clicked it.
* Single clicked (Hicolor)
* Single clicked  48x48
* Drag'n' Dropped the icon into the emblems folder. 
After that I just went through the normal way to change the emblem on the folder.

Hope this can help some other person who wants to add some emblems to cache.
I think there is another way to achieve it via /user/share etc.
regards.

---

### Post by Phantomgraph on 2007-06-10
Actually, their is an easier way. I'm adding this a little late mostly because I had to re-remember how to do this. ;)

[LIST=1]
[*]Open Nautilus (Places, Home Folder)
[*]Select Edit, Backgrounds and Emblems from the menu.
[*]Select The Emblems Tab/Button
[*]Use the + Add New Emblem button.
[/LIST]

Enjoy }:8>

---

