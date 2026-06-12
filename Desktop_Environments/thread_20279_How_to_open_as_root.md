---
title: "How to open as root"
date: 2005-03-15
forum: Desktop Environments
---

### Post by droogie on 2005-03-15
When using the disk browser, how can I click on a file and open it as root for editing.  I can do it from the terminal, just not from the window.

-Mike

---

### Post by Buffalo Soldier on 2005-03-15
[QUOTE=droogie]When using the disk browser, how can I click on a file and open it as root for editing.  I can do it from the terminal, just not from the window.[/QUOTE]
What works for me is [Nautilus script](http://www.ubuntulinux.org/wiki/NautilusScriptsHowto). For that specific function of editing file as root, the *Edit file with gedit with root-privileges* script should work fine.

---

### Post by iomicifikko on 2005-03-16
[QUOTE=Buffalo Soldier]What works for me is [Nautilus script](http://www.ubuntulinux.org/wiki/NautilusScriptsHowto). For that specific function of editing file as root, the *Edit file with gedit with root-privileges* script should work fine.[/QUOTE]
 or simply open nautilus with root privileges:
 from terminal:

$sudo nautilus starting_dir

ex:

sudo nautilus /home

byez

---

### Post by MaX on 2005-03-16
[QUOTE=droogie]When using the disk browser, how can I click on a file and open it as root for editing.  I can do it from the terminal, just not from the window.

-Mike[/QUOTE]
 Or you could do:
ALT+F2
gnome-sudo nautilus

Then you won't have to open a terminal at all.

---

