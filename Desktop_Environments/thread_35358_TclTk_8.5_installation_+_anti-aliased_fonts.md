---
title: "Tcl/Tk 8.5 installation + anti-aliased fonts"
date: 2005-05-18
forum: Desktop Environments
---

### Post by slyhne on 2005-05-18
Hi

First post, so be gentle  ;-) 

The problem.

I want to run a TCL/TK applikation (aMSN), but fonts are so ugly.
Solution found on aMSN's Wiki was to download TCL/TK version 8.5a and compile from source, TCL was compiled with no special options:

./configure --prefix=/usr; make; make install

TK should then be compiled this way:

./configure --prefix=/usr --enable-xft; make; make install

or if that didn't work, then like this:

./configure --prefix=/usr --enable-xft2; make; make install

I tried both and when I call the application with "wish8.5 amsn" it didn't work, fonts still look jagged and ugly.

I have done this under SuSE 9.2 with no problems, so is this a special Ubuntu 5.04 issue?

Can anyone here help out?

Regards

slyhne

---

### Post by jcooper on 2005-05-19
Is aMSN using the newly compiled version? I don't have any experience with the app, so can't provide any in depth info.

Did you run sudo make install to install the newly compiled version?

---

### Post by slyhne on 2005-05-19
Hi jcooper

Actually I did do the "make install" with sudo, my fault I didn't get that right in my post.

and I do call the application with "wish8.5 amsn" and that should be it - it worked under SuSE 9.2.

Anyone using aMSN here?

I'm just wery curios about the MSN webcam-support they have built in this application.

slyhne

---

### Post by slyhne on 2005-08-17
I can now answer my own question.

I had to remove the TCL and TK packages provided by Ubuntu (this removes xchat as well, but I don't use that...).
Then I downloaded and extracted TCL and TK (version 8.5.3) and installed it:

cd to the correct TCL directory (unix)
TCL should then be compiled this way:

./configure --prefix=/usr
make
sudo make install

cd to the correct TK directory (unix)
TK should then be compiled this way:

./configure --prefix=/usr --enable-xft
make
sudo make install

Now go to aMSN's homepage and download the CVS version.
Extract that and run:

./configure
make

in the msn directory

Now you have smooth fonts AND webcam support.
I have tested it against MSN Messenger, and it works great   \\:D/ 


Søren

---

### Post by e4m on 2006-05-10
hi ,
this version tc/tk 8.5a3 will cause much of problem with amsn interface (like dialog .. send file for example). AMSN developers team say me to switch at 8.5 CVS version becouse the bug was...

---

