---
title: "make launcher"
date: 2016-12-26
forum: Desktop Environments
---

### Post by pete1977x on 2016-12-26
can I make a launcher for the desktop ,not sidetray, a permanent one, that runs a terminal script like this...sudo rm *.gz
how??

---

### Post by Frogs Hair on 2016-12-28
What desktop environment and OS version ?

---

### Post by deadflowr on 2016-12-28
sudo in desktop launcher is problematic since sudo wants/needs a terminal to run.
Instead you can use pkexec; if you have the policykit package(s) installed. Which, more likely than not, is. It is a base package, as far as i know, after all.
Then just open a text editor and make a desktop file
here's a template
```
[Desktop Entry]
Name=Remove Stuff
Exec=pkexec rm some-file
Type=Application
Icon=any-image-will-do.jpg
```
that's all you need.
Then save it as something.desktop; needs to be a .desktop extension.
And depending on the desktop session in use could either be saved directly on the Desktop inside the Desktop folder (how you would do it in unity)
(with the method you might need to right click in the properties settings into permossions  and mark it as executable)

Or you might need to save it in ~/.local/share/applications, other desktops might need this method if they don't use the file manager to handle the desktop.

The second method would then place the new launcher/app in the menu system which you can then add to desktop through that desktop systems add to desktop methodology.

The pkexec command will bring up a pop authentication window every time you run the app. Allowing the app to run admin-level rights.


Hope it helps

---

