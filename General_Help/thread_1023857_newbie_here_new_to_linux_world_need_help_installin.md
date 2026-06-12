---
title: "newbie here: new to linux world need help installing aptana"
date: 2008-12-28
forum: General Help
---

### Post by szaflarski80 on 2008-12-28
hey. i have tried using some help on this forum and aptana website...
beginner in unix/linux os ... im having an issue unzipping to usr/local/aptana from terminal ... i was hoping that someone can help me

---

### Post by oldos2er on 2008-12-28
Anytime you work outside of your home directory, you need to give yourself admin privileges. In the terminal, use "sudo" with CLI apps, e.g. "sudo unzip filename.zip /usr/local/".

 If you prefer a GUI way to do the same thing, open a terminal and type "gksu nautilus" to open Nautilus with admin (or root) privileges.

---

