---
title: "Dual Ubuntu and Kubuntu System"
date: 2008-08-05
forum: Desktop Environments
---

### Post by ish4269 on 2008-08-05
Hey All

Firstly, sorry for being a bit lazy. I should search the forums for a thread on this topic. However, search for {Ubuntu Kubuntu dual} hits almost every thread in the forum. 

I am interested to know if anyone has successfully attempted to set up a dual/triple Ubuntu/Kubuntu/Xbuntu system. You can simply just forward me links. 

Back in the day I used to use SuSE before it became a commercial product. I loved having the variety of choosing a GNOME/KDE/X environment. 

I suppose the easiest would be just setup two/three separate partitions and setup GRUB accordingly, but that is just cheating. It would be nice, if possible, to setup at least two systems on the same partition, seeing as there is so much overlap of (K)Ubuntu.

Cheers, Ish

P.S. As I was writing this thread I realised setting up a dual system properly should be left to when one has many, many hours to waste.

---

### Post by Moridin333 on 2008-08-05
this is very easy.  install whatever you want then go to terminal or whatever command line you want to to install the other two

sudo aptitude install ubuntu-desktop

sudo aptitude install kubuntu-desktop

sudo aptitude install xubuntu-desktop


I recommend using aptitude instead of apt-get because it remembers what dependencies it installed and removes them automatically if you remove the -desktop package.

---

