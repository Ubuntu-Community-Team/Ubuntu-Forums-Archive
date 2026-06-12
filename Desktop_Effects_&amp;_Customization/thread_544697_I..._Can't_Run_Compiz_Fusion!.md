---
title: "I... Can't Run Compiz Fusion?!"
date: 2007-09-06
forum: Desktop Effects &amp; Customization
---

### Post by CLUGENHEIM on 2007-09-06
I installed Compiz, and when I went to run it in the
 terminal, it gave me this error:

caleb@Caleb:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

So I checked my gfx card, and checked for an updated driver:

caleb@Caleb:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
caleb@Caleb:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xorg-driver-fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Did I do all of this wrong or what? Or does my gfx card simply not gonna work with it? D=

---

### Post by CLUGENHEIM on 2007-09-06
Bump...

Ok I used [this]("http://ubuntu1501.blogspot.com/2007/08/compiz-fusion-in-fiesty-with-xgl.html") guide and set up xgl.

It says to "log in to my xgl session." how do I do that? >_<

---

### Post by CLUGENHEIM on 2007-09-06
Sorry... *another bump*

I figured out how you do that, but on the log in screen, I see no "user options" button or anything. Do I have to activate it somehow? Or do I access it some other way? :confused:

---

