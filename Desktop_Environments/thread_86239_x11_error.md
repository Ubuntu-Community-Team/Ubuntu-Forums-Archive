---
title: "x11 error?"
date: 2005-11-04
forum: Desktop Environments
---

### Post by not_yet on 2005-11-04
I am trying to compile Fltk

I get the following error 

configure: error: Configure could not find required X11 libraries
./configure: line 8268: exit: aborting.: numeric argument required

:confused:

---

### Post by Ampersand on 2005-11-04
Installing the xlibs-dev package should correct this.

---

### Post by Kyral on 2005-11-04
I'm assuming they you have Breezy. And that FLTK refers to "Fast Light Toolkit".

In that case, let Apt help you.

```
sudo apt-get build-dep fltk1.1
```

This will download all the depends to build fltk.

Now for the next step I reccommend going into a new directory, one that you don't mind nuking when you are done.

```
sudo apt-get source -b fltk1.1
```

This will download the source packages from Apt, unpack them, build them, and spit out the related Debian Packages.

---

### Post by kkiran on 2005-11-19
Hello,
Same problem here. Trying to compile FLTK when I get this error.
Earlier I had to download base development package to make 
configure script run [ it then said gcc can't create executables]
I guess X development libraries/headers are needed for compilation.
If you are able to solve this problem, I request you to either post
to this forum or E-mail me at kuppa under_score kiran at DELETEyahooDOTcom

Thank you,
Kiran Kumar

[QUOTE=not_yet]I am trying to compile Fltk

I get the following error 

configure: error: Configure could not find required X11 libraries
./configure: line 8268: exit: aborting.: numeric argument required

:confused:[/QUOTE]

---

### Post by commodore on 2005-11-21
I have to compile fltk 1.0. I'm not allowed to compile 1.1. But I can't do that. I get this error:
=== making src ===
make[1]: Entering directory `/home/nummer/src/fltk/src'
Compiling Fl.o...
../FL/Fl_Window.H:35: error: ISO C++ forbids declaration of &#8216;Fl_X&#8217; with no type
../FL/Fl_Window.H:35: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
../FL/Fl_Window.H: In member function &#8216;int Fl_Window::shown()&#8217;:
../FL/Fl_Window.H:93: error: &#8216;i&#8217; was not declared in this scope
../FL/x.H: In static member function &#8216;static Fl_X* Fl_X::i(const Fl_Window*)&#8217;:
../FL/x.H:106: error: &#8216;const class Fl_Window&#8217; has no member named &#8216;i&#8217;
../FL/x.H: In member function &#8216;void Fl_X::setwindow(Fl_Window*)&#8217;:
../FL/x.H:107: error: &#8216;class Fl_Window&#8217; has no member named &#8216;i&#8217;
Fl.cxx: In member function &#8216;virtual void Fl_Window::hide()&#8217;:
Fl.cxx:611: error: &#8216;i&#8217; was not declared in this scope
Fl.cxx: In member function &#8216;virtual void Fl_Window::flush()&#8217;:
Fl.cxx:778: error: &#8216;i&#8217; was not declared in this scope
make[1]: *** [Fl.o] Error 1
make[1]: Leaving directory `/home/nummer/src/fltk/src'

---

### Post by commodore on 2005-11-23
Sorry for double-posting, but does anyone know what is the problem? Is there something wrong with the code?

---

### Post by ggankhuy on 2005-11-25
[QUOTE=Kyral]I'm assuming they you have Breezy. And that FLTK refers to "Fast Light Toolkit".

In that case, let Apt help you.

```
sudo apt-get build-dep fltk1.1
```

This will download all the depends to build fltk.

Now for the next step I reccommend going into a new directory, one that you don't mind nuking when you are done.

```
sudo apt-get source -b fltk1.1
```

This will download the source packages from Apt, unpack them, build them, and spit out the related Debian Packages.[/QUOTE]


hi i had same problem when configuring FLTK and  i tried your built but it says :
Reading Package Lists... Done
Building Dependency Tree... Done
E: Unable to find a source package for fltk1.1.6
can u give me some hint>? Thansk!

---

