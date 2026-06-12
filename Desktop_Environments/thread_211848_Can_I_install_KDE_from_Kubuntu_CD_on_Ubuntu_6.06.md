---
title: "Can I install KDE from Kubuntu CD on Ubuntu 6.06?"
date: 2006-07-09
forum: Desktop Environments
---

### Post by kagashe on 2006-07-09
Hi,

I generally use Gnome but sometimes login to KDE to understand Kubuntu/KDE problems. At present I am having download limitations and could not download/install KDE from the repositories.

My friend had ordered Kubuntu CDs and I have exchanged one Ubuntu CD for Kubuntu with him.

I would like to know whether I can install KDE from Kubuntu CD by modifying the sources. I have added Kubuntu CD in Synaptic but when I try to install it starts downloading from the repositories and does not ask to insert the CD.

Please help.

kagashe

---

### Post by aysiu on 2006-07-09
You can install Kubuntu from the **Alternate** CD, but not the Desktop CD.

If you have the Alternate CD, pop it in the drive and ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

