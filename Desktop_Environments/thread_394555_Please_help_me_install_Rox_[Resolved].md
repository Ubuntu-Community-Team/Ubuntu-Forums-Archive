---
title: "Please help me install Rox [Resolved]"
date: 2007-03-27
forum: Desktop Environments
---

### Post by pelikan on 2007-03-27
I did a server install of Feisty, then put on Fluxbox. I'd like to use Rox but I have no idea how to install it. 

Thanks.

---

### Post by aysiu on 2007-03-27
Get to a terminal (Control-Alt-F1 is a quick way) and type ```
sudo nano -B /etc/apt/sources.list
``` Uncomment (i.e., remove the # from in front of) all the lines that look like web addresses. Save (Control-X, Y, Enter). Then install Rox with this command: ```
sudo apt-get update && sudo apt-get install rox-filer
``` Finally, return to Fluxbox with Control-Alt-F7

---

### Post by pelikan on 2007-03-27
That worked. I had tried "install rox." But install "rox-filer" worked. Thanks!

---

### Post by aysiu on 2007-03-27
For future reference, you can do ```
aptitude search rox
``` to find out the exact name of the package.

---

### Post by pelikan on 2007-03-27
good to know. ty

---

