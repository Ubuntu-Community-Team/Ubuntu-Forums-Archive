---
title: "Error activating XKB configuration after installing XGL and Compiz"
date: 2006-07-18
forum: Desktop Environments
---

### Post by turok on 2006-07-18
Hi, i've succesfully installed XGL+Compiz on my computer and everything works great, exept my keyborad. After installing it and the latest nvidia drivers i changed my keyboard configuration. And now when i log in using either xgl or metacity i get the following error message:


Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
70000000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd

---------------------------------------------------
xprop -root | grep XKB says:
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "latam", "latam", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "latam", "latam", ""
---------------------------------------------------
gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd says:
 layouts = [latam,la    la,gb   dvorak]
 model = pc104
 options = [grp grp:alts_toggle]
 overrideSettings = true


I would like to know, first of all how to get to use my latin american keyboard (latam), becouse i select it from gnome's keyboard preferences and nothing happens, i continue using the us layout isntead of the latam one.
And secondly i would like to know what does that error message mean and how can i solve it.
 
Thanks a lot

---

### Post by turok on 2006-07-20
Well, i've been trying to solve this and when i start with my normal gnome session with metacity and everything default it automaticaly loads the Latin American Keyboard layout as i want it to. But when i use Xgl it loads the US keyboard layout, how can i solve this ?.
Btw: the error code when i start session keeps apearing, what should i do ?
Thanks a lot.

---

### Post by goobers on 2006-07-20
When you load XGL and compiz, do you do it with a script? if so can you post them here? i think you have to specify the keyboard layout in the script as xgl/compiz alters it

---

### Post by turok on 2006-07-20
Hi, thanks for your reply.
I followed this guide: 
[http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29](http://doc.gwos.org/index.php/Swich_between_XGl_and_Xorg_through_GDM_%28or_KDM%29)


So my script to start XGL is the following one:

xmodmap /usr/share/xmodmap/xmodmap.us
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
exec gnome-session

i havent seen this line :P
xmodmap /usr/share/xmodmap/xmodmap.us
i will try to change it and i'll tell you. Thanks.
Do you know how can i solve the error message i get when i log in ?
Thanks a lot.

---

### Post by dsmarsh on 2006-09-03
I get the exact same message when i log into ubuntu.
It just an annoyance, but it would be cool if it were gone.
I have a T42, with an ATI 9600 running ubuntu and compiz.
Kinda new to all of this.
Any help getting rid of that.



Also since i have tryed this compiz i was trying to use    xwinwrap, but this doesnt work either and i couldnt find anyone who knew how to fix it.
When i start it my whole session just restarts and the xwinwrap doesnt come on with movies or screensavers.


Thanks ahead for any help :-)](*,)

---

### Post by dsmarsh on 2006-09-11
bump

---

