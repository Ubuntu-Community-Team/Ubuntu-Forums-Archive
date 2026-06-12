---
title: "XFCE4, compositor and adesklets"
date: 2007-06-04
forum: Desktop Effects &amp; Customization
---

### Post by fifafrazer on 2007-06-04
I have a problem with the three programs mentioned in the title. When I enable compositor, to be able to use tranparent windows, the adesklets are looking weird. Take a look at this screenshot:
[http://alcoholic.dk/view.php?id=1951]("http://alcoholic.dk/view.php?id=1951")

The background of the bar is black and is normally transparent, and the background of the weather forecast is totally messed up.. How can i fix that?


I also got another question. How can you make custom keyboard shortcuts in xubuntu, so i can make the windows button useful... Like win + R should start a launcher dialog, win T should start the terminal, win G for Gimp etc.

---

### Post by mrazster on 2007-06-04
About your adesklet, just turn of your composit manager, restart adesklets, turn on your composit manager. You'll most likely encounter this problem everyt time you either reboot computer or restart X.

---

### Post by fifafrazer on 2007-06-06
I've tried to make the sequence automatic at every boot... I've added the following script file to "autostarted applications"
```
#!/bin/bash
killall xfwm4 && xfwm4 --compositor=off &
adesklets --xfce4
killall xfwm4 && xfwm4 --compositor=on &
exit
```

but then the desktop background is black, except for the part of the background which is behind the conky window

---

### Post by holydhaliwal on 2008-02-06
I have this problem aswell on my ubuntu setup, does anyone know how to fix this?

---

