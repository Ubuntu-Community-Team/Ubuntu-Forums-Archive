---
title: "Choosing between KDE and Gnome on login"
date: 2007-04-02
forum: Desktop Environments
---

### Post by M$LOL on 2007-04-02
I'm running Edgy, and I'd like to be able to choose between KDE and Gnome when I login. It's probably been asked before, but can I do that and if so how?

---

### Post by Majorix on 2007-04-02
Have you installed kubuntu? If not type this in:
```
sudo aptitude install kubuntu-desktop
```

Then while it is installing it will ask you for the default env. Choose one there.

And if you want to for some reason switch back and forth you can use the "Options" link in the login screen, in the bottom left corner of the screen.

Also, if you want to uninstall kubuntu back again, then type:
```
sudo aptitude remove kubuntu-desktop
```

Make sure you do this install/uninstall with aptitude or you will have to manually type in the package names when uninstalling.

Good luck.

---

### Post by Arby on 2007-04-02
Assuming you have both kde and gnome installed then yes you can do that. When you get to the login screen there should be a button that looks like a very small menu to the left of the username/password boxes. If you click that you should get a menu, one of the options is session type. Under there you should be able to select KDE or Gnome if both are installed. That's where the menu is in KDE, I'm not sure about gnome but it should be on that screen somewhere.

Arby

---

