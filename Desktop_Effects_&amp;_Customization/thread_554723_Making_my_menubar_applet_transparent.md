---
title: "Making my menubar applet transparent?"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by drazgo on 2007-09-19
hi everyone, got a question concerning the menubar applet of ubuntu. I am making my ubuntu look like leopard, but the menubar applet won't become transparent when i set the panel so. 

Anyone knows how to do so?

thanks in advance!
Drazgo

---

### Post by Lord Illidan on 2007-09-19
Got a screenshot? Some themes, I recall won't let you set the whole applet to transparent. What theme are you using?

---

### Post by drazgo on 2007-09-19
This is the theme i am using: 

[http://www.gnome-look.org/content/show.php/Kougyoku-Leopard?content=62592](http://www.gnome-look.org/content/show.php/Kougyoku-Leopard?content=62592)

And I'm using this panel background: 

[http://i1.tinypic.com/4z2oi6b.png](http://i1.tinypic.com/4z2oi6b.png)

And here's a screenshot of my desktop. As you can see, the menubar won't blend with my panel background:

[http://www.sendspace.com/file/uq60hs](http://www.sendspace.com/file/uq60hs)

---

### Post by FuturePilot on 2007-09-19
Yes, that's because of the theme. If you want you can probably delete the image from the theme. You'll have to find it though, in /home/USER/.themes/theme_name/

---

### Post by Lord Illidan on 2007-09-19
Yes, you can do it.

Delete this file ~/.themes/Kougyoku-L/gtk-2.0/panel-bg23.png

or else rename it.

like this : ```
mv ~/.themes/Kougyoku-L/gtk-2.0/panel-bg23.png mv ~/.themes/Kougyoku-L/gtk-2.0/panel-bg23.png.backup
```

The ~ stands for your home directory by the way. like /home/jean in my case.

---

### Post by kteagan84 on 2007-09-19
Just out of curiosity, can anyone let me know how to install the menubar applet? I don't want my desktop to look like OS X, I only want my menus to show up on my top panel along with my current theme settings. So far, all of the tutorials only explain how to do it alongside a total OS X theme.

---

