---
title: "openbox &amp; nautilus issue"
date: 2007-02-02
forum: Desktop Environments
---

### Post by buuntuu! on 2007-02-02
hi everybody

i am checking out openbox and am quite impressed by its speed and ergonomics! (less is more!)
i've got a minor issue though.
starting nautilus it somehow pulls up my gnome-wallpaper, which remains after closing nautilus...
is there a way to prevent that? (other than using the same wallpaper, that is;))
or has anyone any suggestions about an other file manager that will work fine in openbox?
regards

buuntuu!

---

### Post by Richard Kut on 2007-02-02
Hello! Try thunar, which is much lighter and quicker than nautilus. Also, have a look at leafpad for text editing. Way faster than gedit! Good luck.

---

### Post by buuntuu! on 2007-02-02
thanks 4 the quick reply, i'll check it out immediately:)

---

### Post by moore.bryan on 2007-02-02
[I]if you like light and fast, i prefer xfe over thunar, but it's always about personal choices with us silly linux folk...
;-)
[/I]

---

### Post by buuntuu! on 2007-02-03
i've found that out by now and that's exactly why linux is that good:)will try out some of the myriads of choices! thanx

---

### Post by fuscia on 2007-02-06
*nautilus --no-desktop* is the command you're looking for.

---

### Post by ardchoille42 on 2007-02-06
> **buuntuu! said:**
> hi everybody

i am checking out openbox and am quite impressed by its speed and ergonomics! (less is more!)
i've got a minor issue though.
starting nautilus it somehow pulls up my gnome-wallpaper, which remains after closing nautilus...
is there a way to prevent that? (other than using the same wallpaper, that is;))
or has anyone any suggestions about an other file manager that will work fine in openbox?
regards

buuntuu!

If you want to disable nautilus's management of the desktop on a permenant basis, open gconf-editor and uncheck the following boxes:

/apps/nautilus/preferences/show_desktop (disables the gnome desktop menu)
/desktop/gnome/background/draw_background (disables the gnome background image)

I use openbox as my window manager in gnome (got rid of Metacity, it sucks) and that is how I stopped nautilus from taking over my desktop.

---

### Post by buuntuu! on 2007-02-09
thanks ardchoille42 and fuscia, i was very interested in what caused the nautilus"problem".
with openbox i am sticking to xfe, kind of fits...

>  I use openbox as my window manager in gnome (got rid of Metacity, it sucks) and that is how I stopped nautilus from taking over my desktop.
what exactly makes you dislike metacity? i tried openbox under gnome as well, but i liked the default style better...

---

