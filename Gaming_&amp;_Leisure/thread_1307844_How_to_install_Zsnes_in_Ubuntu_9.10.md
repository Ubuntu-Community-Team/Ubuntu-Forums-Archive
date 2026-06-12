---
title: "How to install Zsnes in Ubuntu 9.10?"
date: 2009-10-31
forum: Gaming &amp; Leisure
---

### Post by jahgamer189x on 2009-10-31
How do I install it? I found it in Ubuntu Software Center but there is no option to install it. Please help!

---

### Post by jpmelos on 2009-10-31
I couldn't find ZSNES in the repositories, so I guess it's not in Karmic anymore. But I did find another SNES emulator, called SNES9x. You may want to give it a shot. You can install it by doing

```
sudo apt-get install snes9express
```

Hope I could help, anyways!

---

### Post by jahgamer189x on 2009-10-31
snes9x doesn't work well for me and doesn't have the options zsnes has. But thanks anyway!

EDIT: I guess I'll just have to go back to Ubuntu 9.04...

---

### Post by tkmn on 2009-10-31
Looks like zsnes is missing..

I suggest you take a look a snes9x-gtk.

[https://launchpad.net/~bearoso/+archive/ppa](https://launchpad.net/~bearoso/+archive/ppa)


Just add this line to software sources: *ppa:bearoso/ppa*


I had some issues with sound, so I changed driver to SDL and increased the buffer to 128 ms, that seems to have fixed it.

---

### Post by donkyhotay on 2009-10-31
zsnes is in karmic's new ubuntu software center (what used to be add/remove programs) however it won't install that way on 64bit systems.

---

### Post by Mike'sHardLinux on 2009-10-31
I downloaded the 32-bit package for Jaunty, and the installed it with 
```

sudo dpkg -i --force-architecture zsnes_1.510-2.2ubuntu2_i386.deb

```

Then, to execute it, I use
```

zsnes -ad sdl

```

---

### Post by jahgamer189x on 2009-10-31
Thanks Mike'sHardLinux, that worked fine!

---

### Post by jpmelos on 2009-10-31
Just one question... I thought 64-bit hardware is 32-bit compatible, but seems like the software that only have 32-bit architecture won't appear on the repositories of Ubuntu 64-bit? Why is that? Because they run if we force install, right?

---

### Post by dfreer on 2009-10-31
> **jpmelos said:**
> Just one question... I thought 64-bit hardware is 32-bit compatible, but seems like the software that only have 32-bit architecture won't appear on the repositories of Ubuntu 64-bit? Why is that? Because they run if we force install, right?

It's not really the best way to install software using force install, in some cases (zsnes) it works ok.

As simply as possible, the reason why is that debian/ubuntu has yet to fully implement multi-arch support, which ideally would let an user decide which version of the software they want to install on their system.

About ZSNES specifically, almost every library needed to run the ubuntu configured binary is provided by ia32-libs package. Hence a simple force-install will work. Other binaries that have libao enabled will need a 32-bit version of it correctly installed and syslinked, otherwise it will segfault.

---

### Post by LordVeovis on 2010-03-30
found this while searching
```

wget http://mirrors.kernel.org/ubuntu/pool/universe/z/zsnes/zsnes_1.510-2.1ubuntu1.1_amd64.deb
sudo dpkg -i zsnes_1.510-2.1ubuntu1.1_amd64.deb

```

---

