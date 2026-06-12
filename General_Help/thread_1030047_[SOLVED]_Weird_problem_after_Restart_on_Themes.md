---
title: "[SOLVED] Weird problem after Restart on Themes"
date: 2009-01-04
forum: General Help
---

### Post by sendblink23 on 2009-01-04
This occured after I restarted (I recently installed Emerald, and all working perfectly)

Really weird Afterwards (Restart)... no themes, even the original one's inside of Ubuntu 8.10 .. the Window's Top Border won't change.. it simply changed to a RED diffrent one.. that I do not have.

Yes I tried changing to all Themes I have.. and still the Top of all windows, look the same.. here is the Print Screen, showing with a *THEME Marked (that is suppose to have)

[IMG]http://i29.photobucket.com/albums/c272/sendblink23/WeirdWindowsBorder.png[/IMG]

Can anybody help me out???
I'm on Ubuntu 8.10

---

### Post by the yawner on 2009-01-04
Well since you installed emerald, it has now taken over the job of drawing your window decorations. That red things is the default emerald theme. There are two options for you now. 

- You could change your emerald theme to one that would suit your requirements. Gnome-look has some themes.
- You could revert to using gtk-window-decorator which is what Compiz uses to maintain your preferred metacity theme.

To see for yourself, try the following commands either on a terminal or via Alt+F2:

To switch to gtk window decorator
```
gtk-window-decorator --replace
```

To switch to emerald
```
emerald --replace
```

---

### Post by gettinoriginal on 2009-01-04
i would also like to recommend installing Compiz Fusion Icon (it's in Synaptic), as it lets you choose your "window decorator" (emerald or gtk) and your window manager (compiz or metacity) on the fly.

---

### Post by sendblink23 on 2009-01-04
> **the yawner said:**
> Well since you installed emerald, it has now taken over the job of drawing your window decorations. That red things is the default emerald theme. There are two options for you now. 

- You could change your emerald theme to one that would suit your requirements. Gnome-look has some themes.
- You could revert to using gtk-window-decorator which is what Compiz uses to maintain your preferred metacity theme.

To see for yourself, try the following commands either on a terminal or via Alt+F2:

To switch to gtk window decorator
```
gtk-window-decorator --replace
```

To switch to emerald
```
emerald --replace
```




Yes that worked... I noticed i have the command for Emerald to Start automaticly on Startup *I unchecked it so that doesn't occur again.


Well anyways...  One question I erased... the theme I added in the Gnome themes (the only one I've installed) ..  now trying to install it again.. but it gives me an error
"Can't move directory over directory"

Its really weird I just erased it.. and well I'm trying to install it again.. why does it say that?

Also where are all Default themes installed in the computer at?

---

### Post by the yawner on 2009-01-04
Hmm... On your home folder, view the hidden folders by pressing Ctrl+H and look for the folder .themes. That's where the themes you installed via the Appearance settings are saved. Try deleting the folder Dark Purple (if that's the theme having problems) and install the theme again via Appearance settings.

For added info, the default themes can be found in /usr/share/themes.

---

### Post by sendblink23 on 2009-01-04
> **the yawner said:**
> Hmm... On your home folder, view the hidden folders by pressing Ctrl+H and look for the folder .themes. That's where the themes you installed via the Appearance settings are saved. Try deleting the folder Dark Purple (if that's the theme having problems) and install the theme again via Appearance settings.

For added info, the default themes can be found in /usr/share/themes.

Yup yup! =)

Thanks a bunch that worked.

---

### Post by the yawner on 2009-01-04
You're welcome. :)

---

