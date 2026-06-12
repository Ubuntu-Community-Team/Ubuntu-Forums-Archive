---
title: "How do I run a *_deb.sh file ?"
date: 2006-01-06
forum: Desktop Environments
---

### Post by pfabrikant on 2006-01-06
Hey,
I'm new with linux so please be gentle with your usage of technical terms in your replies..
I downloaded an OPenoffice new version for linux, it's called OOo_2.0_linux_Install_he_deb.sh. When I open it up in Linux, I have a window opening asking me if I want to run it or display it. When I choose to run it, nothing happens... How can I install the program ?
Thanks !

---

### Post by dcstar on 2006-01-06
[QUOTE=pfabrikant]Hey,
I'm new with linux so please be gentle with your usage of technical terms in your replies..
I downloaded an OPenoffice new version for linux, it's called OOo_2.0_linux_Install_he_deb.sh. When I open it up in Linux, I have a window opening asking me if I want to run it or display it. When I choose to run it, nothing happens... How can I install the program ?
Thanks ![/QUOTE]
Don't run it under the file manager, open a terminal and type:

cd directory-name-where-the-file-is
sudo ./OOo_2.0_linux_Install_he_deb.sh

---

### Post by professor_chaos on 2006-01-06
If your trying to install OpenOffice 2, then just add
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./
to your source.list file in /etc/apt/

then update....

---

