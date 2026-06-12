---
title: "Making panels e.t.c gradient...!?!?"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by mrazster on 2007-05-02
I have a gtk-theme that I'm almost happy with...would like to have my xfcepanel gradient.
I have been looking at other gtk-themes and I have looked in the gtkrc file of theme I want to modify..but I can't "for the love of god" figure it out.

Anyone out ther care to help...or just point min the right directions...so  can fnd out my self.

If yo wan't / need the gtkrc file...just let me know and I'll post it.

---

### Post by mrazster on 2007-05-07
Anyone..??

---

### Post by mikeym on 2007-05-07
I'm having simmilar isues with trying to put effects on the panel using gtk for xfce. I've so-far failed to find any linformation on how to go about it effectively. So if anyone has any hints they'd be appreciated. This is what I've worked out so far.

I know how to put an image on the panel and colour the forground and background. 

```

style "panel"
{
bg[NORMAL] = "#ff0000"

bg_pixmap[NORMAL] = "Panel/panel-bg.png"
}

widget_class "*Panel*" style "panel"
widget "*Panel*" style "panel"
class "*Panel*" style "panel"

```

Where the image location is in relation to the gtkrc file you are working on. You will also see people putting this in panel.rc files which contain this info and are incuded in gtkrc file using an include statement.

I've used something like this to make a change to my panel so that it looks like this:

[[IMG]http://images6.theimagehosting.com/fancypanel.th.png[/img]](http://server6.theimagehosting.com/image.php?img=fancypanel.png)

but as you can see down the bottom right the 'Tray' icons are messed up also I wanted to round up the edges either by making them actualy rounder or just putting a rounded image on them but every icon on the pannel seems to display the top left corner of any image I set as a background. I was also hoping to change the separator image but I don't know how.

Hope this helps you a bit.

---

### Post by mrazster on 2007-05-13
OK...so I have to "kind of" make the panel my self and the add it to the gtkrc file...simply speaking..?

Anyone have a howto..to point me to..?..either I'm blind or dumb or mabye both :) ...but I can't find any.

---

