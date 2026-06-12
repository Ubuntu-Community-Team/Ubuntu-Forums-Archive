---
title: "Gnome 3.0"
date: 2010-02-13
forum: Desktop Environments
---

### Post by MattFinck21 on 2010-02-13
hey everyone, do any of u know how to install gnome 3.0 on an existing ubuntu installation?

---

### Post by deej1976 on 2010-02-13
Try:

sudo apt-get install gnome-shell

Then to try it, open a terminal and run:

gnome-shell --replace


For the daily builds add the following repository for latest build:
    sudo add-apt-repository ppa:ricotz/testing
then:
    sudo apt-get update
    sudo apt-get install gnome-shell

---

### Post by 3Miro on 2010-02-13
I followed the instructions here and got it running on my Karmic laptop.

[http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

---

