---
title: "Frozen after logon"
date: 2009-05-22
forum: General Help
---

### Post by wilf on 2009-05-22
I have 9.04 installed and running fine until this morning.
Downloaded updates. Updates started to install then the screen froze. I rebooted but I can only enter my user name and password.Then nothing. Mouse is still frozen.
How can I recover my system?

---

### Post by severedspirit on 2009-05-22
if you can get into ssh, complete the update by using the following
sudo apt-get update
sudo apt-get upgrade
If you cannot get into ssh try getting into the bash by pressing CTRL+ALT+BACKSPACE

Then attempt to reinstall the desktop by using the following
sudo apt-get install ubuntu-desktop

---

### Post by wilf on 2009-05-22
Cannot get into anything. After logon, cursor and screen is frozen as well an keyboard.

---

### Post by clicktech on 2009-05-22
Before logging on hold CTRL+ALT+F1 to get to the command line and login there, then try the apt-get commands given above.

---

