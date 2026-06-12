---
title: "converting xubuntu to ubuntu (completely)"
date: 2014-12-19
forum: Desktop Environments
---

### Post by John Phang on 2014-12-19
hi there, currently im using xubuntu 14.10 and i've install ubuntu unity in it. is there anyway that i could set ubuntu as my default desktop environment by replacing the lock screen and splash screen completely? your reply will be a great help to me. thanks in advance :)

---

### Post by carlwsnyder on 2014-12-19
My experience is that if you want to install standard Unity Ubuntu starting from Xubuntu, re-install from installation media, or, vice versa, to go from Ubuntu to Xubuntu without any lingering settings which are from the previous desktop.  Otherwise there is going to be something which lingers on from the original installation.

---

### Post by fantab on 2014-12-20
If you like Ubuntu-unity, then the best will be to re-install ubuntu.

To make unity as default you will have to tweak lightdm, see the following quote from ubuntuwiki:
[QUOTE=Ubuntu Wiki/LightDM]**Changing the Default Session**

 The default session is set by configuration in **/usr/share/lightdm/lightdm.conf.d/** that session packages provide. If you need to override this you can set: 
[SeatDefaults]
user-session=name
Where **name** is the name of the session .desktop file from **/usr/share/xsessions/*.desktop**. 
[/QUOTE]

---

