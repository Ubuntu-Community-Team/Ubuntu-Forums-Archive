---
title: "Java and KDE 4"
date: 2008-04-05
forum: Desktop Environments
---

### Post by Asham on 2008-04-05
I have a question regarding Java and KDE, more precisely KDE 4: is the lack of "native"/system look and feel a result of KDE 4 not being final just yet? I get the native look in Gnome but not in KDE, that is why I am wondering. 

Both Swing and SWT based applications look old. In the Swing case application get the default Java look (I think it's named metal) while SWT applicatons get some Windows lookalike look and feel. 

Will it be fixed eventually or has it always been like this? (I am new to KDE).

Adam.

---

### Post by trippinnik on 2008-04-05
Well the GTK look and feel was added relatively recently.  I don't know about any plans to add KDE look and feel, but hopefully.  If you are developing your own apps you can use QT and Java together and get a native look though.

---

### Post by Asham on 2008-04-05
Oh, so that is how it works - one style for GTK and one for KDE/QT. Meh, and here I was getting excited when I read up on Swing, only to find out it applies to just GTK/Gnome! :(

---

### Post by buu700 on 2008-04-22
'sudo aptitude install gtk-qt-engine-kde4'

That should make just about any non-Firefox app that looks native in GTK lok native in KDE4 as well (not Firefox because there are some problems with tabs and widgets).

---

### Post by Asham on 2008-04-22
It's not pixel perfect but it's good enough. thanks!

---

