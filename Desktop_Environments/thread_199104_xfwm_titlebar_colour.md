---
title: "xfwm titlebar colour"
date: 2006-06-18
forum: Desktop Environments
---

### Post by Beej on 2006-06-18
I have been using the rezlooks engine for a while now, and have installed a new theme

[http://http://www.xfce-look.org/content/show.php?content=40990]("http://http://www.xfce-look.org/content/show.php?content=40990")

In the screen shot the window manager (openbox I think) is black, when I apply the theme, my window manager (xfwm) reflects the gtk colour, which is the green colour in the rest of the theme, not the black I would like.

Does anybody know how to make the wm colour a different colour to the GTK one?

Thanks,

Beej.

---

### Post by psychicdragon on 2006-06-18
You have to edit the themerc file included in your xfwm4 theme.

Add a line like this one:
active_color_1=#000000

The restart xfce, or change the xfwm4 theme, then change it back.

There are some other color values you can change as well. Here's a page that lists them all.:[http://www.xfce.org/xfwm4-theme-howto/]("http://www.xfce.org/xfwm4-theme-howto/")

---

