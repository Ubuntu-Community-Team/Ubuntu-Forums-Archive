---
title: "Openbox changing themes doesn't work"
date: 2011-10-31
forum: Desktop Environments
---

### Post by micdhack on 2011-10-31
In the old days where ubuntu had gnome as its basic component changing themes with lxappearance for openbox it was a piece of cake.
Problem is that since the upgrade it doesn't work. The default ambience theme of unity is always on and i have no idea what service causes this.

Does anyone know how i can change themes(theme,icons etc) in openbox? What service do i have to disable that create the default theme of unity in openbox?

---

### Post by mcduck on 2011-10-31
Are the applications you use using GTK2 or GTK3, and which type of theme you try to use?

Most of the Gnome applications would now be using GTK3. And it's more than likely that LXAppearance still only change GTK2 theme...

Anyway, at the moment it's a good idea to try to use themes that include both GTK2 and GTK3 theme.

(by the way Ubuntu still has Gnome as it's default desktop environment. It simply has moved to Gnome 3, and uses a different shell on top of the Gnome desktop than what's used by default. But the desktop environment definitely is still Gnome)

---

### Post by micdhack on 2011-11-04
I had no idea that it might be a problem of gtk3. 
Do you know of any programs that can change themes for gtk3?

---

### Post by mcduck on 2011-11-04
Gnome-tweak-tool, although I have no idea how it would behave with Openbox setup.

I also found a guide that suggested creating a *settings.ini* file in *~/.config/gtk-3.0/* and using the following code there to set the GTK3 theme:
```

[Settings]
gtk-application-prefer-dark-theme = true
gtk-theme-name = Adwaita
gtk-fallback-icon-theme = gnome
```

---

### Post by micdhack on 2011-11-04
gtk-3.0 was missing from config

It seems that the best way is install the package gnome-theme-standard and then
move the folder "/usr/share/themes/Adwaita/gtk-3.0" to ~/.config/

Then with gtk-chtheme or lxappearance you can change the settings

---

### Post by micdhack on 2011-11-05
If you want uniformity between apps that use gtk 2.0 and gtk 3.0 then gnome-tweak-tool would be the best for changing themes.

you have to change two options for the themes and set them both for Adwaita.

There are other alternative themes that you could use also:
[https://wiki.archlinux.org/index.php/GTK%2B#GTK.2B_3.x](https://wiki.archlinux.org/index.php/GTK%2B#GTK.2B_3.x)

---

