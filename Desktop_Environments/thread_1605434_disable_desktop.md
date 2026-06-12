---
title: "disable desktop?"
date: 2010-10-25
forum: Desktop Environments
---

### Post by LinLou on 2010-10-25
Hello,

I have been trying to disable my desktop and also i have been trying to disable the feature which allows the mounted volumes to appear in the desktop.. so i did this on the terminal..

gconf-editor --> apps --> nautilus --> desktop  and i have disabled the feature for the volumes to be visible.

also i did this..

gconf-editor --> apps --> nautilus --> preferences and i have disabled the show desktop feature.

BUT i can still right click on my desktop and i can still see the mounted volumes on my desktop.

Can some one please tell me if there is another way of disabling my desktop entirely?
Is what i did wrong?


Thank you in advance.

---

### Post by Bobhuber on 2010-10-25
> **LinLou said:**
> Hello,

I have been trying to disable my desktop and also i have been trying to disable the feature which allows the mounted volumes to appear in the desktop.. so i did this on the terminal..

gconf-editor --> apps --> nautilus --> desktop  and i have disabled the feature for the volumes to be visible.

also i did this..

gconf-editor --> apps --> nautilus --> preferences and i have disabled the show desktop feature.

BUT i can still right click on my desktop and i can still see the mounted volumes on my desktop.

Can some one please tell me if there is another way of disabling my desktop entirely?
Is what i did wrong?


Thank you in advance.
Two solutions for the mounted volumes on the desktop. Are you using config editor as root ? This will cause the problem you describe. Install ubuntu tweak which gives you a simple way of disabling this feature along with a whole bunch of other very useful features using a GUI.

---

### Post by sikander3786 on 2010-10-25
Are you using compiz? 

If yes, the easiest solution I can think of is to navigate to

```
System > Preferences > CompizConfig Settings Manager > Utilities > Wallpaper
```

and enable it. Your desktop will disappear and as a bonus, you'll be able to select multiple wallpapers for multiple desktops (if more than 1). ;-)

---

### Post by LinLou on 2010-10-26
just to make clear that what i have firstly posted works on previous versions of ubuntu..

I am not sure if this is a bug or not.. but the solution i am looking for is not by installing another program.. 

thank you though for your help.. 

but is there any other way of disabling desktop and the appearance of volumes on desktop by not installing any other software?

for example is there any other similar way as the one i have firstly posted to disable the desktop?

---

### Post by LinLou on 2010-10-26
no worries.. 

i have fixed it.. it seems that being root caused this problem.. 

i did the same thing as my first post without being being root and it worked..

---

