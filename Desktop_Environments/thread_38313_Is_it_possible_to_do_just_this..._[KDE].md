---
title: "Is it possible to do just this...? [KDE]"
date: 2005-05-30
forum: Desktop Environments
---

### Post by Mr Hatch on 2005-05-30
Hi,

I recently abandoned Ubuntu from my harddisk for a while, for I felt my favourite WM, which is KDE, to be somewhat immature. I stumbled over a SuSE 9.3 DVD containing just any Source-RPM they use to install a well-balanced and nicely tweaked KDE 3.4.

I just thought for a while about the opportunity to use **unrpm** to unpack SuSE's src.rpms containing the source (tar.gz) and the necessary spec-file.

For KDE 3.4 under SuSE is running like a charm I wonder whether it is possible to creat *.deb-files from these sources and install them just as I would with KDE coming from the repositories.

What do you think? Is it possible, or just not realisable?

---

### Post by ltmon on 2005-05-31
Unfortunately SuSE has probably tweaked KDE beyond all recognition, and getting it to compile from SuSE on another platform will be a real labour of love.

Personally I wouldn't recommend... but what the hey, if you want to try.

Once you have the vanilla source you should do a normal 

./configure --prefix=[whereamiinstallingto?]
make

and then use the program "checkinstall" to do

sudo checkinstall make install (read up on this first... it may need other options)

This will create a fairly minimal deb package easily enough as longs as you got past the ./configure and make stages.

By the way, what parts or tweaks to KDE do you like in particular?  In other words, what's missing from Kubuntu?

L.

---

