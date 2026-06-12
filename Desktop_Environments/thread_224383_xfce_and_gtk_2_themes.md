---
title: "xfce and gtk 2 themes"
date: 2006-07-27
forum: Desktop Environments
---

### Post by Bosco on 2006-07-27
I just installed the Xubuntu-dekstop package to try out xfce.  I had a theme in Gnome that I'd like to continue using, and I simply cannot get it to work in Xfce.  The theme is called ish, and I've extracted it into my .themes dir and my /usr/share/themes dir to see if that had any effect.  When I run "User Interface Settings" under the settings meny the ish theme does show up (though whatever I choose here has almost no effect on my theme aside from some minor color changes).

When I run "Window Manager Settings" it allows me to change my window decoration, but the ish gtk 2 theme is NOT there.  Additionally, I've checked the themes dir, and based on what I found there, only xfce themes are showing up in this list.

How can I get gtk 2 themes working with xfce?

Thanks.

---

### Post by Ziox on 2006-07-27
i believe that in order of for the GTK 2 themes to show (and take effect on the computer), you need to install the GTK engine that runs the theme. Some theme-makers would provide the engine for you, or they would specify what engine to use (such as clearlooks).

There was one time when I had to install an engine, and to install the engine, I had to find a .deb package...i'm not sure about all the engine packages...

---

### Post by Bosco on 2006-07-27
Okay, well ish happens to be for clearlooks.  I checked Synaptic and it says that I have the clearlooks engine installed (gtk2-engines-clearlooks).

Any other ideas?

---

