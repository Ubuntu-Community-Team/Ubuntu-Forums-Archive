---
title: "Installing IceWM"
date: 2005-12-21
forum: General Help
---

### Post by nami on 2005-12-21
Hi

I have a slow computer, which is most likely why ubuntu runs slow.  Is it possible to install IceWM and have the option to use either the default gnome or IceWM from the login screen?

---

### Post by localzuk on 2005-12-21
It should be. All you should need to do is enable the universe repository (take a look at [http://www.ubuntuguide.org](http://www.ubuntuguide.org) - bear in mind this site is aimed at hoary, so change references to hoary to breezy when altering sources.list) and run
```
sudo apt-get install icewm
``` or use synaptic and select the files you want.

---

### Post by Hairy_Palms on 2005-12-21
make sure your gdm theme has asession selection box, the default ubuntu one has, but some dont. then you can just change the session from gnome to icewm, thats what i do on my 300mhz p2 laptop

---

### Post by az on 2005-12-21
Install menu too.  Icem has menu functionality built-in, but installing the menu package populates it's menu system.

sudo apt-get install icewm menu

---

### Post by nami on 2005-12-21
Wow that was quick!  Thanks. :) 

How do I get other programs into the programs menu of IceWM.  For example, any other programs which I can access from ubuntu gnome?

I make or plan to make use of things like OpenOffice, which is not or does not seem to be available from IceWM's menu?

And also things like changing the screen resolution?

---

### Post by az on 2005-12-21
[QUOTE=nami]
How do I get other programs into the programs menu of IceWM.  For example, any other programs which I can access from ubuntu gnome?

I make or plan to make use of things like OpenOffice, which is not or does not seem to be available from IceWM's menu?[/QUOTE]

They should all be there.  They are all under applications or something (I forget).  The layout is differnet but you get everything that has a debian menu entry - and that is actually more than is in gnome.

[QUOTE=nami]
And also things like changing the screen resolution?[/QUOTE]

You can put a startup script in /home/you/.icewm/startup

Make it executable and it will be run every time you startup.  I am 99 percent sure that is the name of the file.  You can read the docs to confirm.

---

### Post by az on 2005-12-22
See the screenshot for menu location.

I also forgot -

xrandr can set the screen resolution for you.

---

### Post by nami on 2005-12-23
azz - Thanks for the screenshot.  However, for some reason in my programs menu I get nothing?

---

### Post by az on 2005-12-23
What do you have installed?

---

### Post by nami on 2005-12-23
All the default programs when I installed ubuntu 5.10 e.g. OpenOffice 2 is one of the suites I make use of a lot but is not in the programs menu?

You guys made it very easy to install IceWM, is it just as easy to uninstall it?

azz - thanks for telling me about xrandr, it worked perfectly :)

---

