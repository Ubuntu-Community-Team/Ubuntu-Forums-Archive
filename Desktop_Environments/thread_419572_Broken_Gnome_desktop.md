---
title: "Broken Gnome desktop"
date: 2007-04-23
forum: Desktop Environments
---

### Post by francoisdp on 2007-04-23
Hi
I was busy installing a game that required python when the installation was interrupted.  Without thinking I let the python install start to uninstall some of the apps such as synaptic, nautilus and others, which I do not know.  The problem is that I cannot start the Gnome desktop.  I get the graphical login page, but following the login, I simply get the brown screen without anything else.

I have tried a number of things, but without any success - I think I have only broken it further.  It seems like I have to reinstall the x-window based applications with the whole Gnome desktop, but how?  Can anyone help me on this one?

Francois

---

### Post by kesomir on 2007-04-23
If GDM works, it would appear X is working ok and it's just gnome thats broken. You could try 

"sudo aptitude reinstall gnome" 

I believe gnome is the package, if not it could be

"sudo aptitude reinstall gnome-desktop"

I don't think this overwrites configs but I may be wrong, so you may wish to wait for words from someone wiser than I.

Best of luck regardless.

---

