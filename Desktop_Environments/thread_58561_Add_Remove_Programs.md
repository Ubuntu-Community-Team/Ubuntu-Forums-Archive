---
title: "Add Remove Programs"
date: 2005-08-20
forum: Desktop Environments
---

### Post by speedemonV12 on 2005-08-20
Hi when ever i try to run add remove programs....it opens up but then it never fully opens...like when i move my mouse over it it goes to working...like it is busy...so it never gives me the list....is there anyway that i can remove it...the reinstall addremove programs...or does anyone know what is going on???


thanks

speedy

---

### Post by AnythingBut on 2005-08-20
you can remove it using

sudo apt-get remove gnome-app-install

and reinstall using

sudo apt-get install gnome-app-install

You might get some useful debugging information if you run it from a terminal.  Run "sudo gnome-app-install" and watch the terminal for its output.  Mine responds with:
```
Reading package lists... Done
Building dependency tree... Done
Got badly sized icon for gnome-util
Got badly sized icon for xmms_mini
Got badly sized icon for hwdb

```

---

### Post by speedemonV12 on 2005-08-20
this is what i get ....


Reading package lists... Done
Building dependency tree... Done
Traceback (most recent call last):
  File "/usr/lib/gnome-app-install/AppInstall.py", line 125, in idle
    self.updateCache()
  File "/usr/lib/gnome-app-install/AppInstall.py", line 144, in updateCache
    self.populate_menu()
  File "/usr/lib/gnome-app-install/AppInstall.py", line 242, in populate_menu
    import locale ; menu.setLocale(locale.getlocale(locale.LC_MESSAGES)[0])
AttributeError: Menu instance has no attribute 'setLocale'



any suggestions?

---

