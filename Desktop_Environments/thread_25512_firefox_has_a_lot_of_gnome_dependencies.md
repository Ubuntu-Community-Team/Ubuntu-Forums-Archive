---
title: "firefox has a lot of gnome dependencies?"
date: 2005-04-10
forum: Desktop Environments
---

### Post by dworzec.net on 2005-04-10
hello everybody,
in my Kubuntu sudo apt-get install mozilla-firefox results in the folowing dependencies which must be installed:
> gconf2 gnome-keyring gnome-mime-data libatk1.0-0 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libgconf2-4 libglade2-0
  libgnome-keyring0 libgnome2-0 libgnome2-common libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libpango1.0-0
  libpango1.0-common shared-mime-info 
what worries me is that I see a lot of gnome packages... do I really need them? why not KDE dependencies? what's more, I get suggested packages like this:
> gnome-icon-theme ttf-thryomanes mozilla-firefox-gnome-support
  latex-xft-fonts xprt-xprintorg which means even more gnome...

---

### Post by apokryphos on 2005-04-10
The Firefox in the Ubuntu repositories relies on GTK stuff because of the way it was made. If you want a Firefox without those things, you'll have to manually install it (which is among the easiest installations around).

---

### Post by dworzec.net on 2005-04-10
all right, now I know what they meant by "gnome based distro"...
I'll try the installer from mozilla site than...
thnx. :)

---

### Post by az on 2005-04-10
You will still end up with the libs, just statically linked.

---

### Post by dworzec.net on 2005-04-10
[QUOTE=azz]You will still end up with the libs, just statically linked.[/QUOTE]
what do you mean by this? I will have to install gnome stuff anyway?

---

### Post by Jonathan2007 on 2005-04-10
[QUOTE=dworzec.net]what do you mean by this? I will have to install gnome stuff anyway?[/QUOTE]
 I installed Kubuntu to begin with and didn't add KDE from Ubuntu (as it somewhat seems like you did). I used Kynaptic (it somewhat worked then) to install Firefox and it worked fine. I don't know what stuff it got but it looked like crap until I followed the tut on ubuntuguide.org on adding repositories to (K)Ubuntu. Then I downloaded gtk2-engines-gtk-qt and Firefox and all the other Gnome apps I use (Gaim, ...) looked much better. Hope that helps.

---

