---
title: "tomenet"
date: 2007-03-31
forum: Gaming &amp; Leisure
---

### Post by dcherryholmes on 2007-03-31
Does anyone know what packages I need to have installed in order to get tomenet to compile?  The installation instructions simply say:

Go into '/tomenet/src' where the file 'makefile' is located.
Make sure you have X11, ncurses, ncurses-devel and crypt libraries installed.
Enter these two lines:
        make clean
        make tomenet
and the binary 'tomenet' will be created in this folder 'tomenet/src'.

I did some apt-cache searching, but there is a lot of output, and installed libncurses5-dev, but that does not seem to be sufficient.

---

### Post by richieboy on 2007-06-01
i got it working and it's great.  what error messages do you get?  maybe i can help some.
rich

---

