---
title: "gDesklet starter icons"
date: 2006-09-16
forum: Desktop Environments
---

### Post by eeefresh on 2006-09-16
I've installed the starter gDesklet and added several programs to it. However, when I go to add an icon, a few of them. like Open Office Writer and Open Office Calc, don't have icons in /usr/share/pixmaps/.

Also, I have a starter for amaroK 1.3, but the amaroK icons in /usr/share/pixmaps/ are weird-looking...badly pixelated CD icons instead of the more attractive howling wolf icon. AQnybody know why that is, or how I can use the wolf icon? I tried copying the .png from their Web site, but when I browse to it from within starter, it won't let me select it. Apparently everything but /usr/share/pixmaps/ is off limits???

Any help would be appreciated.

---

### Post by ayoli on 2006-09-16
have a look under /usr/share/icons
if you dont find any cool icons there download a theme at gnome-look.org
and extract it into ~/.icons

---

### Post by eeefresh on 2006-09-16
Well I see several under user/share/icons/hicolor, including the ones I need.  But I am still having a problem selecting them from within starter.  When I go to "edit starter" it as an option to add an icon.  By  default it loads /usr/share/pixmaps, but there is a "browse" button.  However, when I browse to another folder, all of the files are greyed out and can't be selected.  Any idea why?

---

### Post by UltraMathMan on 2006-09-16
No idea, I just copy icons into /usr/share/pixmaps from the terminal when I want to use them.

P.S. - If you're looking for icons check out [http://customxp.net/images/PngFactory/](http://customxp.net/images/PngFactory/)

---

### Post by ayoli on 2006-09-16
> **eeefresh said:**
> Well I see several under user/share/icons/hicolor, including the ones I need.  But I am still having a problem selecting them from within starter.  When I go to "edit starter" it as an option to add an icon.  By  default it loads /usr/share/pixmaps, but there is a "browse" button.  However, when I browse to another folder, all of the files are greyed out and can't be selected.  Any idea why?

use the browse button to select a folder where the icons are, then you will see the icons in the window

---

### Post by eeefresh on 2006-09-16
> **UltraMathMan said:**
> No idea, I just copy icons into /usr/share/pixmaps from the terminal when I want to use them.

P.S. - If you're looking for icons check out [http://customxp.net/images/PngFactory/](http://customxp.net/images/PngFactory/)

Already tried that.  It says I don't have permission to write to the folder.

---

### Post by orb9220 on 2006-09-16
Are you using a gksudo nautilus it is required to write into system folders.

---

### Post by eeefresh on 2006-09-16
> **ayoli said:**
> use the browse button to select a folder where the icons are, then you will see the icons in the window

That's what I have been trying to do, but it will only let me select what's in the user/share/pixmaps folder.  When I navigate to another folder,  I can see the files but can't select them.  They are greyed out.

---

### Post by eeefresh on 2006-09-16
> **orb9220 said:**
> Are you using a gksudo nautilus it is required to write into system folders.

I'm logged into my normal account.  What do I have to do to use gksudo?

---

### Post by ayoli on 2006-09-16
> **eeefresh said:**
> I'm logged into my normal account.  What do I have to do to use gksudo?

hit ALT+F2 wil prompt run dialog, type in: gksudo nautilus
then you will be prompted for your user password and nautilus will open with root rights.
btw, why don't you copy them in ~/.icons like i said above, then in your icon selector enter this path and hit enter, then you will see the icons

---

### Post by eeefresh on 2006-09-16
Okay, that worked.

Thanks guys!  Ayoili - That's two you've helped me with today! Much appreciated!

---

