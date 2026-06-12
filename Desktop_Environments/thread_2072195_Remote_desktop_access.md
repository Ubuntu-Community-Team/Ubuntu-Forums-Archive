---
title: "Remote desktop access"
date: 2012-10-17
forum: Desktop Environments
---

### Post by sudtech on 2012-10-17
The Remote Desktop access  option is not visible in Ubuntu 12.10 . I need to access remotely Ubuntu desktop from a windows PC or a thin client via RDP .

I tried Xterm , but i need to press f2 or f3 for the desktop and also there is no proper option for log off and killing any open applications .

Kindly let me know if anyone has done the same before

---

### Post by PowerBarry43 on 2012-10-17
Hi

Have you considered using tightvnc or is this not suitable for your needs?

you can install a server and a viewer in ubuntu by running

```
sudo apt-get install tightvncserver vncviewer

```and run by typing the package names in a terminal.

There are also Windows version widely and freely avaible all over the web :)

if you wish to use RDP I believe it's started in ubuntu by using the command rdesktop in a terminal

Hope this helps!

Barry

---

