---
title: "How to use the Grid function in 12.04 Gnome Classic-No effects"
date: 2013-04-12
forum: Desktop Environments
---

### Post by Albatrossed on 2013-04-12
[COLOR=#333333][FONT=Ubuntu Beta]I'm using 12.04, Gnome Classic - No effects, because it is the one that best seems to work with my somewhat old laptop. 

Now, is there a way to use the Grid function? I've gone thru CompizConfig, but no matter what combination of keys I set, it does nothing. I guess my Compiz is not managing my windows. How can I tell If I'm using Metacity? And if this was the case, How can I set the grid function with it? Both keyboard and mouse drag&drop would be awesome. In fact, I loved those in Unity 3D, and I'm missing them quite a lot![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Also, I find that I can't seem to be able to run Gnome-classic (with effects). When I try to log in in this mode, It seems to be starting as Unity 2D.

Thanks!! [/FONT][/COLOR]

---

### Post by stinkeye on 2013-04-12
> **Albatrossed said:**
> [COLOR=#333333][FONT=Ubuntu Beta]I'm using 12.04, Gnome Classic - No effects, because it is the one that best seems to work with my somewhat old laptop. 

Now, is there a way to use the Grid function? I've gone thru CompizConfig, but no matter what combination of keys I set, it does nothing. I guess my Compiz is not managing my windows. How can I tell If I'm using Metacity? And if this was the case, How can I set the grid function with it? Both keyboard and mouse drag&drop would be awesome. In fact, I loved those in Unity 3D, and I'm missing them quite a lot![/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Beta]Also, I find that I can't seem to be able to run Gnome-classic (with effects). When I try to log in in this mode, It seems to be starting as Unity 2D.

Thanks!! [/FONT][/COLOR]
The Gnome Classic - No effects session uses metacity.
If you want to use the grid, login to the Gnome Classic session which uses compiz.

Check what window manager your using...
```
sudo apt-get install wmctrl
```

Then...
```
wmctrl -m
```

You may need to install a proprietary driver to run compiz depending on your gfx card.

---

### Post by ibjsb4 on 2013-04-12
Is the grid function another name for wireframe feature?  If so in metacity it still in gconf-editor under reduced_resources.

[ATTACH=CONFIG]241268[/ATTACH]

---

