---
title: "Can't Change Window Borders/Colors"
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by strik9 on 2008-01-29
i recently downloaded and installed the KDE desktop enviroment and it screwed some things up so i removed it but now i cannot change the window borders or the colors. if i turn off compiz desktop effects it returns the window border back to normal. when i turn effects back on it reverts to the red color and wont let me change it.  maybe this is just a simple setting change in compiz i dont know. if you know what to do and can help it would be greatly appreciated. 

heres a screenshot:

---

### Post by Tenken on 2008-01-29
To change the red boarder you need to install emerald window/theme manager, and install some themes (from [gnome-look ]("http://www.gnome-look.org")for example)

```
sudo apt-get install emerald
```

to get your boarders back with out using compiz effects try this in a terminal

```
metacity --replace &
```

---

### Post by strik9 on 2008-01-29
> **Tenken said:**
> To change the red boarder you need to install emerald window/theme manager, and install some themes (from [gnome-look ]("http://www.gnome-look.org")for example)

```
sudo apt-get install emerald
```

to get your boarders back with out using compiz effects try this in a terminal

```
metacity --replace &
```

ok i tried installing emerald but i already have it so that doesnt change anything.
i think thats where i got my current theme/window border from in the first place.
its fine when desktop effects isnt enabled, and it was fine before i installed KDE 
but even after i removed KDE it remained and it wont let me change it.
neither one of these does any good. im not sure what the problem is.

---

### Post by Tenken on 2008-01-29
[QUOTE=strik9]i think thats where i got my current theme/window border from in the first place.[/QUOTE]

You have emerald installed, did you try using a different theme from System->Preferences->Emerald Theme manager? That red board is the default used when no other emerald themes are installed, and can't be changed through Gnome Appearances.

---

### Post by strik9 on 2008-01-29
> **Tenken said:**
> You have emerald installed, did you try using a different theme from System->Preferences->Emerald Theme manager? That red board is the default used when no other emerald themes are installed, and can't be changed through Gnome Appearances.

you know ... i never even thought of checking those settings. now i feel dumb.
not my original border but will do. definitely better than the red. THANKS!

---

### Post by Tenken on 2008-01-30
If you're looking for some more emerald themes you can find some nice ones at [gnome-look.org ]("http://www.gnome-look.org")or [compiz-themes.org]("http://compiz-themes.org").

---

### Post by strik9 on 2008-01-30
> **Tenken said:**
> If you're looking for some more emerald themes you can find some nice ones at [gnome-look.org ]("http://www.gnome-look.org")or [compiz-themes.org]("http://compiz-themes.org").

im glad you just read my mind i just went to search how to download extra themes and this showed up as the first thread lol. i really appreciate all of your help!

---

