---
title: "kde4 very slow"
date: 2008-08-16
forum: Desktop Environments
---

### Post by Ulrik04 on 2008-08-16
on Ubuntu 8.04, i've just installed kde4 (just installed desktop-kde4-kubuntu or something) and I can enter it without errors or anything, but it run really slow, and I can't use any effects at all. Just opening a single program is really slow. It's like the graphics card diver isn't activated, Ubuntu was the same until i installed nvidia-glx-new, but when I go to the drivers manager, it shows that my graphic card is in use. And before saying "if you want kde, install kubuntu" then it's only installed for fun and I still uses Gnome :D

and btw, can i remove all the kde programs like amarok and konqueror without messing kde up? :P

---

### Post by Ulrik04 on 2008-08-16
ok by changing a setting somewhere, it now runs fine and compiz is working, but still all buttons and menus are just ugly squares, like there's no theme on... how do i change this?

EDIT: noticed it's only in some programs like firefox that the theme doesn't apply, in conqueror, the buttons are smooth as they should...

---

### Post by benerivo on 2008-08-16
The kde4 theme will not be applied to non kde4/qt4 apps. This means that many programs like firefox will not use the kde4 theme, but instead revert to the the basic gnome/gtk theme. There is a package called gtk-qt-engine-kde4 that can you can set (via kde4 system settings) to apply your kde4 theme to gtk apps like firefox. You can download it with```
sudo apt-get install gtk-qt-engine-kde4
```

---

### Post by Ulrik04 on 2008-08-16
it worked, thanks :D

---

### Post by Ulrik04 on 2008-08-17
and one last thing, the system loading screen has changed to kubuntu blue instead of ubuntu orange. How can i change this back?

---

### Post by benerivo on 2008-08-17
See [this]("http://ubuntuforums.org/showthread.php?t=317487") thread.

---

### Post by ichthus on 2008-08-17
>  and btw, can i remove all the kde programs like amarok and konqueror without messing kde up? :P

Yes and no.  I should first qualify this by saying that I'm still using kde 3.5, but this should be accurate of kde 4.1 as well.

Konqueror is the browser and (kde 3.5) file manager that ships with KDE.  I believe it is part of kdebase, so removing it might result in removing all or most of kde.  I am not sure as I haven't really tried it.  But it uses libraries that exist as part of KDE for other applications (like d3lphin, the kde3 port of dolphin (the KDE 4 file manager) so removing it would probably be negligible.

Amarok is one of about 5 media players (including KsCD) for KDE, and can certainly be safely removed.  I understand that the KDE 4 Amarok (version 2) isn't even out yet (beta) so KDE 4.1 ships with Amarok 1 by default, so you're likely using a KDE 3 Amarok anyway (KDE 4.[01] isn't really the finished product: it basically means that the platform is ready.  The actual finished product will be KDE 4.2, set to release in January.)

---

### Post by Ulrik04 on 2008-08-17
just removed a lot of programs from add/remove, and it just told me when the program was a part of kde and couldn't be removed :)

@benerivo: thx :D

---

