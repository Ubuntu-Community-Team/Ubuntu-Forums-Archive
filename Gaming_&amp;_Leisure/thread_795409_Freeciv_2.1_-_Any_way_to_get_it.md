---
title: "Freeciv 2.1 - Any way to get it?"
date: 2008-05-15
forum: Gaming &amp; Leisure
---

### Post by ffahog on 2008-05-15
I was wondering if anyone knew of a simple method for installing Freeciv 2.1 (and especially Freeciv 2.14, SDL) on Ubuntu. The repositories haven't updated in forever, and try as I might I can't figure out how to do the compiling myself.

I've done some extensive searching on Google and Ubuntu, and I appear to have missed a window for acquiring it on _[getdeb.net]("http://www.getdeb.net/release.php?id=2076")_, because as best as I can tell they aren't supporting it anymore. (I get this error message when opening the package installer: "Error: Dependency is not satisfiable: freeciv-data")

---

### Post by Perfect Storm on 2008-05-15
Should work as well on 32-bit: [http://gaming.gwos.org/doku.php/guides:64bit:freeciv](http://gaming.gwos.org/doku.php/guides:64bit:freeciv)

note, where it says: ./configure --enable-client=gtk change it to ./configure --enable-client=sdl

---

### Post by ffahog on 2008-05-15
Thanks so much! It worked!

---

### Post by Vadi on 2008-05-15
> **ffahog said:**
> I was wondering if anyone knew of a simple method for installing Freeciv 2.1 (and especially Freeciv 2.14, SDL) on Ubuntu. The repositories haven't updated in forever, and try as I might I can't figure out how to do the compiling myself.

I've done some extensive searching on Google and Ubuntu, and I appear to have missed a window for acquiring it on _[getdeb.net]("http://www.getdeb.net/release.php?id=2076")_, because as best as I can tell they aren't supporting it anymore. (I get this error message when opening the package installer: "Error: Dependency is not satisfiable: freeciv-data")

They do support it - that error means you were supposed to install "freeciv-data" first, then the package you were trying to.

atm they go in an order... but the rule of thumb is to get data first, then other things.

---

### Post by elisagwendolyn on 2008-05-16
It is difficult to do it....

Please try continuously....:lolflag::popcorn:

---

### Post by maljaros on 2008-05-21
Apology for interrupting the thread, which seems to be solved, but why go for the sdl version?  Or to ask another way, why not GTK+ or Xaw3D?  Is this a KDE/Gnome issue, or what?

---

### Post by frenchn00b on 2008-05-22
> **ffahog said:**
> I was wondering if anyone knew of a simple method for installing Freeciv 2.1 (and especially Freeciv 2.14, SDL) on Ubuntu. The repositories haven't updated in forever, and try as I might I can't figure out how to do the compiling myself.

I've done some extensive searching on Google and Ubuntu, and I appear to have missed a window for acquiring it on _[getdeb.net]("http://www.getdeb.net/release.php?id=2076")_, because as best as I can tell they aren't supporting it anymore. (I get this error message when opening the package installer: "Error: Dependency is not satisfiable: freeciv-data")

Freeciv isnt working well

I would advice you : 
dosbox and simcity for msdos.
You can get it from abandonwares

---

