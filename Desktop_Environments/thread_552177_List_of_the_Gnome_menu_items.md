---
title: "List of the Gnome menu items?"
date: 2007-09-16
forum: Desktop Environments
---

### Post by Fingolfin on 2007-09-16
Hi, just installed Debian 4.0 on the second hard drive. My first thought after several minutes spent in its Gnome environment is that I would like to recreate the same Gnome-Applications menu structure to the one from Ubuntu drive (after installing all of the additional programs).
In which file/directory are the Gnome-Applications menu entries actually stored?
I would think in  /usr/share/applications, all entries appear to be there but I couldn't find the file which "places" them onto the specific branches of the menu tree e.g. "Office", "Editors", "Games" etc...

---

### Post by Happy_Man on 2007-09-16
I would think that would be in the home folder's settings......

---

### Post by Fingolfin on 2007-09-16
Thank you for the thought :-)
I looked into the home ~, into the various ./gnome directories and found nothing.
Then I went into  /usr/share/  with a notion that all applications and their predefined meny entries are stored into the system after installation for all users. 
Alacarte Menu Editor then allows the user to simply switch the menu entries on/off in the predefined menu tree as its list must be stored somewhere in advance.
I havent found that file yet.

---

### Post by Wolki on 2007-09-16
> **Fingolfin said:**
> Then I went into  /usr/share/  with a notion that all applications and their predefined meny entries are stored into the system after installation for all users. 
Alacarte Menu Editor then allows the user to simply switch the menu entries on/off in the predefined menu tree as its list must be stored somewhere in advance.
I havent found that file yet.

And you're basically right, except that the issue is a bit more complex. Gnome follows the freedesktop.org specification here, two are relevant: the desktop entry spec for describing how the menu entry works (found here: [http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec](http://www.freedesktop.org/wiki/Specifications/desktop-entry-spec) ) and the menu spec for how the menus are constructed from there (see here: [http://www.freedesktop.org/wiki/Specifications/menu-spec](http://www.freedesktop.org/wiki/Specifications/menu-spec))

You can find the .desktop files for applications in /usr/share/applications/ and the basic menu structure in /etc/xdg/menus (especially the file applications.menu). Some other directories seem to be relevant as well, plus there's modifications by the user which live in the home directory. For more detail see the specs.

---

### Post by Fingolfin on 2007-09-17
Yes, it is more complicated than one would expect.
I found the file applications.menu in /etc/xdg/menus where the main user menu items are listed + the complete list in /share/applications/*.desktop.
I'll have a more go at the links you provided to try to figure out how to extract (and reconstruct) the complete list from these files. Thanks.

---

