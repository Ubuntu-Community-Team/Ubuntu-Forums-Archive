---
title: "installing brewtarget on ubuntu 64 bit 10.10"
date: 2010-12-21
forum: Gaming &amp; Leisure
---

### Post by HH60Gunner on 2010-12-21
Ok, 

So I'm no linux wizard but I'm learning as I go along. I'm trying to install brewtarget but just can't seem to. I tried the deb package but it won't work on my 64 bit ubuntu. So I tried compiling the source (still new to that). Here's where I'm stuck.

So I run the ./configure and I get

---Configure script for Brewtarget.
OS: Linux...yay!
/usr/bin/qmake brewtarget.pro

You are now ready to run "/usr/bin/make" then "/usr/bin/make install".

So I type sudo /usr/bin/make and get this 

enderusaf@GeekBox:~/Downloads/temp/brewtarget-1.2$ sudo /usr/bin/make
/usr/bin/uic-qt4 ui/aboutDialog.ui -o src/ui_aboutDialog.h
make: /usr/bin/uic-qt4: Command not found
make: *** [src/ui_aboutDialog.h] Error 127



What am I doing wrong?

if I use /usr/bin/qmake the command enters and gives me another prompt.

when I type enderusaf@GeekBox:~/Downloads/temp/brewtarget-1.2$ sudo /usr/bin/qmake install
Cannot find file: install.



What am I doing wrong?

---

