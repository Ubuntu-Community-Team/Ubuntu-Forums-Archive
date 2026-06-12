---
title: "Counter Strike 2D problems!"
date: 2009-11-17
forum: Gaming &amp; Leisure
---

### Post by tuahaa on 2009-11-17
I've tried to run CS2D on Linux by running the Linux executable (with all the files) but I get this error in terminal:

```
./CounterStrike2D: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

I already have the latest version of libstdc++ installed. I use Karmic Koala. Could this be a bug?

Thanks in advance guys

---

### Post by Perfect Storm on 2009-11-17
You need to install the previous version of libstdc. Find it here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Searcj jaunty for the package as libstdc++5 is obsolete.

---

### Post by tuahaa on 2009-11-17
Thanks! But now I get this error:

```
Graphics Mode Error:
640x480 at 32 bit does not work!
```

I've played this in jaunty but now it won't work in Karmic =(

---

### Post by Perfect Storm on 2009-11-17
See if you can find its config file in your home directory to change the resolution of the game.

---

### Post by tuahaa on 2009-11-17
Thanks, I got it working under 24bit colour! My laptop only has 24 bit colour XD

---

### Post by tommygun01 on 2009-12-12
When my loads ups just in 24 bit with linux files the game freezes when im at the main menu and i click on an option.:(

---

### Post by tuahaa on 2009-12-14
> **tommygun01 said:**
> When my loads ups just in 24 bit with linux files the game freezes when im at the main menu and i click on an option.:(

I might be able to help you. Try running it through terminal and give us the output please.

---

