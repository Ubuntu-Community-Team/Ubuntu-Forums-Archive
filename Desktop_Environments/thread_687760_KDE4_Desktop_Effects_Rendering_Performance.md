---
title: "KDE4 Desktop Effects Rendering Performance"
date: 2008-02-04
forum: Desktop Environments
---

### Post by Markus72 on 2008-02-04
Hi,

I just installed KDE4 on my Kubuntu 7.10 installation in addtion to my KD3.x desktop.
Besides some useability issues I experienced some severely noticeable performance impacts when desktop effects are activated.

Of course you might say - eye candy comes with some drawbacks.

Yes, that's true. But for example when I scroll down a web site in my firefox the complete scrolling feels delayed in reaction and it seems the rendering cannot compete with my scrolling.

It "feels" slow.
On the other hand: when I switch off the effects, everything is lightningly fast.

Let's say I had a Core2Duo with 2.2 GHz and a 512MB ATI Radeon HD2600 shouldn't I expect something else?

I cannot believe that enabling desktop effects can have these impact regarding my hardware...
Am I wrong?

Why is a MacBook so much smoother when it has the same or less hardware power?

Any ideas?

Markus

PS: even the show- and hide-effects of windows cannot be considered "smooth"

---

### Post by luisromangz on 2008-02-04
It's a problem with the software, it needs more optimizations. It simply is slow although it will improve, I hope.

---

### Post by puelocesar on 2008-02-04
Well, it can be your drivers for example. ATI drivers were known for being 2x slower than windows ones, but very recently they released better drivers for linux, but that were poor on compositing..

Right after that I got sick of waiting and bought a Nvidia one.

Well, here at home I have a good performance with kde4 and compositing, but it is a svn-compiled version of kde4 and it's a fast distro, Arch Linux, but on my work, I have Ubuntu Gutsy and installed kde4 packages, and they are, much more buggy and I can't barely ALT-TAB with composite enabled..

I think we have to wait a while for using compositing on Ubuntu's packages of kde4, because KWin4 compositing is very new and non-optimized, and KUbuntu's packages are always more than 1 month or more behind SVN kde4

---

### Post by Markus72 on 2008-02-05
Let's hope, these things change soon :-)

---

### Post by PmDematagoda on 2008-02-05
The changes and improvements are already underway and progress is looking good, you can check up on this by making regular visits to the KDE web site and by reading the KDE Commit Digests.

---

### Post by Markus72 on 2008-02-05
By the way: where would be the right place to post feedback about first kde4 experiences?

---

### Post by miggols99 on 2008-02-05
There has been a problem with Qt4 rendering widgets very badly. This means things will lag a lot. This will hopefully be fixed with Qt4.4 (around when KDE 4.1 is released - correct me if I'm wrong)

---

### Post by puelocesar on 2008-02-06
> **Markus72 said:**
> By the way: where would be the right place to post feedback about first kde4 experiences?

Well, you can submit bugs and wishes here:
[http://bugs.kde.org/](http://bugs.kde.org/)

---

