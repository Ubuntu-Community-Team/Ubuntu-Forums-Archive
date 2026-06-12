---
title: "how to find out how to start game package"
date: 2005-08-12
forum: Gaming &amp; Leisure
---

### Post by Nasir Amra on 2005-08-12
I've often downloaded game packages from ubuntu universe, but I can not easily figure out how to start it. Where does one go to figure out how to start it ( especially since it doesn't show up in the menu under games ) . Examples: ggz-gtk-games. 

I think that there should be a standard way to add a menu item for these downloads in the menu tree  when installing these packages. I think debian used to do it that way.

---

### Post by AndyAWS on 2005-08-12
As I understand it, some packages are not yet compliant with the menu system in Gnome 2.10.

This is what I do if a menu item is not added...
Run Synaptic, search for the package you just installed. Look at properties and go to the tab that shows you the files that were installed for that package. The executable should be a file that was put in a bin folder. Run the executable from a terminal, or create a menu entry yourself with Smeg.

Or post the name of the package in question here and someone will probably know how to run it.

---

### Post by AndyAWS on 2005-08-12
Also 'sometimes' if something doesn't show up in Gnome's menu, you may be able to find it in the KDE menu (if you have Kubuntu-desktop installed).

---

### Post by No6 on 2005-08-12
Also, if you install the menu package you get the debian menu back. With all the entries fro everything there! (I like the Debian menu...)

```
sudo apt-get install menu
```

---

