---
title: "don't see visualboyadvance app in Ubuntu menu."
date: 2005-10-28
forum: Desktop Environments
---

### Post by kazuya on 2005-10-28
I installed visualboyadvance via synaptic as well as gnuboy, the problem is that I do not see the emulator or stuff in my menu or games applications. How do I set this up such that I launch this visualboyadvance app in Ubuntu app menu?

---

### Post by KingBahamut on 2005-10-28
just use the menu editor , smeg, to add the appropriate entries into your apps list. 

Applications > System Tools > Menu editor

---

### Post by SilentCacophony on 2005-10-28
Hi. I don't know about gnuboy, but I remember visualboyadvance as being a commandline application, which requires the filename of the rom to follow the executable name. Look for it in the /usr/bin folder to see the exact name (I think 'vba' and 'visualboyadvance' both work, but not sure.)

Once you know the executable filename, you can enter 'man visualboyadvance' (or whatever the name is) in a terminal to read about how it works, or look in /usr/share/doc for a directory named as such, which will contain docs for it.

One way you can make it easier to use is to use nautilus to navigate to the roms folder, and right-click on one, then select 'open with', and set it to use visualboyadvance, which will associate it with those files.

---

### Post by manu59240 on 2005-11-07
Here is a front end for GBA:

[IMG]http://vbaexpress.tuxfamily.org/capture_fr_affichage.jpg[/IMG]

[http://vbaexpress.tuxfamily.org/english.php]("http://vbaexpress.tuxfamily.org/english.php")

what you need to compile (synaptic):

    * libfltk -dev
    * libxpm-dev
    * libsdl1.2
    * virtualboyadvance

then: add FLTK Utility Widgets: [http://www.osc.edu/~jbryan/FLU/](http://www.osc.edu/~jbryan/FLU/)

```
$ wget http://www.osc.edu/~jbryan/FLU/FLU_2.14.tar.gz
$ tar xvzf FLU_2.14.tar.gz
$ cd FLU_2.14
$ ./configure
$ make
$ sudo make install
```

then install VBAExpress:

```
$ cd ~   
$ wget http://vbaexpress.tuxfamily.org/vbaexpress-1.1.tar.gz
$ tar xvzf vbaexpress-1.1.tar.gz
$ cd vbaexpress-1.1
$ make
$ sudo make install
```

then edit the apps' menu:

/usr/bin/vbaexpress (launcher)
/usr/share/pixmaps/vbaexpress.png (img)


a french guy.
If you want help, I know that the developer of this application will help you.

---

### Post by ikki_72 on 2006-01-04
that happened to my znes too, but i found it out in bin folder, double click n play.

---

