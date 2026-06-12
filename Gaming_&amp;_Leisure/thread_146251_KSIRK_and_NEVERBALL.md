---
title: "KSIRK and NEVERBALL"
date: 2006-03-17
forum: Gaming &amp; Leisure
---

### Post by user1397 on 2006-03-17
These are two games found in the ubuntu main documentation page.
I don't know how to install them, could someone please tell me how?
(sorta an ubuntu noob)

---

### Post by Perfect Storm on 2006-03-18
First you have to enable universe in your sourelist, then

```
sudo apt-get install neverball
```

I wasn't able to find any .deb for Ksirk so you might download the source and then compile it. Please read this: [http://home.gna.org/ksirk/ksirk-kde-documentation/installation.html](http://home.gna.org/ksirk/ksirk-kde-documentation/installation.html) before starting compiling it.
The basic tools for compiling you'll need no matter what:
```
sudo apt-get install build-essential
```

When run ./configure keep a closer eye for the output, it will tell you what you need/missing.

Note: Ksirk is a KDE application/game so if you're on gnome desktop you need alot kdelibs and QT files.

---

### Post by user1397 on 2006-03-18
Thank you 
Neverball is working but I decided to not install ksirk

---

