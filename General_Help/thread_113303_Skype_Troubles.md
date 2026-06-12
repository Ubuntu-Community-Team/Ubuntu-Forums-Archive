---
title: "Skype Troubles"
date: 2006-01-06
forum: General Help
---

### Post by kurokikaze on 2006-01-06
I've downloaded Skype tarball (with QT precompiled). I've unpacked it into /apps/ folder but when I do, from console,

```
~/apps/skype/#./skype
```

I get this message:

```
./skype: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory
```

Obviously I've already looked for libXcursor.so.1 in Synaptic and it's correctly installed. So, what's the problem?

---

### Post by neoflight on 2006-01-06
[QUOTE=kurokikaze]I've downloaded Skype tarball (with QT precompiled). I've unpacked it into /apps/ folder but when I do, from console,

```
~/apps/skype/#./skype
```

I get this message:

```
./skype: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory
```

Obviously I've already looked for libXcursor.so.1 in Synaptic and it's correctly installed. So, what's the problem?[/QUOTE]

here is what I did....(i posted the same in Kubuntu forum..i wanted to place it here first..)

use **AUTOMATIX** to install skype...no headaches and as easy as jelly...

remember to [FONT="Courier New"]sudo apt-get update[/FONT] before using automatix...

to test if it works...
add _echo123_ as a friend and call...follow instructions...and u r all set...

how did it go???

---

### Post by kurokikaze on 2006-01-07
The link is broken. Anyway, as far as I know there's no Automatix for AMD64 Ubuntu, so I don't think I can use it and that's why I've downloaded the tarball.

---

### Post by DimaIL on 2006-01-07
Try to use this:
[http://www.skype.com/products/skype/linux/repositories.html](http://www.skype.com/products/skype/linux/repositories.html)
or [http://klik.atekon.de/](http://klik.atekon.de/)

Dima.

---

### Post by kurokikaze on 2006-01-07
[QUOTE=DimaIL]Try to use this:
[http://www.skype.com/products/skype/linux/repositories.html](http://www.skype.com/products/skype/linux/repositories.html)
or [http://klik.atekon.de/](http://klik.atekon.de/)

Dima.[/QUOTE]

I've tried adding the Skype repositories, but I can't find it. As I said before, there's no 64 bit package yet and that's why I've chosen the tarball.

---

