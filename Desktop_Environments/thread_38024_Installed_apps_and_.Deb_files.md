---
title: "Installed apps and .Deb files"
date: 2005-05-29
forum: Desktop Environments
---

### Post by Peter Alien on 2005-05-29
sometimes i install several apps but the shortcuts arent created.
Does anyone know where the apps are installed, and how to create shortcuts ?

Just one thing more, when i intall apps with Synaptic, in what Folder Ubuntu keeps the .Deb files that were downloaded ?


Many thanks.

---

### Post by cudaman73 on 2005-05-29
most of your apps are installed in /usr/bin, or /bin, or /usr/local/bin.

most of the time (99% or so) you'll find them in /usr/bin.

apt-get stores cached .deb files in /var/cache/apt/archives/

as for creating shortcuts, just use the gnome menu editor. Its name escapes me at the moment, as I don't use it often, but I'm sure someone else can give it to you. the menu editor was taken out in Gnome 2.10, but there are several projects on sourceforge that do the job. i have a link to one somewhere in my history.. let me search for it.

---

### Post by Jenda on 2005-05-29
Although I don't know how to create new menu entries, I can tell you how to run the program and/or create a point&click launcher on your Gnome panels.

When you click "properties" in Synaptic, it shows you all the files installed from the package. You have to find the one that looks like the executable (for firefox, it's going to be firefox, for 3D chess it'll be 3Dc). If you use that as a command in the terminal, it'll run the prog.
Alternatively, you can rightclick a panel, click "add to panel", select "custom launcher" and enter the above found command into the command: field. Then enter whatever you want to appear as a tooltip (when you hover the mouse) in the name: field.
Hope this helps.

---

### Post by cudaman73 on 2005-05-29
found something useful.. perhaps. I myself don't use the menu all that much, but give this a look ->

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#menu-editor](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#menu-editor)

also. that's the unofficial ubuntu starter guide for hoary, so i'd suggest you bookmark the main page.

[http://www.frankandjacq.com/ubuntuguide/5.04/index.html](http://www.frankandjacq.com/ubuntuguide/5.04/index.html)  is what you want. go there first for questions ;)

EDIT: for the record, the program is called Smeg. /EDIT.

---

### Post by Peter Alien on 2005-05-31
Many thanks for your answers.

But, about the menu entries and the shortcuts, i wanna to do it in KDE 3.4 ?

Does anyone know how to do it ?

---

### Post by shakin on 2005-05-31
[QUOTE=Peter Alien]Many thanks for your answers.

But, about the menu entries and the shortcuts, i wanna to do it in KDE 3.4 ?

Does anyone know how to do it ?[/QUOTE]

Right click on the K menu and go to Menu Editor. It will let you add the shortcuts in whichever menu category you want. From there you can add a shortcut to your panel by right-clicking on the panel and going to Add to Panel -> Application, then selecting the app you want.

---

### Post by Peter Alien on 2005-05-31
Many thanks again mates :grin:  :grin:  :grin:

---

