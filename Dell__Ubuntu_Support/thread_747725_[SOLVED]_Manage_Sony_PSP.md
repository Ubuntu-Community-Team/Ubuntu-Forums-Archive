---
title: "[SOLVED] Manage Sony PSP?"
date: 2008-04-06
forum: Dell  Ubuntu Support
---

### Post by slugicide on 2008-04-06
I wanted to install qPSP Manager, as [described here,]("https://help.ubuntu.com/community/PSP") but the instructions don't work.  I think they are out-of-date.  pspvc (PSP video converter) compiled and installed, but not so for the manager--which is kind of a bummer, since [they say]("http://qpspmanager.sourceforge.net/") the new version has video conversion built-in.
I would appreciate any help.  Perhaps someone could just update the wiki?  Thanks in advance.

Update:
I changed the command to qmake-qt4 and went through the steps as described on the wiki.  It did, then, create a binary which I was able to copy into /usr/local/bin and then create a working launcher.  I haven't used it yet, so don't know how it works.

---

### Post by slugicide on 2008-04-07
Any takers?

---

### Post by zeronothing on 2008-04-07
what part are you stuck on. you have to configure, make and install. I have it working, but the video convertion sucks. I could never get it to work right

---

### Post by slugicide on 2008-04-07
I'm stuck at the "qmake" part.  I believe I've done right by upgrading to QT 4, as was suggested in another thread, and as the app's site says all code was "migrated to version 4."  
Here's my problem:  when I "qmake" inside the src folder nothing happens.  When I "qmake" in the folder containing src it creates files which give me errors when I try and "make" them.  
I'd never heard of qmake before, actually (which lets you know how newbish I am).  Are the steps in the wiki wrong?

---

### Post by zeronothing on 2008-04-07
yea, give me a moment I have to log into my machine. I'm actually in graduate class right now. The class is really boring.

---

### Post by zeronothing on 2008-04-07
try this, open up terminal and execute this in terminal:

sudo apt-get install qt4-designer qt4-dev-tools build-essential

this will install all of the nessesary programs to compile the program. next we need to compile the program. open up terminal and change directory into the root of the qpspmanager folder. execute this in terminal:

qmake-qt4

next do this in terminal

make

finally do this in terminal

sudo make install

at this point it will probably fail or error out. this is ok, next do a ls command in terminal and you should find a folder called bin. next change directory into that folder and you should find a executable called QPSPmanager. now do this command in terminal:

sudo cp QPSPmanager /usr/bin/

this will copy the executable to the /usr/bin directory where a lot of executes are held.

then from terminal execute this:

gksu QPSPmanager

hopefully this will work for you

---

