---
title: "help with Gnome themes"
date: 2009-02-26
forum: General Help
---

### Post by 37fleetwood on 2009-02-26
I'm sorry if this has been asked before but whenever I do a search I get like 30 pages and never seem to be able to find what I'm looking for.
the question I have is this. when I install a theme through Gnome-Art and then try to adjust things through Appearance Preferences, I get this message:
This theme will not look as intended because the required GTK+ theme engine is not installed.
how do I know which one to install? or will it hurt anything if I just install them all? the FAQ at art.Gnome.org isn't too helpfull.
thanks
Scott;)

---

### Post by Ms_Angel_D on 2009-02-26
What theme engine does it tell you to look for?

---

### Post by nemomarlin on 2009-02-26
this website has 60 good selections of gnome themes.
[http://www.anewmorning.com/2008/12/29/60-best-ubuntu-themes/](http://www.anewmorning.com/2008/12/29/60-best-ubuntu-themes/)

Not included in the list but good themes are nimbus(not nimbus vista look), nimbus is one of the most professional themes done by Sun. and Dust theme is also excellent. Search them on gnome-look.org

I've tried many many themes but now I decide that the default human theme is the best. :P

---

### Post by mcduck on 2009-02-26
If the error message doesn't tell what engine its missing, you can just ignore the error. The theme will still work correctly.

It's an issue with the common practice of using empty engine definitions in theme configuration files when the theme creator doesn't want to apply any theming to some part. Gnome's theme manager doesn't quite understand this and as a result produces that error message.

Of course, when the error actually tells what engine it's missing, you should install that engine.

edit: It's also possible to go through the theme's gtkrc file and change every instance of *engine ""* into *engine "pixmap"* which would work in a similar way without confusing the theme manager, but as this makes no difference to how the theme looks/works and is quite a lot of work to do for all your themes I don't think it's worth doing.

---

