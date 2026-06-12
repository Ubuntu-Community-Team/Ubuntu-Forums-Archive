---
title: "Gnome application launcher and custom environment variables?"
date: 2006-03-21
forum: Desktop Environments
---

### Post by bender unit on 2006-03-21
Hello,

I don't know if I'm missing something really obvious, but I can't get this to work for the life of me. I just want to have an application launcher that doesn't simply run an executable, but modifies the environment before that. Because some apps have problems with SCIM, I want to modify their launcher to run them with GTK_IM_MODULE=xim (e.g. I want to run "GTK_IM_MODULE=xim acroread"). In KDE, this is simple, you can just write use whatever you enter at the command line as the program command. But in GNOME, this doesn't work (why not?). 
Anyways, is there any way to achieve this other than aliasing the program's names to some command like that (does that even work?) or creating a custom script that does this? I find that workaround very cumbersome!

---

### Post by hw-tph on 2006-03-21
I have been pondering the same thing. I just want to run **LC_ALL="sv_SE" urxvtc** but it doesn't work, so I have resorted to writing a simple launcher script and put it in ~/bin (which is added to the $PATH in my login scripts).

---

### Post by bender unit on 2006-03-21
Sure, that'll work, like I said. But I don't find this very comfortable. Is that really the only way to solve this problem? Have the GNOME devs never thought about this issue when they decided to make GNOME not support this?

---

