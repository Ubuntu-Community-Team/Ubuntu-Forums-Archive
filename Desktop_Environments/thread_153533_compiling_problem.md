---
title: "compiling problem"
date: 2006-04-01
forum: Desktop Environments
---

### Post by garethppls on 2006-04-01
evlj56.o ./obj/gdevpxut.o ./obj/gdevpcl.o
make: *** No rule to make target `obj/cdeskjet.dev', needed by `obj/ld.tr'.  Stop.


problem during compiling... can anyone tell me what to do to stop it stopping here

---

### Post by dermotti on 2006-04-01
What are you compiling?

---

### Post by garethppls on 2006-04-01
[QUOTE=dermotti]What are you compiling?[/QUOTE]
ghostscript 8.53 to get my printer working

---

### Post by Sef on 2006-04-01
Did you download build-essential? If not, you can't compile.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by garethppls on 2006-04-01
yes I did that, I did ./configure and then make install but it stops in the middle of it

---

### Post by Ramses de Norre on 2006-04-01
Did the output of ./configure show any errors?

---

### Post by garethppls on 2006-04-01
[QUOTE=Ramses de Norre]Did the output of ./configure show any errors?[/QUOTE]
no configure went fine it was make install that had that one error there (on first post)

---

### Post by garethppls on 2006-04-02
actually is there any binary for ESP GhostScript 8.15.1

---

### Post by Spano on 2006-04-02
Do you have all of these installed?
libjpeg (Default branch) (required)
Common UNIX Printing System (recommended)
libpng (recommended)
zlib (recommended)

---

### Post by garethppls on 2006-04-02
[QUOTE=Spano]Do you have all of these installed?
libjpeg (Default branch) (required)
Common UNIX Printing System (recommended)
libpng (recommended)
zlib (recommended)[/QUOTE]
make: *** No rule to make target `src/png.c', needed by `obj/png.o'.  Stop.

now i'm getting that error :(

would be damned nice if there was a binary, and yes I have all those installed

---

### Post by Spano on 2006-04-02
my next idea would be to install libpng12-dev.
googled for binary package - don't see one for you.
let me download Ghostscript-8.53 and look it over.
Take heart, it took me six hours to get my Canon i860 to print!

---

### Post by garethppls on 2006-04-02
[QUOTE=Spano]my next idea would be to install libpng12-dev.
googled for binary package - don't see one for you.
let me download Ghostscript-8.53 and look it over.
Take heart, it took me six hours to get my Canon i860 to print![/QUOTE]
I got ESP Ghostscript 8.15.1 to install but when I restarted the printer still fecked up... The Samsung ML-4500 is meant to be linux compatible it has the penguin on the front even :/

---

### Post by Spano on 2006-04-02
I am out of ideas.  I did find this link from linuxprinting.org back to this forum:

[http://ubuntuforums.org/showthread.php?t=65111&highlight=ML-2010](http://ubuntuforums.org/showthread.php?t=65111&highlight=ML-2010)

hope this helps.  Good Luck

---

### Post by garethppls on 2006-04-02
I got the printer to work by updating to Dapper but the ndiswrapper wont work now :( :confused: :confused: :confused:

---

### Post by myspacee on 2007-08-02
same error for ESP GhostScript 8.15.4

how install ? :

libjpeg (Default branch) 
Common UNIX Printing System
libpng 
zlib

one-by-one?

thank you for reply

A.

---

