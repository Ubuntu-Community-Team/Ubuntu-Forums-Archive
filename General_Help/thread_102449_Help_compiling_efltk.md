---
title: "Help compiling efltk"
date: 2005-12-12
forum: General Help
---

### Post by kubark42 on 2005-12-12
Hi, I'm a new convert to Kubuntu (installed it last night) and am trying to compile efltk on my Dell Optiplex GX620 in order to run RTAI (a linux real-time application interface). However, I'm getting errors compiling efltk that I don't get when under gentoo. I've tried gcc 3.3, 3.4, and 4.0, to no avail.

Here are the errors:

[SIZE="1"]
Compiling Fl.cpp...
/usr/src/efltk/efltk/Fl_Boxtype.h:30: warning: ‘class Fl_Boxtype_’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:60: warning: ‘class Fl_Frame_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:99: warning: ‘class Fl_Flat_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:108: warning: ‘class Fl_Highlight_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:126: warning: ‘class Fl_Round_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:140: warning: ‘class Fl_Diamond_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:154: warning: ‘class Fl_Plastic_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:168: warning: ‘class Fl_No_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:177: warning: ‘class Fl_Shadow_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:186: warning: ‘class Fl_Rounded_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:195: warning: ‘class Fl_RShadow_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:204: warning: ‘class Fl_RFlat_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:213: warning: ‘class Fl_Oval_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:222: warning: ‘class Fl_Oval_Shadow_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:230: warning: ‘class Fl_Oval_Flat_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:239: warning: ‘class Fl_Border_Frame’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:248: warning: ‘class Fl_Dotted_Frame’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:257: warning: ‘class Fl_Hor_Shade_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Boxtype.h:267: warning: ‘class Fl_Vert_Shade_Box’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Labeltype.h:29: warning: ‘class Fl_Labeltype_’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Labeltype.h:46: warning: ‘class Fl_No_Label’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Labeltype.h:54: warning: ‘class Fl_Symbol_Label’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Labeltype.h:62: warning: ‘class Fl_Engraved_Label’ has virtual functions but non-virtual destructor
/usr/src/efltk/efltk/Fl_Window.h:130: error: ISO C++ forbids declaration of ‘Fl_X’ with no type
/usr/src/efltk/efltk/Fl_Window.h:130: error: expected ‘;’ before ‘*’ token
/usr/src/efltk/efltk/Fl_Window.h: In member function ‘bool Fl_Window::shown() const’:
/usr/src/efltk/efltk/Fl_Window.h:80: error: ‘i’ was not declared in this scope
/usr/src/efltk/efltk/x.h: In static member function ‘static Fl_X* Fl_X::i(const Fl_Window*)’:
/usr/src/efltk/efltk/x.h:207: error: ‘const class Fl_Window’ has no member named ‘i’
Fl_x.cpp: In member function ‘virtual void Fl_Window::layout()’:
Fl_x.cpp:1357: error: ‘i’ was not declared in this scope
Fl_x.cpp: In static member function ‘static void Fl_X::create(Fl_Window*, XVisualInfo*, Colormap, int)’:
Fl_x.cpp:1422: error: ‘class Fl_Window’ has no member named ‘i’
Fl_x.cpp:1465: error: ‘class Fl_Window’ has no member named ‘i’
Fl_x.cpp:1499: error: ‘const class Fl_Window’ has no member named ‘i’
Fl_x.cpp: In member function ‘void Fl_Window::size_range_()’:
Fl_x.cpp:1600: error: ‘i’ was not declared in this scope
Fl_x.cpp: In member function ‘bool Fl_Window::iconic() const’:
Fl_x.cpp:1606: error: ‘i’ was not declared in this scope
Fl_x.cpp: In member function ‘void Fl_Window::label(const Fl_String&, const Fl_String&)’:
Fl_x.cpp:1623: error: ‘i’ was not declared in this scope
Fl_x.cpp: In member function ‘void Fl_Window::make_current() const’:
Fl_x.cpp:1652: error: ‘i’ was not declared in this scope
make[2]: *** [Fl.shared.o] Error 1
make[2]: Leaving directory `/usr/src/efltk/src/core'
make[1]: *** [shared] Error 2
make[1]: Leaving directory `/usr/src/efltk/src'
make: *** [all] Error 2
[/SIZE]

I do realize that normally for this kind of error I should go to the efltk developers, but since it only occurs under Ubuntu, I'm thinking that this is Ubuntu related and I'm not really familiar with the system, so I don't have the first clue about how to troubleshoot it.

Anyone know anything?

---

### Post by daller on 2005-12-12
I don't use that app myself, but try installing "g++"

---

### Post by kubark42 on 2005-12-12
I checked and I've already got g++ installed. Dang. I was hoping that that might be a magic bullet.

Unfortunately, I *must* use efltk for RTAI, no two ways around it. Any other suggestions? Does anyone even understand what the error means and why I'm not getting it under gentoo? Could i even compile efltk under gentoo and then copy it to ubuntu?

---

### Post by Zaventh on 2005-12-12
are you using gnumake?

---

### Post by kubark42 on 2005-12-13
Umm... Is "I don't know" a valid response?

In fact, I checked in Adept and there's no gnumake package, so I don't really know. I simply downloaded the sources, type ./configure, which worked just fine, and then ./emake, which fails after several seconds, but only on Ubuntu.

This is happening to me on both Ubuntu machines, a Dell GX620 and a Dell GX240. Can someone else download the sources and verify? Perhaps this is a bug in the Ubuntu compiler.

---

