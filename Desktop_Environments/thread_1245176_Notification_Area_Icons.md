---
title: "Notification Area Icons"
date: 2009-08-20
forum: Desktop Environments
---

### Post by magnumstyle007 on 2009-08-20
Where are those stored? 
I installed a new theme and want to replace the battery charge monitor icons, but I cannot find them. 

Thanks in advance

---

### Post by magnumstyle007 on 2009-08-20
Anyone please? It drives me crazy, i looked into pixmaps, share and lib folders, didn`t find anything. Also, Volume and Brightness control adapted the new icons as soon as i got the new theme installed.
Please help

---

### Post by gamerchick02 on 2009-08-20
For the battery, go to System-Preferences-Power Management.

The window that opens will be the Power Management Options.

Click on the "General" tab, and where it says "Notification Area" pick the "Always display this icon" option.

That should show your battery in the notification area.

The icons should show up in the new icon theme you installed.

Amy

EDIT: Sometimes the theme doesn't have a specific icon for your app.  In that case, it will go back to the default Gnome/Ubuntu one.

---

### Post by magnumstyle007 on 2009-08-20
Thank you, that does the trick.

However, that is the power monitor, while I was looking for the battery charge monitor. I just removed it now, so I m happy. But it is still a mystery to me where the icons (of the bcm) are stored.

Thank you for your fast help!

---

### Post by londonali1010 on 2009-08-20
A slightly different solution to a similar problem...If you install a new theme, if there are any programs (such as the battery or wifi) that it doesn't recognise, it will default to (IMHO) an icky Gnome one...If you want to change that, you can edit "index.theme" in /usr/share/icons/<whatever icon theme you're using>.  In there, there's an "inherit" line, which can point to whatever other theme you want.  For instance, I typically use gnome-wise icons, set to inherit Human, because I like the Human battery icon better than the Gnome default.

HTH.

---

### Post by r5r4y on 2009-08-20
you can also do it manually if you have problems editing index.theme...

those icons stored in /usr/share/pixamps [not all but most i think]

---

### Post by gamerchick02 on 2009-08-20
I thought they were one in the same...

Either way, londonali1010 has some good advice there.

Amy

---

