---
title: "How to throw-out last session programs?"
date: 2005-10-12
forum: Desktop Environments
---

### Post by Czubek on 2005-10-12
Hi.
I hawe problem.
One day, about month ago I have save my session before logout. After login Gnome is freezing. I have to login throught option "awaryjny GNOME" (i dont know how to translate it to english - maybe rescue?) in menu session. 

Soulution of this problem is throw out information of saved sesion. Byt I don't know how? Can someone help me?

Thanks.

---

### Post by Alexander Kirillov on 2005-10-12
[QUOTE=Czubek]Hi.
I hawe problem.
One day, about month ago I have save my session before logout. After login Gnome is freezing. I have to login throught option "awaryjny GNOME" (i dont know how to translate it to english - maybe rescue?) in menu session. 

Soulution of this problem is throw out information of saved sesion. Byt I don't know how? Can someone help me?

Thanks.[/QUOTE]
This info is stored in the file~/.gnome2/session
If you delete it, default session values will be used instead.
I suggest you delete while not logged in to GNOME (e.g., from command line, - obtainable by ctrl-alt-F1; use alt-F7 to switch back - or from KDE).

---

### Post by Czubek on 2005-10-12
Thanks !!
It works!

---

