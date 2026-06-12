---
title: "Gnome 3 - Application spawns another icon in dock"
date: 2011-10-15
forum: Desktop Environments
---

### Post by freefragx on 2011-10-15
Hey there, I'm using ubuntu 11.10 and the Gnome 3 shell.

Everytime I launch a game called heroes of newerth, a new-blurriedicon  spawns in the overview  (same in the alt + tab menu). Does anyone know  what the isssue might be? Here is a screenshot that describes what I  mean:
[[IMG]http://img542.imageshack.us/img542/7531/shot.th.png[/IMG]]("http://imageshack.us/photo/my-images/542/shot.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

---

### Post by crdlb on 2011-10-15
GNOME Shell (and Unity) has to match open windows to the .desktop file describing the application. One very reliable way for this to work is [startup notification]("http://developer.gnome.org/integration-guide/stable/startup-notification.html.en"). You may want to request that the game authors add that (assuming this is a native linux game).

Out of curiosity, have you tried this game in Unity? Unity has a [different implementation]("https://launchpad.net/bamf") that may have better quirks support.

---

### Post by freefragx on 2011-10-15
> **crdlb said:**
> GNOME Shell (and Unity) has to match open windows to the .desktop file describing the application. One very reliable way for this to work is [startup notification]("http://developer.gnome.org/integration-guide/stable/startup-notification.html.en"). You may want to request that the game authors add that (assuming this is a native linux game).

Out of curiosity, have you tried this game in Unity? Unity has a [different implementation]("https://launchpad.net/bamf") that may have better quirks support.

Hi, thanks a lot for your response. It works correctly on unity, but since I prefer gnome I'm going to have to request the developers to tinker with the desktop file.
Also do you have any idea why the "new" icon is blurry, while the previous one looks normal?

---

### Post by crdlb on 2011-10-15
The second icon is the one set by the application in the window's X properties. You can see this by running xprop in a terminal and clicking on the window. It's possible to embed multiple icon sizes, including gigantic sizes like 256x256, but that was not common until recently. When everything is working properly, the shell has an icon name from the .desktop file to use, and it can use any available size. That also allows your icon theme to override app icons to fit better with the theme.

---

