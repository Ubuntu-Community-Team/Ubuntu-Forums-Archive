---
title: "[SOLVED] Installing GTK Theme Engine"
date: 2008-12-31
forum: Desktop Environments
---

### Post by sharathpaps on 2008-12-31
Hi,
      I've just started experimenting with Themes in Ubuntu Intrepid Ibex. When I tried applying a theme I got an error message saying that the theme would not work correctly without the GTK Theme engine.

How do I install the GTK engine and its dependencies in Ubuntu Intrepid Ibex 8.10?


Thank You

---

### Post by mcduck on 2008-12-31
Depends on what theme engine you are trying to install. Quite many are available in Ubuntu's repositories and you can install them with Synaptic. Just search for "gtk2-engine" to find them all.

If the engine you want isn't available you can most likely download it from gnome-look.org. In that case try to look for .deb packages made for Ubuntu, they can be installed simply by downloading them to your deskop and double clicking the icon.

If .deb packages are not available things get a bit more complicated, as you'll probably need to compile the theme engine from source code. In that case the instructions should be included in the source package.

---

### Post by sharathpaps on 2008-12-31
@mcduck

Thanx for the help... I managed to compile the Aurora Gtk engine from source and install new themes. I'm putting down what I did here so that it will help anyone trying to solve the same problem...

I got the engine from [this]("http://gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438&PHPSESSID=4c458aa6e7a11636a6fb9c641a7bd9f9") link.. The description has a series of steps for installation ie. compiling from source that are pretty self explanatory.

The only problem that I ran into was I got an error message while trying to compile "configure: error: GTK+-2.10 is required to compile aurora"

This was easily solved by typing "sudo apt-get install libgtk2.0-dev" at the terminal as adviced in [this]("http://ubuntuforums.org/showthread.php?t=619065") post..

I'm a happy themer now.. In addition, I found some really nice themes for Intrepid Ibex [here]("http://www.junauza.com/2008/08/10-beautiful-themes-for-ubuntu-intrepid.html")

Thats it...Thanks again... :-D

---

