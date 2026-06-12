---
title: "How do I install the latest version of GNOME 3?"
date: 2011-07-23
forum: Desktop Environments
---

### Post by quyvuong00 on 2011-07-23
#1 : Open synaptic package manager and add the PPA (Settings -> Repositories -> Other Softwares, then add the PPA given below ) for GNOME 3.

ppa:ubuntu-desktop/gnome3-builds


#2 : Then, update the repository packages (using Reload button).

#3 : Now search for gnome 3 package and install it.

sudo add-apt-repository ppa:ubuntu-desktop/gnome3-builds
sudo apt-get update && sudo apt-get install gnome-desktop3

But This does not work with Lucid 10.04 as the software repository for Lucid (referenced above) does not exist.

can you help me ? plz, i don't want to reinstall ubuntu

---

### Post by Frogs Hair on 2011-07-23
I don't know if I could help , but please explain your current problem . Why do you think a re-installation is needed .

---

### Post by Krytarik on 2011-07-23
Well, afaik, currently there is no Gnome 3 PPA for Lucid, and the one you are referring to is dead anyway.

Greetings.

---

