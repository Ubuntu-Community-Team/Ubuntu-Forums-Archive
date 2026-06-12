---
title: "How to Change Ubuntu logo"
date: 2007-10-18
forum: Desktop Effects &amp; Customization
---

### Post by pavankumar25386 on 2007-10-18
How to change the Ubuntu logo at the top panel near applications,Places????

---

### Post by joshuachad on 2007-10-18
First download your logo. So now you have a start button and you want to change it from the default. By the way when you say Ubuntu logo i assume you mean the start button on the panel. At any rate go to a terminal and run gconf-editor. Go to apps >> panel >> objects and then there should be  a menu object. It will be named maybe differently on your system but mine is menu_bar_screen0. Ok so click on that then check the box next to "use custom icon" Then go to the key that say "custom icon" and type the path to your custom icon image there. Blammo you should be good to go.

---

### Post by &#1056;&#1091;&#1089;&#1083;&#1072;&#1085; on 2007-10-21
to change distributor-logo in Ubuntu:
worked for me.
first make 48x48 png image(I did it in gimp), place it in your home directory.
search for distributor-logo.png in file system. save results to file(right click in the list, save results as., open file and in terminal replace all found ubuntu-icons by: sudo cp /home/your name/distributor-logo.png /paste/ here/ icons/ gnome/ found/
Then I  did: gtk-update-icon-cache and killall gnome-panel in terminal. 
that&#347; all.

---

