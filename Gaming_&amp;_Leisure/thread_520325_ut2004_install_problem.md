---
title: "ut2004 install problem"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by stlouis1 on 2007-08-08
trying to run the linux-installer.sh from the konsole as root here. and here's what i get

> root@urmom-laptop:/home/urmom# cd /media/cdrom
root@urmom-laptop:/media/cdrom# dir
AutoRun.inf  CD1  CD2  CD3  CD4  CD5  CD6  linux-installer.sh  Setup.exe
root@urmom-laptop:/media/cdrom# linux-installer.sh
bash: linux-installer.sh: command not found
root@urmom-laptop:/media/cdrom# linux-installer
bash: linux-installer: command not found

now if i run it from my desktop as my user through the gui, itll install to my home folder. but i want to install it as root so itll go in the /usr folder cuz i want to keep my home folder for personal data

need help here really, im such a newb

---

### Post by stlouis1 on 2007-08-08
nvm, i just figured out my problem. changed tried different search terms

needed to run sh linux-installer.sh

thanks anyway

---

