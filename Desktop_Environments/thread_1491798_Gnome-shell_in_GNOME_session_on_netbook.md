---
title: "Gnome-shell in GNOME session on netbook"
date: 2010-05-24
forum: Desktop Environments
---

### Post by djmoore85 on 2010-05-24
hey yall, just got an idea to play around with using gnome-shell in a GNOME session on a netbook. I thought it might be a good interface to use on the small screen, and I am hoping to be able to take advantage of having multiple workspaces in one area. But anyway, here is output of some errors I am getting:

```
daniel@daniel-laptop:~$ gnome-shell --replace
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.

(mutter:1743): Clutter-WARNING **: The actor 'BigBox' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:1743): Clutter-WARNING **: The actor 'searchEntry' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:1743): Clutter-WARNING **: The actor 'BigBox' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:1743): Clutter-WARNING **: The actor 'dash' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:1743): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended

(mutter:1743): Clutter-WARNING **: The actor 'ClutterGroup' is currently inside an allocation cycle; calling clutter_actor_queue_relayout() is not recommended
Window manager warning: Log level 16: IA__g_object_set_valist: construct property "type" for object `ShellEmbeddedWindow' can't be set after construction
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!
```

Any ideas on getting gnome-shell running smoothly?

---

### Post by PGScooter on 2010-05-30
This is for the ubuntu netbook edition (you mentioned you're "on a netbook" but do you also mean that you're using the netbook edition?)

Can you run compiz?

---

### Post by djmoore85 on 2010-05-31
It is on a UNR install, but I am playing around with it in a GNOME session. For now I just have the gnome replace command on a launcher, because I believe if I edit my startup programs to include that command it will spill over into my regularly used UNR edition sessions

---

### Post by dleonov on 2010-07-16
Commenting out the following lines in /etc/X11/xorg.conf helped me with the similar problem:

Section "DRI"
       Mode    0666
EndSection

---

### Post by KdotJ on 2010-07-16
Possibly due to conflicts of libraries and/or versions? UNR uses clutter and gnome-shell uses mutter (a mix of clutter and metacity). I had errors too when trying out gnome-shell on my netbook

---

