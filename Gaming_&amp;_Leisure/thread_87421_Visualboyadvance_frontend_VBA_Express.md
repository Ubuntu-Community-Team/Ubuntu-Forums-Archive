---
title: "Visualboyadvance frontend: VBA Express"
date: 2005-11-08
forum: Gaming &amp; Leisure
---

### Post by manu59240 on 2005-11-08
Here is a front end for VBA:

[IMG]http://vbaexpress.tuxfamily.org/capture_fr_affichage.jpg[/IMG]

It's easy to install, you won't spend time anymore writing in the terminal.

[http://vbaexpress.tuxfamily.org/english.php]("http://vbaexpress.tuxfamily.org/english.php")

what you need to compile (synaptic):

    * libfltk **-dev
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
$ mkdir ~/.vba
```

then edit the apps' menu:

/usr/bin/vbaexpress (launcher)
/usr/share/pixmaps/vbaexpress.png (img)

Then launch VBA Express, configure with your joystick or keyboard, give the path for save_state, screeshoots... (/home/login/.vba). try some video adjustments and play


Manu (a french guy.)

If you want help, I know that the developer of this application will help you.
If someone think It would be great to find this apps in synaptic, I know that the developper is thinking about installing ubuntu and creating ***.deb package. If someone want to help, He will be pleased-> email him.

---

### Post by slipk487 on 2006-04-02
i cant get it to work it cant do the make commands

---

### Post by Perfect Storm on 2006-04-02
Make sure you have the basics compile tool install first: 
```
sudo apt-get install build-essential
```

---

### Post by Morbett on 2006-04-08
I'm getting this error, even though I have the packages Libfltk1.1, Libfltk1.1-dbg and Libfltk1.1-dev (all version 1.1.6-6) installed:


> Checking for required libs...
  FL/Fl.H
  GL/gl.h
  GL/glu.h
  libfltk
Cannot find required lib 'libfltk'. Perhaps you are missing the library
or it is installed in a nonstandard location.
Either install the necessary library, or if it is installed in a nonstandard
location use the "--L=DIR" option.
If this is an FLTK lib, use the "--fltk=DIR" option.
  libfltk_gl
Cannot find required lib 'libfltk_gl'. Perhaps you are missing the library
or it is installed in a nonstandard location.
Either install the necessary library, or if it is installed in a nonstandard
location use the "--L=DIR" option.
If this is an FLTK lib, use the "--fltk=DIR" option.
  libGL
Cannot find required lib 'libGL'. Perhaps you are missing the library
or it is installed in a nonstandard location.
Either install the necessary library, or if it is installed in a nonstandard
location use the "--L=DIR" option.
If this is an FLTK lib, use the "--fltk=DIR" option.
  libGLU
Cannot find required lib 'libGLU'. Perhaps you are missing the library
or it is installed in a nonstandard location.
Either install the necessary library, or if it is installed in a nonstandard
location use the "--L=DIR" option.
If this is an FLTK lib, use the "--fltk=DIR" option.


---

### Post by harrypotter123 on 2010-04-07
I did all that, but when I open a game in VBA Express, it does nothing. It just says "99%" or some other percentage. What do I do?

And when you say 
"edit the usr/bin/vbaexpress
and
usr/bin/pixmaps/vbaexpress.png" ?
Please reply soon..........

---

### Post by Satoyaki on 2012-02-05
I have it installed but i cant get the buttons to work. when i press down on my controller it does screen capture.

---

### Post by uRock on 2012-02-05
This thread is more than 5 years old. Please start a new thread with your issue.

---

