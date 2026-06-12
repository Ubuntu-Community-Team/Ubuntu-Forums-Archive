---
title: "terminal transparency issue"
date: 2012-02-03
forum: Desktop Environments
---

### Post by GraeW on 2012-02-03
tinkering around with my xfce, and have installed the old aterm emulation for when I want a CLI to check things. I've set the terminal window to open up with some transparency, but when I start up, instead of seeing the desktop background I have selected (a picture from my recent wedding) I see the purplish-pink default background from I presume gnome/nautilus/lightdm.
 
When I look to see if nautilus snuck in the background, I don't see it (it doesn't pop up on top, and if I do a kill command from the CLI it just says "not running").
 
Any ideas where this behind-the-scenes-background might be sneaking in from? and more importantly, how can I get it to stop harrassing the picture I want to see? ;)
 
Thanks

---

### Post by Rodney9 on 2012-02-03
Lots of Aterm tips in this guide - 

[http://linuxreviews.org/software/x11-terms/aterm/](http://linuxreviews.org/software/x11-terms/aterm/)

Rodney

---

### Post by m_duck on 2012-02-03
I think the gist of it is that aterms transparency is a pseudo-transparency so, instead of drawing what is actually just behind it, it draws what is currently displayed on the root window (i.e. right at the back). This presumably gets set by lightdm (though that's a guess).

If you don't change your wallpaper much, a bit of a bodge-fix would be to set your root wallpaper to the same as your XFCE wallpaper (which is actually on top of the other) with a program such as feh or nitrogen, e.g.

```
feh --bg-scale ~/Pictures/the_wallpaper_you_want.png
```

The downside might be if lightdm (or whatever) sets the wallpaper on every boot, but you could add the above code as an autostarting item.

Another alternative would be to use the XFCE terminal, as it supports true transparency (if compositig is enabled).

---

### Post by GraeW on 2012-02-03
xfterm now has full transparency.. I did not realize. I will have to go back and tweak this weekend - give me something to do besides watch the stuporbowl ;)
 
thanks!

---

### Post by GraeW on 2012-02-03
xfterm4 .. transparent and sized how I want it.. perfect and thanks again!

---

