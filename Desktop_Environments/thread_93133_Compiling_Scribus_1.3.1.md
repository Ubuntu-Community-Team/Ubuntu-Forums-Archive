---
title: "Compiling Scribus 1.3.1"
date: 2005-11-21
forum: Desktop Environments
---

### Post by Ian Christie on 2005-11-21
I've been trying to compile Scribus 1.3.1 and also tried the cvs versions on Breezy. Each time I get this message from ./configure

checking for Qt... configure: error: Qt (>= Qt 3.3) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!

Now I do have the Ubuntu package Scribus (1.2.2.1-1ubuntu1) which apparently installed libqt3-mt (>= 3:3.3.4) when I used synaptic. So I would assume that I have the correct version for 1.3.1 but for some reason it's not being found.

I've also installed QT4 using Synaptic.

Any sugestions of how to fix this or where to find a binary package of 1.3.1 would be great.

---

### Post by Ampersand on 2005-11-21
When compiling, you also need the development packages. Install libqt3-mt-dev and it should work.

---

### Post by Ian Christie on 2005-11-21
Thanks for the sugestion, just checked and I forgot I had already installed libqt3-mt-dev. Still doesn't like me.

---

