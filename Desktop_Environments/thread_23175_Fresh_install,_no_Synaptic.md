---
title: "Fresh install, no Synaptic?"
date: 2005-03-31
forum: Desktop Environments
---

### Post by Komakino on 2005-03-31
Hi.

I just finished installing KDE and it looks good and feels fast. However, when I tried to install some apps that I wanted, I had a couple of problems. I followed the instructions found at [www.kubuntu.org](www.kubuntu.org) and I typed 

> sudo synaptic 

in a Konsole shell, but it says 'command not found'? I guess that meant that Synaptic is not installed in my system. I tried Kynaptic and although it's ok for a work in progress, it does not allow me to add any repositories, which leads me to another problem:

I tried to edit my /etc/apt/sources.list but no repositories present? It's essentially blank. Nothing in there. 

Where can I get some directions as to what to write in my /etc/apt/sources.list? Anyone know of a list of KDE repositories? I'm liking Kubuntu better than Ubuntu Gnome and I'd really like to sort this thing out. 

Thanks for any help.

---

### Post by techlord on 2005-03-31
I found this list here in the forums and it works great
```
 
 # Ubuntu Hoary
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted

deb http://archive.ubuntu.com/ubuntu/ hoary universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe multiverse

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted

deb http://pt.archive.ubuntu.com/ubuntu hoary universe
deb-src http://pt.archive.ubuntu.com/ubuntu hoary universe

#Marillat
deb ftp://ftp.nerim.net/debian-marillat/ unstable main

```

---

### Post by apokryphos on 2005-03-31
No idea why your sources.list is empty (you must have deleted it at some time); Kubuntu doesn't come with synaptic, but it does have Kynaptic. Though, it is pretty primitive and you might want to try out KPackage and see if you like that -- you can alter the repositories from there.

techlord's repositories above seem in order, so you might want to use that one.

---

### Post by Komakino on 2005-04-01
Problem Solved. Kate editor was not opening the sources list when I did 'sudo kate /etc/apt/sources.list' unlike gedit which does.

I just opened Kate editor manually, and loaded the /etc/apt/sources.list through a GUI browser. 

then they appeared.

Thank you **techlord** and **apokryphos.**

---

