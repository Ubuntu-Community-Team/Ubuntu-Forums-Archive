---
title: "Liferea unread folder"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Matt Houston on 2005-11-29
Hi, 

Anybody ever deleted their unread folder in Liferea? How did you get it back, I even tried re-installing and it's still gone. Ideas?

---

### Post by Xian on 2005-11-29
[QUOTE=Matt Houston]How did you get it back, I even tried re-installing and it's still gone. Ideas?[/QUOTE]
Two ideas:

1. Try purging the application:
$ sudo apt-get remove --purge liferea

2. Remove the /home/yourname/.liferea folder.

---

### Post by Matt Houston on 2005-11-30
Nice one, deleting the folder did the trick.

---

