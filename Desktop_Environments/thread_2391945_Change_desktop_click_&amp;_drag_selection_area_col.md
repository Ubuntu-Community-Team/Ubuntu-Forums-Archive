---
title: "Change desktop click &amp; drag selection area color"
date: 2018-05-15
forum: Desktop Environments
---

### Post by maceaferrer on 2018-05-15
I'm building a custom Lubuntu enviroment and I've been trying to change the color of the selection area in desktop:
[ATTACH=CONFIG]279699[/ATTACH]

I have looked in a lot of directories, al ready tried using dconf to edit the gtk color scheme in /org/destkop/gnome/interface (I might wrote that wrong, but the point is I already tried dconf)

If anyone knows where are the config files, a guide or anykind of directions, I will truly apreciate it.

---

### Post by kerry_s on 2018-05-15
the click drag is transparent, so the color you see depends on the background/wallpaper. is it different in lubuntu?

---

### Post by kazakore on 2018-05-16
I can't find for definite whether LXDE is using GTK2 or GTK3. GTK2 is a lot easier to edit (or at least I've started to understand it in the last week) and I would expect it to be from one of these three in the main Engine and I would probably change and test them in this order if I was trying to change it myself. Obviously it will also change selections in all other GTK2 programs.

    base[SELECTED] 

    fg[SELECTED]

    bg[SELECTED]


If it uses GTK3 that is currently beyond what I've played with and the only theme I've look at uses a script to regenerate the related from from .scss file containing colours etc. Still have to research that further myself....

---

### Post by maceaferrer on 2018-05-17
> **kerry_s said:**
> the click drag is transparent, so the color you see depends on the background/wallpaper. is it different in lubuntu? AFAIK, they might but not that much. My issue is that I haven't found any config file that actually changes the color.

---

### Post by maceaferrer on 2018-05-17
I will give it a try in a few hours and come back with results.

---

### Post by maceaferrer on 2018-05-21
Ok, I manage to change everything but the very thing I'm trying to. Sorry for replying until today; besides messing up my sleep patterns, it's been a really busy week.

---

