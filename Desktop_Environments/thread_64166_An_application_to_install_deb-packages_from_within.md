---
title: "An application to install deb-packages from within KDE"
date: 2005-09-10
forum: Desktop Environments
---

### Post by daller on 2005-09-10
Hi All,

Anyone knows about an application that can install deb-packages from within KDE?

---

### Post by djib on 2005-09-10
[QUOTE=daller]Hi All,

Anyone knows about an application that can install deb-packages from within KDE?[/QUOTE]
 Hello,
There is one in kubuntu isn't there ?
It is called kynaptic and is available in the 'System' sub-menu.

---

### Post by DarkT on 2005-09-10
I think he means to installed downloaded deb packages and I didn' think kynaptic or synaptic did that.
 
In konqurer you could right click on a deb package, go to open with and then choose your own app. Now set it to use a custom command and write *kdesu dpkg -i* and tick the box to open it in a terminal. That may be the sort of thing you are after but at the moment I'm in windows (erg) so I can't confirm it.

---

### Post by SGC on 2005-09-10
[QUOTE=daller]Hi All,

Anyone knows about an application that can install deb-packages from within KDE?[/QUOTE]

kpackage

---

### Post by DarkT on 2005-09-10
Does it? I didn't know that, I thought it just managed uninstalls etc. Good to know, thanks :)

---

### Post by haaglin on 2005-09-10
Try this one: 

[http://kde-apps.org/content/show.php?content=23981](http://kde-apps.org/content/show.php?content=23981)

---

### Post by yhotg on 2005-09-10
kpackage
in konqueror u right click on the .deb package and go to open with....
there u should have kpackage (if u did apt-get it   :-P )

now, i saw that kpackage stop working if change desktop while it's doing the install.
and i read in a post that is some kind of a bug, 
but i believe it will get your package installed.

(i went back to the command line after trying kpackage for a while, lol)

yhotg

---

### Post by daller on 2005-09-10
Kpackage is great - thanks!

---

