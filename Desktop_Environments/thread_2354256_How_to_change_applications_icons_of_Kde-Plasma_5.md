---
title: "How to change applications icons of Kde-Plasma 5"
date: 2017-03-01
forum: Desktop Environments
---

### Post by fernando.cesar on 2017-03-01
I'm using

    Kubuntu 16.04
    KDE Plasma version 5.5.5

In my applications I have these enormous icons. Eg., from Dolphin:

[IMG]https://i.stack.imgur.com/1spSI.png[/IMG]

Which I cannot change. I tried "System Settings"-> changing everything in "Appearance", except the theme that remains Breeze because I couldn't find any other. But these icons remain the same. Help?

Thanks!

---

### Post by fernando.cesar on 2017-03-17
For some reasons my apps were using GTK+ settings.
 I had to unset environment variable "QT_QPA_PLATFORMTHEME".
Alternatively,  I was able to change icons by changing GTK2 settings, in "System  Settings" -> "Applications Style" -> "Gnome Applications Style".

---

