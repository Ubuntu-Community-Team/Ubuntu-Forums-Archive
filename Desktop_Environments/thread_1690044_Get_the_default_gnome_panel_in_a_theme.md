---
title: "Get the default gnome panel in a theme"
date: 2011-02-17
forum: Desktop Environments
---

### Post by RevJonathan on 2011-02-17
Hey all, I want to get the top panel from here-
[http://imgur.com/kJ8re&3wVeWl](http://imgur.com/kJ8re&3wVeWl)

and put it on this desktop-
[http://imgur.com/kJ8rel&3wVeW](http://imgur.com/kJ8rel&3wVeW)

This is a basic theme from gnome-look, but I don't like the status icons in it, how can I do it?

Thanks!

---

### Post by Copper Bezel on 2011-02-17
The panel itself is a part of the GTK theme, and you can just switch out images, but the status icons are part of the icon theme. You can try changing out the status icons, but not all themes follow the same directory structure and name scheme, so if the two icon themes you're looking at are different in that way, it'll take some work to match things up.

To do it, though, copy the folder of the icon theme you want, then copy in the status icons from the other theme and work them in. Your icon themes are saved in your home directory, under .icons. You'll need to hit Ctrl+H in Nautilus, "Show Hidden Files and Folders," to see the directory.

---

