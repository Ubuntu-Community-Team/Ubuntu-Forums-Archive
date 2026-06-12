---
title: "HOW TO: Installing libpst"
date: 2005-12-07
forum: General Help
---

### Post by filipenetto on 2005-12-07
Hi people,

Somebody know how to install the libpst package ? I have downloaded this files (attachment), but, how I'm a newbie user, don't know how to install ... :neutral: 

So, somebody can help me ?

Thanks so much ... :)

---

### Post by Joe_CoT on 2005-12-07
wow, i looked online to find a deb package, but there really isn't one
from the console, type:
```
sudo apt-get install build-essential checkinstall
```

after that's done, in the directory of the source code you downloaded:
```
./configure
make
sudo checkinstall
```

that will compile the code for you, make it into a deb package, and install the package for you. that way you can uninstall it in synaptic later if you need to.

---

### Post by filipenetto on 2005-12-07
Hi Bob, 

I do it. The first step is ok (build-essential checkinstall), but, when I'm gone to the libpst directory, and type ./configure, I have an error (screenshot). Do you know why ?

Tks ! ;)

---

### Post by Joe_CoT on 2005-12-07
uh, not really. could you perhaps translate into a language i understand? :)

---

### Post by GameGod on 2005-12-07
Looks like you don't have to run "./configure" for this library...

Just do:
make
sudo checkinstall

---

### Post by Joe_CoT on 2005-12-07
the source code doesn't compile:
```
joe@jpt8:~/Desktop/libpst_0.3.4$ make
gcc -c -Wall -Werror libpst.c -g -o libpst.o
cc1: warnings being treated as errors
libpst.c: In function ‘_pst_read_block_size’:
libpst.c:2468: warning: pointer targets in passing argument 1 of ‘_pst_decrypt’ differ in signedness
make: *** [libpst.o] Error 1
```

i assume this doesn't screw up the program any, otherwise they wouldn't have released it. anyone know how to turn off the "warnings being treated as errors" thing?

---

### Post by Joe_CoT on 2005-12-07
i edited the code in libpst.c to fix the error. fixed version is attached.

*edit*
good god. apparently this guy stopped working on the library, and it's being maintained somewhere else.
[http://alioth.debian.org/projects/libpst/](http://alioth.debian.org/projects/libpst/)
this version works just fine.

---

### Post by filipenetto on 2005-12-07
So, 

bobfnordman help-me to resolve the problem: he found the 0.5 version of libpst, and its work ... with 'readpst' command, I can convert the messages of Outlook to Evolution.

Thank you everybody .... !!! :D

---

