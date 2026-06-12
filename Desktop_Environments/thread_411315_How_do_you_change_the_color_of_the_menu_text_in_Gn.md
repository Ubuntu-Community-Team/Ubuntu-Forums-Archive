---
title: "How do you change the color of the menu text in Gnome?"
date: 2007-04-16
forum: Desktop Environments
---

### Post by Happy_Man on 2007-04-16
Hey all,

I just found this awesome new background. Only problem is, it's black. And so, now I can't see my menu text. Y'know, up at the top it says "Applications, Places, System"? I've been hunting around gconf -- no luck. Anybody know how to get this?

---

### Post by ComplexNumber on 2007-04-16
i need a little more information. is your panel is completely transparent or something? do you have a screenshot? 

you could use a dark theme because a) dark themes go better with dark wallpaper, and b) the text is usually white or light grey.

---

### Post by Happy_Man on 2007-04-16
That's my menu. I need white text instead of black. Sorry about the really hacked together GIMP job...I'm not very good at it. :oops:

---

### Post by ComplexNumber on 2007-04-16
you could try using a dark theme instead or a light theme that uses a dark panel such as Linsta. there is a way of changing just the text of the menubar, but i don't know how, exactly.

---

### Post by kerry_s on 2007-04-16
You can use a gtkrc-2.0, i'll have to look it up and get back to you.
i know it's 1 of these.

```
  fg[NORMAL]      = "#000000" 
  fg[PRELIGHT]    = "#000000" 
  fg[ACTIVE]      = "#000000" 
  base[NORMAL]    = "#ffffff"
  base[SELECTED]  = "#84a8cc"
  base[ACTIVE]    = "#84a8cc"
```

---

### Post by kerry_s on 2007-04-16
Try this:

```
gedit .gtkrc-2.0
put->

style &#8220;my_color&#8221;
{
fg[NORMAL] = &#8220;#FFFFFF"
}
widget &#8220;*.Panel.*&#8221; style &#8220;my_color&#8221;
```

---

### Post by ComplexNumber on 2007-04-16
i think the widget it is GtkMenuBar, but i tried that earlier and it didn't work. i just don't know the exact syntax.

---

### Post by notwen on 2007-04-16
This [thread]("http://ubuntuforums.org/showthread.php?t=397971") might prove useful, hope it helps. =]

---

