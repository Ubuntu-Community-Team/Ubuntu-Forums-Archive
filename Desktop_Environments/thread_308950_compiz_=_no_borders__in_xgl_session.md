---
title: "compiz = no borders  in xgl session"
date: 2006-11-28
forum: Desktop Environments
---

### Post by dracule on 2006-11-28
I installed compiz added the line that everyone says to add in your xorg.conf, followed a wiki on how to get xgl up and running, booted into an xgl session now I run compiz without errors but still cant get a window manager... I also can run beryl-manager and have all my effects(rotating cube, and other stuff) but dont have a window border ](*,)

---

### Post by dracule on 2006-11-29
I now I found compiz-freedesktop for 64bit and replaced compiz with it, now when i do "compiz-tray-icon" it gives me this huge list of plugins which arent installed, and i cant find anywhere where it tells to install these plugins or how.

this crashes my system: gnome-window-decorator & compiz --replace --use-cow gconf


by the way, im using nvidia drivers on 64 bit edgy.

---

### Post by dracule on 2006-11-29
Im still having no luck with this,.. if anyone can help please please help me.

---

### Post by wieman01 on 2006-11-29
I have the same problem... Initially I thought this had to do with the "baghira" add-on. But your posts makes me think it does not. You don't run "baghira" (window manager) by chance?

---

### Post by dracule on 2006-11-29
i dont run that

---

### Post by RAOF on 2006-11-30
> **dracule said:**
> I now I found compiz-freedesktop for 64bit and replaced compiz with it, now when i do "compiz-tray-icon" it gives me this huge list of plugins which arent installed, and i cant find anywhere where it tells to install these plugins or how.

this crashes my system: gnome-window-decorator & compiz --replace --use-cow gconf


by the way, im using nvidia drivers on 64 bit edgy.

1) Have you installed the compiz-freedesktop-gnome package?  Where did you get the compiz-freedesktop packages?

2) gnome-window-decorator is now called **gtk**-window-decorator.

3) Do you have any plugins in your ~/.compiz directory?  They may be confusing matters.

---

### Post by dracule on 2006-11-30
1) yes i have the compiz-freedesktop-gnome package taken from a falcon repository (i think it may have been yours)
2)alright
3)Ill have to check but im pretty sure I dont, ill check in a couple of minutes (in XP)

---

### Post by shanepardue on 2006-12-07
I am having the same problem. XGL, Edgy, and Compiz aren't working well together. Any updates on this situation?

---

