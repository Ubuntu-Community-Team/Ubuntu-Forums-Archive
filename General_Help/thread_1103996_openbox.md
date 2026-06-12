---
title: "openbox"
date: 2009-03-23
forum: General Help
---

### Post by theozzlives on 2009-03-23
I tried to compile openbox on my test machine for something to do (I'm disabled and bored). It said it couldn't find the make file after I did ./configure. This was the "stable" version. I did ./configure, then make and thats as far as I got. Any input?

Oh! I haven't put build-essential on it yet, would that be it?

---

### Post by rendon on 2009-03-23
Sounds like you're doing the right thing for a traditional linux package, is there a REAME with particular installation info for this package?  These days it tends to be a little different for each package...

---

### Post by theozzlives on 2009-03-23
That's what it says to do, the error is:

checking for t_open in -lnsl... no
checking for socket in -lsocket... no
checking for X... no
configure: error: Openbox requires the X Window System libraries and headers.
ozzie@ozzie-tower:~/openbox-2.2.3$ make
make: *** No targets specified and no makefile found.  Stop.

---

### Post by skymera on 2009-03-23
Openbox is in the Ubuntu repos.

---

### Post by theozzlives on 2009-03-23
I looked in Add/Remove, I guess I'll try Synaptic.

---

### Post by skymera on 2009-03-23
or you could just sudo apt-get ..

---

### Post by theozzlives on 2009-03-25
Well I installed openbox on my test computer through synaptic and when I tried to boot the session I got an error saying my session lasted 10 seconds and I was out of disk space. My test computer has 15 GB free.

So I installed it on my laptop that has 90 GB free, same thing. What am I doing wrong?

---

