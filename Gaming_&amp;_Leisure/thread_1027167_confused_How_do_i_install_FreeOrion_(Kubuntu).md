---
title: "confused: How do i install FreeOrion? (Kubuntu)"
date: 2009-01-01
forum: Gaming &amp; Leisure
---

### Post by Firestem4 on 2009-01-01
Hi, I'm new to Linux (i'm running Kubuntu 8.10), and I was hoping someone here would be able to explain to me how to download and install FreeOrion.

http://www.freeorion.org/index.php/Main_Page

One way is to compile freeorion which they include a shell command for it, although I am slightly confused on what i need to compile it. They mention something about GCC 4.x+ (which i read is a C++), Also i need OpenGL 1.5 and i can't figure out what version i have (or what version is with 8.10 by default).

They also have a tar.zip with a script installer. I was looking at it earlier but I couldn't get it to work properly. I think I was missing dome dependancies.
http://www.freeorion.org/forum/viewtopic.php?f=9&t=1792 (<--statically linked binaries)

I am also having a tearing and flickering problem (Intel 915m). I found a fix online which said to disable "Detecing RANDR(monitor) changes. Which got rid of the flickering but sometimems when i open/close windows, or have thumbnails appear i get tearing. (or even drop down menus).

Any help would be greatly appreciated.

---

### Post by Perfect Storm on 2009-01-01
Compiling FreeOrion might be a little tricky/advanced if you're a new to linux.

> They mention something about GCC 4.x+
It's the compiler (GNU C Compiler).
To compile or build stuff from source you need the standard compiling stuff, you get it by installing **build-essential**
```
sudo apt-get install build-essential
```

> Also i need OpenGL 1.5 and i can't figure out what version i have (or what version is with 8.10 by default).
Your Intel card supports up to OpenGL1.5 so it should be good (but slow), to install the required headers and -devs to compile with them you need;
```
sudo apt-get install libgl1-mesa-dev libglu1-mesa-dev
```


The other question about flickering intel stuff, make another thread for that.

---

