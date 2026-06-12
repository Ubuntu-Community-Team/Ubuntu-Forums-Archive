---
title: "Change File manager"
date: 2009-05-19
forum: General Help
---

### Post by Swatfoot on 2009-05-19
Im currently using nautilus and want to make Dolphin my default file manager. I tried preferred applications in the system menu but there
was no setting for file managers, so im assuming it has to be done through the terminal.

---

### Post by helofromseattle on 2009-05-19
install it from the repository, then change it in the default applications. hope this helps:p

---

### Post by colau on 2009-05-19
> **Swatfoot said:**
> Im currently using nautilus and want to make Dolphin my default file manager. I tried preferred applications in the system menu but there
was no setting for file managers, so im assuming it has to be done through the terminal.
aptitude install dolphin

---

### Post by Swatfoot on 2009-05-19
> **helofromseattle said:**
> install it from the repository, then change it in the default applications. hope this helps:p

Sorry should have said that I already have it installed but, just need to change it to default. Like I said before there is no option in preferred applications to change the file managers.

---

### Post by colau on 2009-05-19
> **Swatfoot said:**
> Sorry should have said that I already have it installed but, just need to change it to default. Like I said before there is no option in preferred applications to change the file managers.
[Info]("http://www.linuxquestions.org/questions/linux-software-2/change-of-default-file-manager-700122/")

---

### Post by Swatfoot on 2009-05-19
Found this in another thread works for me for now.


1. right click Menu Bar and choose edit menu
2. highlight Other
3. right click "open folder" item and go to properties
4. just replace nautilus + arguments with dolphin.

Thats it.

Hope it helps someone.

Ian

---

