---
title: "gnome-screensaver - make your own"
date: 2011-01-21
forum: Desktop Environments
---

### Post by ankillito on 2011-01-21
I have been working on making my own screensaver.  Ubuntu uses gnome-screensaver, but there seems to be absolutely no information online about how to write a screensaver compatible with gnome-screensaver.  Last year, I made a bunch of progress, figured it out, and I was going to post a tutorial. There still aren't any tutorials out there, so I thought I'd post how I made a screensaver.  It's not a full tutorial, but it's better than nothing.  Below you should find instructions to download, compile, and install a simple, commented screensaver that uses OpenGL to show a rectangle that changes color.

For a program to be run by gnome-screensaver, it must use a gs-theme-window. To use this window, you will need the files:[gs-theme-window.c]("http://gnome-screensaver.sourcearchive.com/documentation/2.30.0-1ubuntu1/gs-theme-window_8c-source.html") [gs-theme-window.h]("http://gnome-screensaver.sourcearchive.com/documentation/2.30.0-1ubuntu1/gste-slideshow_8h-source.html") (also in attached tar)

You'll also need the gtk libraries installed, libgtk2.0-dev libgtkglext1-dev. The second one is an OpenGL extension for Gtk.
```
sudo apt-get install libgtk2.0-dev libgtkglext1-dev
```

Download the sample files, and extract them, and try to compile.
```

tar -zxf sample_screensave.tar.gz
cd screensaver
make

```

It should compile with one warning, though I have not throughly tested. Let me know if it doesn't work for you, and I'll try to help.  

Try running it, just to be sure it works
```
./your_screensaver
```

The code is fairly straightforward and well commented, so you should easily be able to hack it to do what you want. Now to get gnome-screensaver to use it.

You must put the screensaver into the location gnome-screensaver can run it from. Find the directory with:
```
pkg-config --variable=privlibexecdir gnome-screensaver
```

Copy the program into that directory. Then edit the your_screensaver.desktop file and ensure that it is referring to the location you just put the screensaver in.  Then **copy** the desktop file into the location given by
```
pkg-config --variable=themesdir gnome-screensaver

```

Theoretically, you should now be able to choose your screensaver:
```
gnome-screensaver-preferences
```

However, it doesn't show up for me.  That's where you are **supposed** to put the file from what I can tell, but it doesn't show up as an option until I put the .desktop file in:
```
~/.local/share/applications/screensavers/
```

I have no idea why, but if you put the desktop file there, you should be able to use your new screensaver.  Happy Hacking, and I'll try to answer any question you post.  Also, if anyone *does* know of a tutorial, please say so!

---

### Post by ..k1.. on 2011-05-01
=D>

Thank YOU! 

i searched in web 6 or 7 hours and find nothing ...

Now i have build my first Screensaver,

ugly but running :D

---

### Post by ankillito on 2011-05-01
Glad to hear it!

Also, for anyone else coming across this, please go to the other thread at [http://ubuntuforums.org/showthread.php?t=1583335]("http://ubuntuforums.org/showthread.php?t=1583335") I apologise greatly for double posting, but I thought my first post hadn't gone through. :oops:

---

### Post by ..k1.. on 2011-05-03
> **ankillito said:**
> Glad to hear it!

Also, for anyone else coming across this, please go to the other thread at [http://ubuntuforums.org/showthread.php?t=1583335](http://ubuntuforums.org/showthread.php?t=1583335) I apologise greatly for double posting, but I thought my first post hadn't gone through. :oops:


LOL 

I found this tread before I landed here, and I think this tread here is eseay to understand and more clear and simple ^^

 the only thing missing now is a useful opengl tutorial linked, but i'm working on it::D

---

### Post by ankillito on 2011-05-03
I think I started learning OpenGL with [NeHe's tutorials]("http://nehe.gamedev.net/"). Not mindbogglingly great, but I found them very useful.

---

