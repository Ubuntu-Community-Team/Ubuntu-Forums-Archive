---
title: "Changing Terminal's title"
date: 2008-01-13
forum: Desktop Environments
---

### Post by salah_tr on 2008-01-13
how to make **mp3blaster** changing the Terminal's title :?:
I tried the following procedure but it didn't work 
:arrow: **Open Edit > Current Profile > Title and Command**
:arrow: set **Dynamically-set title** to** Replace initial title**

---

### Post by kellemes on 2008-01-13
[http://ubuntuforums.org/showthread.php?t=448614]("http://ubuntuforums.org/showthread.php?t=448614")
[http://www.unix.com/sun-solaris/23038-change-terminal-title.html]("http://www.unix.com/sun-solaris/23038-change-terminal-title.html")
[http://blog.technomancy.org/2007/04/06/change-the-gnome-terminal-tab-title-from-the-command-line/]("http://blog.technomancy.org/2007/04/06/change-the-gnome-terminal-tab-title-from-the-command-line/")

---

### Post by salah_tr on 2008-01-18
Thanks for reply kellemes
I tried the following code to change the title's **Terminal** when I lunch **mp3blaster**
```
echo -en "\033]0;MP3blaster\a"
mp3blaster
```
I'm wonder how to change the title again after **mp3blaster** is exited :?:

---

