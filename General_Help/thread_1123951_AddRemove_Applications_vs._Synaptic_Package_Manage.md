---
title: "Add/Remove Applications vs. Synaptic Package Manager"
date: 2009-04-12
forum: General Help
---

### Post by zzzBrett on 2009-04-12
New to Ubuntu here,

I have both Add/Remove Applications and Synaptic Package Manager to install applications.  Does it matter which I use, or are they the same?

Also, I noticed that the Add/Remove Applications one also adds the program to the taskbar menu -- does Synaptic not always do this?

Thanks!

---

### Post by Universal344 on 2009-04-12
add/remove is for installing applications, which may consist of multiple packages.  Synaptic is for installing individual packages, some of which are applications (and will be added to menus) and others are not.  If you want access to the full repositories you should use synaptic.  They both satisfy package dependencies so they are both relatively easy to use.  There are a number of apps that add/remove doesn't see so you you should always search synaptic before giving up.

---

### Post by 3Miro on 2009-04-12
Software is split into packages, Synaptic allows you view/install and remove all packages. Add/Remove is a variation where things a split into "Applications". When you install an Application you actually install several packages that correspond to the app.

There are things (some add-ons and such) that can only be installed via Synaptic, other than that, there is no difference. I use Add/Remove whenever I can just because it is easier.

---

### Post by acimmarusti on 2009-04-12
They are almost the same. The add/remove gui is meant to be more user friendly. Both should add the icons to the menus. Synaptics is better if you are looking for an specific package that you need, like some library, etc. Also, not everything that is listed in synaptics is in the add/remove gui

---

### Post by zzzBrett on 2009-04-12
Thanks for the replies.

One more (semi) related question:
If a program does not appear in the menu, I see where I have the option to add it, but how would I go about finding the command to run?

Ex) Calculator's command is: gcalctool

How would I find this if it wasn't already there?



Thanks again.

---

### Post by oldos2er on 2009-04-12
Most user-installed executables wind up in /usr/bin. You can use the "which" command to find where an executable is in the file system, e.g.
```
which [program name]
```

---

### Post by zzzBrett on 2009-04-12
Perfect, thanks!

---

### Post by mb_webguy on 2009-04-13
Also, be aware that applications aren't necessarily listed in the Applications menu by their actual name.  For example, File Roller is listed as Archive Manager, because that's what it is.  gcalctool is listed in the Applications menu as Accessories->Calculator.

---

### Post by 3rdalbum on 2009-04-13
My signature has a screencast of how to find the name or location of a program that has been installed from Synaptic or Add/Remove Applications.

The package management system doesn't create a menu item - the package itself usually contains a file that gets installed and defines which menu to go into, what icon to use, and translations of the program name and description. This file gets installed in a place where the menu menu generator can find it. If you notice a GUI program that you install and it doesn't have one of these ".desktop" files (it doesn't get added automatically to the menu) then I'd advise that you file a bug report against the package.

---

