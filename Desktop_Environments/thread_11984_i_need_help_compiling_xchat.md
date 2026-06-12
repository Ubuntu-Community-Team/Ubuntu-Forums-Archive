---
title: "i need help compiling xchat"
date: 2005-01-20
forum: Desktop Environments
---

### Post by akurashy on 2005-01-20
I downloaded the new sources of xchat but can someone help me how to compile it and install it :(

---

### Post by Quest-Master on 2005-01-20
Just do this in the terminal.

sudo apt-get install xchat

---

### Post by akurashy on 2005-01-20
didnt work..
im still stuck with 2.0.8

and i want to install the latest one :(

---

### Post by DJ_Max on 2005-01-20
[http://www.xchat.org/compiling/](http://www.xchat.org/compiling/)
Of course, replace x's with correct numbers.
On step #4. Do
```
sudo make install
```

Do not do what it says on step 4. Do what I provided.

---

### Post by akurashy on 2005-01-20
checking for GLIB - version >= 2.0.3... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: "Cannot find glib"


i did that over and over and i get that that error :(

---

### Post by DJ_Max on 2005-01-20
Either you don't have the Glib installed, or an old version.

Do
```
sudo apt-get install libglib2.0-0 
```

---

### Post by akurashy on 2005-01-20
well it is installed :(
i dont know what wrong with it :(

---

### Post by akurashy on 2005-01-20
i just saw the problem
i think i need to get a newest version of GLIB
how to update it then?

---

### Post by Pluk on 2005-01-21
dont you just need the development files of glib2?

sudo apt-get install libglib2.0-dev

---

### Post by akurashy on 2005-01-21
nevermind i guess
i found a post in HOW-TO forums to update to xchat and the latest gaim version and firefox i guess

---

