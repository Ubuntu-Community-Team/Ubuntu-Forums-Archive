---
title: "Adding Window managers to Gnome GDM"
date: 2005-03-09
forum: Desktop Environments
---

### Post by hal8000 on 2005-03-09
Installed Ubuntu 5.03 and used the synaptic download manager to install the enlightenment and blackbox desktops.

After logging out of gnome 2.10 these are not automatically included in the session
menu. What file do I modify to include the new desktops to gdm? Thx in advance.

---

### Post by Qdlaty on 2005-03-09
You need to create a file named *winmanagername.desktop* in /usr/share/xsessions directory and put in it something like this:

[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Enlightenment
Exec=enlightenment
Icon=
Type=Application

it will start Enlightenment.
After that you need to restart GDM and that's all.

---

