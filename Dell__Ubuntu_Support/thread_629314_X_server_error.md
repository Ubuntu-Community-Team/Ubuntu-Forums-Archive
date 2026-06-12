---
title: "X server error"
date: 2007-12-02
forum: Dell  Ubuntu Support
---

### Post by Ivandro Moreira on 2007-12-02
Hi everyone,
 

I have a problem with x server , yesterday i´m configuring the Ubunto to get the Beryl and Emerald , and so i go to the  gedit/etc/X11/xorg.cnf  and put some codes to it , off course that i find this codes in a web page that said how to put my graphic card to is best performance, is everything going alright ,but after i finish and restart the pc a error ocurred and the graphical interface couldn't  open ! I thin k that i find what goes wrong but im new with ubuntu and i dnt know how to use the command llne to change the xorg.cnf .I tried to input the xorg commands but it says that the interface couldn't open. How cn i modify the xorg.conf page or is better to reinstall the xorg.conf ? and if it so how can i do that?

---

### Post by jken146 on 2007-12-02
In a terminal or in recovery mode: ```
dpkg-reconfigure xserver-xorg
``` will let you reset your X settings.

In future when you mess with configuration files, be sure to make a backup first!

---

