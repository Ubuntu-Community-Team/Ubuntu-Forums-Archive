---
title: "Gnome themes don't seem to install"
date: 2009-08-02
forum: Desktop Environments
---

### Post by random turnip on 2009-08-02
I've been downloading themes from Gnome-look, dragging and dropping them from the desktop to the theme manager window, and nothing happens, the theme doesn't appear in the list and the .tar.gz file is still on the desktop.  I haven't been unzipping them or anything, just downloading, and drag & dropping.
Any ideas?


[edit]
I just tried a different theme and it said that it wasn't a valid theme.

---

### Post by Excedio on 2009-08-02
> **random turnip said:**
> I've been downloading themes from Gnome-look, dragging and dropping them from the desktop to the theme manager window, and nothing happens, the theme doesn't appear in the list and the .tar.gz file is still on the desktop. I haven't been unzipping them or anything, just downloading, and drag & dropping.
Any ideas?
 
 
[edit]
I just tried a different theme and it said that it wasn't a valid theme.
 
Themes don't usually apply themselves automatically. Are you clicking on the theme after dropping it into the Theme Manager?

---

### Post by random turnip on 2009-08-02
No, there was nothing to click, it still wasnt in the list.

---

### Post by sasho_zl on 2009-08-02
What kind of themes? You can download Beryl - Emerald themes and install them with the Emerald Theme Manager. Just dont forget to add the **emerald --replace** command to your startup scripts.

---

### Post by Buce on 2009-08-02
You could install them manually. First, you have to extract the package, then move the folder to ~/.themes. Then, edit ~/.gtkrc-2.0 so that it has this line:

```
include "/home/woody/.themes/Theme_Name/gtk-2.0/gtkrc"
```

Don't forget to change "Theme_Name" to the appropriate thing, and make sure that the gtkrc file referenced actually exists.

---

### Post by random turnip on 2009-09-29
> **Buce said:**
> You could install them manually. First, you have to extract the package, then move the folder to ~/.themes. Then, edit ~/.gtkrc-2.0 so that it has this line:

```
include "/home/woody/.themes/Theme_Name/gtk-2.0/gtkrc"
```

Don't forget to change "Theme_Name" to the appropriate thing, and make sure that the gtkrc file referenced actually exists.

Ah, that sounds like it would work.
Only one thing i don't get, what do you mean by editing "*~/.gtkrc-2.0*"?
And how do i do that?

---

### Post by VCoolio on 2009-09-29
~ is short for /home/<user>, so that's your home folder. .gtkrc-2.0 is a hidden file in which you can define what themes should be used. It looks eg. like this:

gtk-theme-name="ElegantDev"
gtk-icon-theme-name="LaGaDesk-BlueNight"
gtk-font-name="Verdana 10"

I doubt though that it's where appearance manager stores it's settings. Just extract gtk and metacity themes to ~/.themes and icons to ~/.icons and they should show up in the theme list, at least when you press configure and look in controls (for gtk).
Extracting to .themes and .icons is the same as 'install' themes does. 

If your theme still doesn't show up post a link here.

---

### Post by ~sHyLoCk~ on 2009-09-29
Most of the times you will find window themes or control themes as well, only complete theme package [like crux,human, etc] show up in the theme tab. So customize and see if you find the themes.

---

