---
title: "Highlighted menu item is dark blue...can't read selected item!"
date: 2008-11-02
forum: Desktop Environments
---

### Post by Flywaver on 2008-11-02
Hi,

I don't know where I can change the color of a highlighted item in a menu...right now it uses a dark blue which makes the items in black text unreadable! :(

This is not an issue in Dolphin or any of Kubuntu's menus!
So far I see it in apps like RhythmBox, pidgin, firefox.

Here is a screenshot attached!

Cheers!

---

### Post by txcrackers on 2008-11-03
That's an "artifact" of the GTK-QT plug-in. Think of it as a tranlation layer between GTK calls - such as used by Firefox - and the underlying KDE system. Depending upong your color scheme, it may not work quite so well. You can essentially disable it by going to System Settings -> Appearance -> GTK Styles and Fonts. Select "Use another style" and set it to "Raleigh". Apply.

You'll need to restart any GTK applications to see the results. You also have the option of removing the GTK-QT engine.

---

### Post by Flywaver on 2008-11-03
Thanks txcrackers! :)

Will do! 

What are the disadvantages in removing the GTK-QT engine, if any?
Cheers!

---

