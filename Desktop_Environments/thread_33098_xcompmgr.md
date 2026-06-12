---
title: "xcompmgr"
date: 2005-05-09
forum: Desktop Environments
---

### Post by kestasjk on 2005-05-09
xcompmgr looks great, but has just one annoying quirk which stops me from being able to use it in GNOME 2.10: metacity windows go over the top and bottom panels, and when you maximize a window it is maximized over the top and bottom panels. Is there any way around this? Thanks again,
Kestas.

---

### Post by okenobu on 2005-05-09
I seem to remember this problem was fixed by putting xcompmgr in your gnome-session so it starts up before the panel. Run gnome-session-properties from the menu and add 'xcompmgr' to 'startup programs' with priority 0 and it should do the trick. If that still doesnt work, find your way through the thread in the hoary customization forum ;)

---

### Post by Fab on 2005-05-11
[QUOTE=kestasjk]xcompmgr looks great, but has just one annoying quirk which stops me from being able to use it in GNOME 2.10: metacity windows go over the top and bottom panels, and when you maximize a window it is maximized over the top and bottom panels. Is there any way around this? Thanks again,
Kestas.[/QUOTE]
 -C after the -c switch

---

### Post by deception on 2005-05-11
Had this issue when I first loaded xcompmgr, i did "killall gnome-panel" which restarted it and things have been peachy since then. 

Also set xcompmgr -c to run at position 40 in gnome sessions manager.

HTH  :)

---

### Post by Nico65 on 2005-05-30
hello

if you want to put xcompgrm ON and OFF on the fly with gnome open, "skill gnome-panel" is a solution but "metacity-message restart" do the job and is much, much faster ;-)  

I have a (small) problem however, with xcompmgr ON, if I do System/Close Session, gnome hangs :-x I have to turn xcompmgr OFF before doing so. I could live with that, but...

---

### Post by Beer on 2005-06-14
You guys should try this, I hear it works well.

[http://sourceforge.net/projects/gcompmgr/](http://sourceforge.net/projects/gcompmgr/)

---

