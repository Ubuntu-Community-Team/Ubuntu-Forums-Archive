---
title: "Using Gnome-Shell themes for Unity possible?"
date: 2012-06-14
forum: Desktop Environments
---

### Post by jasonwyz98 on 2012-06-14
I'd like to install some themes made for Gnome-Shell, like to know if they will work on Unity as well?

---

### Post by Frogs Hair on 2012-06-14
I don't think it will work because the Gnome shell uses a different window manager. As you know shell themes aren't displayed in advanced settings while Unity is being used.

---

### Post by 3Miro on 2012-06-14
Unity uses GTK3 + Metacity windows decorations. You can use any GTK3 theme with Unity and you should be able to use at least most Metacity themes. Install Ubuntu-Tweak to gain more control over the themes.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by jasonwyz98 on 2012-06-14
> **Frogs Hair said:**
> I don't think it will work because the Gnome shell uses a different window manager. As you know shell themes aren't displayed in advanced settings while Unity is being used.

So I were to install a theme made for Gnome 3, and then log into Unity, which theme will be used?

---

### Post by jasonwyz98 on 2012-06-14
> **3Miro said:**
> Unity uses GTK3 + Metacity windows decorations. You can use any GTK3 theme with Unity and you should be able to use at least most Metacity themes. Install Ubuntu-Tweak to gain more control over the themes.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Just curious, have you actually tried this? I'm at work unable to try it now

---

### Post by 3Miro on 2012-06-14
> **jasonwyz98 said:**
> Just curious, have you actually tried this? I'm at work unable to try it now

I don't think I have tried the Metacity decoration themes, however, I have tried the GTK3 themes and those work well. Ubuntu Tweak does provide an option to adjust the Unity decoration theme, but I can't remember if I have used it.

BTW if you install a Gnome 3 theme, it will not show immediately. If you install and set a Gnome 3 theme from Gnome-shell, then at least the GTK3 part should work under Unity. I don't think setting the them in Gnome-shell will affect Unity.

---

### Post by diesch on 2012-06-14
Using Metracity themes works at least with MyUnity and Unsettings, I guess Ubuntu-Tweak can use them, too.

---

### Post by zombifier25 on 2012-06-15
There are some confusion here. GTK themes change the look of windows, except for windows decoration (the titlebar). Metacity themes change windows decoration. GNOME Shell themes change the look of GNOME Shell itself.

If the themes explicitly said that it's a GTK theme, then it can be used in both GNOME Shell and Unity. If it's a GNOME Shell them, then it only changes the look and feel of GNOME Shell, so it cannot be used in Unity.

---

### Post by Frogs Hair on 2012-06-15
> **jasonwyz98 said:**
> So I were to install a theme made for Gnome 3, and then log into Unity, which theme will be used?

The GTK 3 theme will work but not the Gnome shell theme.

---

### Post by Frogs Hair on 2012-06-15
Advanced settings in Unity. Notice that the Gnome S hell theme is not displayed even though the theme Gnomish Beige includes one .

---

