---
title: "Duplicate one user's K Menu?"
date: 2005-09-25
forum: Desktop Environments
---

### Post by Old *ix Geek on 2005-09-25
I have a finely-tuned K Menu for one user that I'd like to exactly duplicate--without doing it manually!--for another user.  Is there an easy way to do this?

Thanks!

---

### Post by cwaldbieser on 2005-09-25
[QUOTE=Old *ix Geek]I have a finely-tuned K Menu for one user that I'd like to exactly duplicate--without doing it manually!--for another user.  Is there an easy way to do this?

Thanks![/QUOTE]
Looks like menus are stored in ~/.config/menus/applications-kmenuedit.menu for KDE 3.4.  You could probably just copy the file.

---

### Post by kosmic on 2005-09-25
If you want to apply that configuration to various new users just copy the file ~/.config/menus/applications-kmenuedit.menu to the /etc/skel directory, and all new users will have the same menu :)

---

### Post by Old *ix Geek on 2005-09-25
Thanks!  I'll give the suggestions a try.

---

### Post by Hairy_Palms on 2005-09-25
can you do the same thing in gnome?

---

