---
title: "GTK and Enlightenment17"
date: 2007-06-27
forum: Desktop Environments
---

### Post by Freddy on 2007-06-27
Hi all.

I just wondered how to install a gtk theme and it's metacity engine under Enlightenment17. I have played around with both gtk-theme-switch and the far superior gtk-chtheme but to no avail.

I moved a folder that should contain the theme file E17-GTK/gtk2.0 to /usr/share/themes and it shows up in the theme selection menu but just the colors are changed the graphics looks like crap. The theme I tried to install also had several different metacity configurations and I tried copying some of them into /usr/share/gtk-engines but I guess that wasn't it, cause nothing changed.

Pls can someone with a little more knowhow let me in on the secret on how to install gtk themes without having Gnome installed.

Ohh this is the theme I would like to install: [http://www.gnome-look.org/content/show.php/E17+-GTK2+and+Metacity+%28not+official%29?content=60092&PHPSESSID=8ce7e929d6d98e348fc50d37d33628e8](http://www.gnome-look.org/content/show.php/E17+-GTK2+and+Metacity+%28not+official%29?content=60092&PHPSESSID=8ce7e929d6d98e348fc50d37d33628e8)

Hehe I have one more question for ya'll, how can I make submenus inside the right-click favorite menu. I would like a "headmenu" for audio, multimedia, internet, you get the picture right? :).

---

### Post by mcduck on 2007-06-28
For GTK themes, you are probably missing some GTK engine they are using. Like pixbuf or murrine..

E17 doesn't use Metacity as it's window manager, so Metacity themes won't work. But if you still want to install them, the corretc places are same where GTK themes go. (/usr/share/themes or ~/.themes)

---

### Post by Freddy on 2007-06-28
Yeah thanks, it was gtk2-engines-pixbuf I needed.

Still need some help on making submenus inside the favorite menu, so I'll bump this thread :).

/Freddan

---

