---
title: "Disable desktop icons??"
date: 2009-10-24
forum: Desktop Environments
---

### Post by LinLou on 2009-10-24
Hey there,

Anyone knows how can i disable the icons on the desktop?

Cheers.

---

### Post by sisco311 on 2009-10-24
Press Alt+F2 and type:
```
gconf-editor
```
Navigate to &#8220;apps > nautilus > preferences&#8221; and on the right-side look for &#8220;show_desktop&#8221;.  Toggling this will toggle, in real-time, the icons from being displayed on your Desktop

---

### Post by LinLou on 2009-10-25
Ok i did that.. but i dont want to actually disable the whole desktop.. i want to disable the icons. I still want to be able to right click on the desktop etc.. Is there any way of doing that?

Thnx

---

### Post by MelDJ on 2009-10-25
how about just removing them by clicking them and pressing delete?

---

### Post by LinLou on 2009-10-25
Smart! but no.. i want to be able to access the "change desktop background" option by right clicking and not from System-->Preferences.

---

### Post by MelDJ on 2009-10-25
i  don't get it. you can remove all your icons and still right click the desktop to change the  desktop background

---

### Post by LinLou on 2009-10-25
I dont want to be able to create folders or put stuff on my desktop. Athough i want to be able to right click in the desktop.. i dont want to disable it completely.. Is this possible?

Thnx

---

### Post by iExist on 2010-01-03
> **sisco311 said:**
> Press Alt+F2 and type:
```
gconf-editor
```Navigate to “apps > nautilus > preferences” and on the right-side look for “show_desktop”.  Toggling this will toggle, in real-time, the icons from being displayed on your Desktop

I just went through the same problem. That just disables everything. Instead though you have to navigate to "apps>nautilus>desktop"

---

