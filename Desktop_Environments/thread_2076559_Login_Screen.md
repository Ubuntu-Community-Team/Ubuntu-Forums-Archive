---
title: "Login Screen"
date: 2012-10-26
forum: Desktop Environments
---

### Post by Spit Fyre on 2012-10-26
If anyone could help me,I'd like to know how to change the Xubuntu 12.10 login screen background and icon.Thanks in advance to anyone who provides a solution x)

---

### Post by Toz on 2012-10-26
Hello and welcome to the forums.

The file that you need to edit is **/etc/lightdm/lightdm-gtk-greeter.conf** (you will need root privileges).

Make changes to the **logo** and **background** lines.

You will need to log out and back in again for the change to take effect.

---

