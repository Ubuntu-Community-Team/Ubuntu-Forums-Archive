---
title: "Multiple Mouse Pointers in X"
date: 2007-02-08
forum: Desktop Environments
---

### Post by johng4 on 2007-02-08
I've read a few articles on building multiple seats on a single X server, which is neat.  However, I was more interested in the concept of implimenting multiple pointers within a single X session.  The idea is to have 2 touch screens with seperate inputs, and a mouse working independantly on a multi-view setup.

Though, the test bed, would be a laptop with the touchpad and usb mouse working simultaneously with two different pointers on 2 different monitors.

Anyone know which direction to go?  Is X capable of this without patching?

---

### Post by shareMenaPeace on 2007-02-08
Maybe you want
HowTo: Dual Monitors (Xinerama/TwinView/MergedFB)  
[http://ubuntuforums.org/showthread.php?t=221174&highlight=1+desktop+2+screen](http://ubuntuforums.org/showthread.php?t=221174&highlight=1+desktop+2+screen)

---

### Post by johng4 on 2007-02-08
I can get 2 monitors working just fine with linux.  What I want are 2 different mouse input devices working at the same time, and independant of each other.

---

### Post by johng4 on 2007-02-09
Still googling.. I know its possible with extra patches, but some of these articles are for older versions of XFree/Xorg

---

### Post by kamallneet on 2008-07-08
It's called MPX, and it's finally a part of Xorg. The code is in the master branch of xserver. It is not planned for the next release, so get from git.

---

### Post by brnetonboy on 2008-07-10
> **kamallneet said:**
> It's called MPX, and it's finally a part of Xorg. The code is in the master branch of xserver. It is not planned for the next release, so get from git.
wait... what? It's part of Xorg but it's not part of the next release? Which release of Xorg will contain MPX?

---

