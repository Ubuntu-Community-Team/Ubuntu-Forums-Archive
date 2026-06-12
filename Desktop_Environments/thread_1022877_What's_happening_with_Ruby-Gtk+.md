---
title: "What's happening with Ruby-Gtk+?"
date: 2008-12-27
forum: Desktop Environments
---

### Post by ubix on 2008-12-27
In June I have started to play with {{ Ruby Gtk+ }} on Ubuntu Hardy. It was not too hard to install required pieces of software and libraries. After downloading the {{ ruby-gnome2-0.17.0-rc1 }} the README file helped me enough, to get it done in less than a few hours. The first order of business  was to figure out that you needed Ruby1.9 for installation to work, otherwise the first installation command {{ ruby extconf.rb }} would fail. But a more challenging task was to find out why the {{ gtk2 }} library didn't get created. I discovered a rather dubious program error in {{ gtk/src/rbgtkbuilder.c }}. I was almost certain that by fixing the problem something else will be broken. However, to my surprise my {{ helloworld.rb }} worked. Throughout my first few Ruby Gtk+ lessons all was well. It was only when I started to use the glade that things got a bit harry. However, a rather elaborate example from the web tutorial worked flawlessly, and I believed the next release will most likely fix most of the problems. Of course I was eager to see the  {{ gtk/src/rbgtkbuilder.c }} bug do be squashed. But things got worse half a year later, after for an unrelated problem elsewhere I had to reinstall my OS. Of course I lost all my Ruby setups and additional instalations in the process and by the time I got around to reinstall it all again, a new release of ruby-gnome2 {{ 0.18.1 }} became available. In the meantime, while investigating different options to implement "Rapid Development Techniques", I have also learnt about some disturbing facts in the areas related to Ruby GUI, in particular in the area of "canvas" which happens to be of particular interest to my projects. I often encountered statements like the following:

> 
Time has passed by and DiaCanvas has had it's time in place. Current development on GTK+ (mainly the integration of the Cairo library and the deprecation of the GnomeCanvas library) has made this library quite out-of-date. For most people this library has become an installation nightmare.

Gaphor, the foremost application that uses DiaCanvas, has abandoned this library in favor of it's own, Python based,library. Libraries like goocanvas and crcanvas have taken the place of DiaCanvas.

([http://diacanvas.sourceforge.net/](http://diacanvas.sourceforge.net/))


Indeed, I was eager to learn more from the GNOME and Gtk+ sources about these issues, however, not very much or better, next to nothing, is available for general public on the Internet. As I already mentioned, my expectations that the new Ruby-GNOME2 release would be better were dashed after I installed the last  {{ ruby-gnome2-all-0.18.1 }}. Not only did the previous {{ gtk/src/rbgtkbuilder.c }} bug persist, new unrecoverable problems with Pango and Cairo libraries cropped up. After my latest experiences and indeed all the early warnings that something in the areas of gdk, canvas and rendering is not quite right I was not as much surprised as disappointed that my worst fears materialized and left me dead on my tracks.

Does anybody know anything more about these issues, and perhaps a solution to the problems they created:confused:

---

