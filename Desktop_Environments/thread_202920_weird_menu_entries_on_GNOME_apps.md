---
title: "weird menu entries on GNOME apps"
date: 2006-06-24
forum: Desktop Environments
---

### Post by dhaneshr on 2006-06-24
After the recent GNOME update, my UBUNTU 6.06 LTS system running on a Dell D600 exhibits peculiar menu entries for major GNOME apps such as gedit, evince,   gimp and evolution. On these applications, menu entries typically look like this:

xx   Keyboard Shortcut | CTRL-F
yy  Keyboard Shortcut | CTRL-V

Why do the words "Keyboard shortcut | CTRL-xx" appear on several menus on these apps ? Is this a bug ?

---

### Post by dhaneshr on 2006-06-25
Found a solution to this problem. It seems that after the GNOME update, the locale is set to English(Autralia). Change the language settings back to English (USA) via Administration->Language Support->Default Language and you're back in business.

---

