---
title: "You do not have the permissions necessary to save the file"
date: 2009-05-04
forum: General Help
---

### Post by man0l0 on 2009-05-04
i have installed ubuntu 8.04 and it doesnt recognize my monitors resolutions.i try to edit xorg.conf to fix the problem but i cant save the changes and an error appears that says "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."what should i do??  please help  :confused:

---

### Post by Vonnick on 2009-05-04
You need to be editing it with root privileges. 

Press Alt + F2, then type "gksudo gedit /etc/X11/xorg.conf", without the quotes. You will be editing the file with root privileges now.

---

### Post by roger_1960 on 2009-05-04
Hi

You need root priviledge to edit and save the file.  run your editor with gksudo in front and enter your password when asked - it doesnt show when typing it.

Your editor should then allow you to edit and save the file.  eg

> gksudo gedit

---

### Post by man0l0 on 2009-05-04
at last!!thanks a lot!!! :)

---

### Post by meduser on 2012-03-11
> **roger_1960 said:**
> Hi

gksudo gedit

fixed it for me. Thank you.

Blown away everyday as to what a great site this is.

---

