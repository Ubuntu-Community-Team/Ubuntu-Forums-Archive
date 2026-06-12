---
title: "Oneiric 32bit. Strange toolbar in fallback mode."
date: 2011-10-16
forum: Desktop Environments
---

### Post by drum on 2011-10-16
Strange Oneiric 32bit toolbar sits at top in fallback mode. It sits underneath my regular dropdown toolbar.
When the normal toolbar hides it leaves this other toolbar with "File Edit View Go Bookmarks Help" Alt-right/click brings up nothing to edit or remove it.
Never seen this before with any Gnome distro.
Any ideas how to remove it. I like a clean desktop.
Otherwise everyuthing looks and runs great in the new release.
Thanks.

---

### Post by Pirate Zoro on 2011-10-16
According to WedUpD8, there is a problem with Gnome-shell and fallback mode showing the nautilus menubar behind the panel when using transparent themes. There are three fixes. 

1. if you don't use unity, which I assume you don't at all, you can remove the global menu by running ```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
``` in a terminal.

2. you can make it so nautilus doesn't handle the desktop by opening gnome-tweak-tool (if you don't have it, run sudo apt-get install gnome-tweak-tool to install it) and clicking the desktop tab. There is an option to allow the file manager to run the desktop, just switch it off. You will, however, not be able to have icons on your desktop, and you will have to change the wallpaper with the appearance app.

3. The easiest way is to simply change the theme to one that isn't transparent.

Those are your options. the article can be found _[here]("http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html")_ for more tweaks and fixes.

---

### Post by drum on 2011-10-16
Thanks Pirate Zoro for your great help.
I downloaded the "tweak-tool" and that fixed it.
Also the link you included for extra tweaks is great too.
Cheers
:D

---

