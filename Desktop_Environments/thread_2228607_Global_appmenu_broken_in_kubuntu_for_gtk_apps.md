---
title: "Global appmenu broken in kubuntu for gtk apps"
date: 2014-06-08
forum: Desktop Environments
---

### Post by jxjl on 2014-06-08
hi, does anybody know, how to get global appmenu working for gtk apps and LibreOffice in new Kubuntu? I have installed appmenu-gtk as usual, unfortunatelly, this package is replaced by unity-gtk-module, that doesn't work with kde globalmenu plasmoid.

---

### Post by vincentz2 on 2014-07-24
Came across this post on Google whilst trying to look up the fix for this after a recent install of Kubuntu trusty.

This is the bug: [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1200006](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/1200006)

The problem lies with the package appmenu-gtk being replaced by [COLOR=#333333][FONT=monospace]unity-gtk-module, which doesn't work outside of Unity. This PPA fixes things for me: [/FONT][/COLOR]https://launchpad.net/~joe-yasi/+archive/ubuntu/appmenu

sudo apt-add-repository ppa:joe-yasi/appmenu
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install appmenu-gtk

Hope this helps.

---

