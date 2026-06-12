---
title: "Compiling Octave 3.2 on Jaunty"
date: 2009-08-05
forum: Education &amp; Science
---

### Post by gab10 on 2009-08-05
Has anybody had success compiling Octave 3.2 on Jaunty? My latest error during make is

./DLD-FUNCTIONS/fltk_backend.cc: In member function ‘virtual void OpenGL_fltk::draw_overlay()’:
./DLD-FUNCTIONS/fltk_backend.cc:145: error: ‘gluOrtho2D’ was not declared in this scope
make[2]: *** [pic/fltk_backend.o] Error 1
make[2]: Leaving directory `/usr/local/src/octave-3.2.2/src'
make[1]: *** [src] Error 2
make[1]: Leaving directory `/usr/local/src/octave-3.2.2'
make: *** [all] Error 2

I would greatly appreciate any advice anybody could offer.

---

### Post by ahmatti on 2009-08-05
Did you get any errors during configure? Do you have libftlkx.x-dev installed? Make errors are often due to missing depencies, alhtough you should see an error about missing fltk libraries also during configure. I'm compiling it on my Hardy computer to see how it goes, I'll try it also on Jaunty at home if find time, compiling Octave takes a bit of time...

---

### Post by gab10 on 2009-08-06
Thanks for replying.

I do have libfltk1.1-dev installed.

There are no errors during configure, just these warnings:

configure: WARNING: cannot determine how to obtain linking information from f77
configure: WARNING: qrupdate not found. The QR & Cholesky updating functions will be slow.
configure: WARNING: qrupdate not found. The QR & Cholesky updating functions will be slow.
configure: WARNING: GraphicsMagick++ config script not found.  Assuming GraphicsMagic++ library and header files are missing, so imread will not be fully functional

---

### Post by ahmatti on 2009-08-07
OK,
I Octave compiled and installed fine on my Hardy machine, but I get the same errors as you did with Jaunty. I don't have time to debug in Jaunty right now, but I actually noticed that I didn't have libfltk1.1-dev installed on Hardy and errors seem to related to it. Another difference is that Hardy has gcc-4.2 and Jaunty gcc-4.3

 So what I'm going to try next (in the following order)  and what might also help you is:

[LIST]
* Try to compile with gcc-4.2 
* Disable fltk which seems to be causing the errors with ./without-framework-opengl
* Remove libfltk-dev and try again
[/LIST]

The last two options are of course bad if your reason for compiling Octave is to try out the new FLTK based plotting system, I'm not quite sure what else uses but I never had the need for it.

Note that sometimes it is a good idea to get a fresh start after you run into compile errors, so extract the source form archive again after you run into errors.

---

### Post by gab10 on 2009-08-07
Thanks to some help from the Octave mailing list I was able to resolve this. I ended up doing:

sudo apt-get build-dep octave3.0
sudo apt-get install libftgl-dev

and configuring with:

sudo ./configure prefix=/usr/local/octave3p2 --with-g77=gfortrain --without-qrupdate

The build went fine and everything is working great now.

---

