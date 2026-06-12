---
title: "Desktop Icon Issues Gnome Desktop"
date: 2020-05-20
forum: Desktop Environments
---

### Post by joandrew1981 on 2020-05-20
Hello I am running Xubuntu 20.04

I recently tried a new desktop environment gnome desktop 3

When I first logged in there were no desktop icons but I found a document on how to use the tweak tool snap to enable them.

The enabled but look like generic document icons and are named in the convention of Application.Desktop

Under the desktop folder in the file manager however they look normal and function normal

But if I double click them from the desktop this error appears.

Failed to add plugin to panel
GDBus.Error.org.freedesktop.DBus.Error.ServiceUnknown: The name org.xfce.Panel was not provided by any .service files

I tried to follow another doc which suggested copying icons from the usr/share/applications folder to desktop and I tried that and got a dialog asking me to approve the launching the file gave permission but nothing changed still Icon looks weird and receive the error stated above.

I must be really dumb because adding an icon to the desktop shouldn't be a 7 hour ordeal.

Can someone help please

Thanks in advance

---

### Post by daniewicz on 2020-05-20
I can't help you because I am using Ubuntu 20.04 (gnome) rather than Xubuntu 20.04 (xfce). I do want to tell you that you are not dumb, desktop icons are (highly) discouraged from my perspective as a new Ubuntu user. In Ubuntu (using gnome), you can install tweaks as you have done but it only allows for home and trash icons on the desktop.

I can offer a guess toward your problem. Are the [COLOR=#000000]Application.Desktop icons you mention marked as executable? Check the icon with a right click, properties, permissions.[/COLOR]

---

