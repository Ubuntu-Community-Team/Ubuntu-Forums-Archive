---
title: "need help with multiple stuff,cedega,.deb files and more"
date: 2006-08-20
forum: Desktop Environments
---

### Post by aceofskies04@comcast.net on 2006-08-20
Ok heres my situation i need to install ie6 on ubuntu i have wine and everything and when i try to open ie ( after installed) a white box coems up and pretty much nothing happens. So my friend told me to use cedega which has ie6 in it. the problem is that its a .deb file so i need to know how to install the .deb package/file

---

### Post by xtknight on 2006-08-20
$ sudo dpkg -i pkgname.deb

(at the terminal that is)

To use the GUI Gdebi program: To use the graphical user interface, right-click on a '.deb' software package in the file browser and select: Open with 'GDebi Package Installer'.

---

### Post by aceofskies04@comcast.net on 2006-08-20
well i have the package saved to my desktop as cedega_5.0_i386.deb what do i type then

---

### Post by aceofskies04@comcast.net on 2006-08-20
o yeah i opened it with that prgram and it says no despository associtated or something like that

---

### Post by xtknight on 2006-08-20
Goto Applications->Accessories->Terminal.
Now type (this is case sensitive):

[B]cd ~/Desktop
sudo dpkg -i cedega_5.0_i386.deb[/B]

---

### Post by aceofskies04@comcast.net on 2006-08-20
ok ill try that

---

### Post by aceofskies04@comcast.net on 2006-08-21
it says depednecy problems

---

### Post by xtknight on 2006-08-21
Could you post the exact console output result of the dpkg command here?

---

### Post by aceofskies04@comcast.net on 2006-08-21
mitch@mitch-laptop:~$ cd ~/Desktop
mitch@mitch-laptop:~/Desktop$ sudo dpkg -i cedega_5.0_i386.deb
Selecting previously deselected package cedega.
(Reading database ... 79282 files and directories currently installed.)
Unpacking cedega (from cedega_5.0_i386.deb) ...
dpkg: dependency problems prevent configuration of cedega:
 cedega depends on xlibs (>> 4.1.0); however:
  Package xlibs is not installed.
dpkg: error processing cedega (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cedega
mitch@mitch-laptop:~/Desktop$

---

### Post by aceofskies04@comcast.net on 2006-08-21
and?

---

### Post by xtknight on 2006-08-21
> **aceofskies04@comcast.net said:**
> and?

Check out this page: [http://www.chorse.org/archive/2006/05/01/cedega-and-ubuntu-dapper/](http://www.chorse.org/archive/2006/05/01/cedega-and-ubuntu-dapper/)

---

