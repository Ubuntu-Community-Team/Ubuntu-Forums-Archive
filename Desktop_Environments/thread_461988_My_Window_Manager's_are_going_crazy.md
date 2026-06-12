---
title: "My Window Manager's are going crazy"
date: 2007-06-02
forum: Desktop Environments
---

### Post by Kobra on 2007-06-02
I'm starting to have problems with my Window Managers.  First, my Gnome window tops (It's the part at the top of windows, the part that would say Buddy List, Automatix, etc...) has disappeared and every window that I load acts like the top bar where my Application button is, it acts like it's a menubar.

What's going on here?

That's been happening for about 2 weeks now.  I installed Xubuntu so I could at least keep using my Ubuntu, but now it's started to fail.  In Xfce, the top and bottom bars have disappeared.  My machine runs perfect, it's just that I can't get to any of my applications, I don't know what time it is, etc...

What's going on here as well?

Please help!  Now I'm stuck using Windows for the moment, and it's killing me!

Thanks in advance!

---

### Post by kellemes on 2007-06-02
When stuff like this happens you often can fix it by deleting your Gnome and/or XFCE-sessionfile and temperarely disabling the saving of sessions at logout. There probably is crap in your sessionfile.
You only have to google to find the locations of these files, I'm not sure where they are.

---

### Post by kellemes on 2007-06-02
~/.gnome2/session for Gnome
so probably .xfce4/blabla for xfce??

---

### Post by llamakc on 2007-06-02
Did you enable Desktop Effects or try installing Beryl/Compiz around two weeks ago?

Anyway in Gnome you can type the key combo "alt+F2" to get a Run dialog. In that, type:

metacity --replace

---

