---
title: "Setting a Makefile to use a certain version of gcc"
date: 2009-03-09
forum: General Help
---

### Post by Neo_The_User on 2009-03-09
Hello. I am experienced with mainly C and C++ and I recently compiled GCC 4.4 March 6 2009 snapshot from source and I was going to make a guide on compiling a kernel using the version of GCC that was compiled from source but I do not know how to specify the Makefile to use that particular version of gcc. Sorry my English is a bit difficult to keep track of. 

Basically what I am asking, how do you set the option when compiling a program to use a specific target? I want the kernel's Makefile to look for the gcc that I compiled by hand from source and not the one in the Ubuntu 8.10 repository. Any advice would be greatly appreciated. Thanks in advance.

Also, my dad is trying to compile flashrom using gcc 4.1 and he has it installed from the ubuntu repository but flashrom uses the gcc-4.3 version from the repos. The new version of flashrom requires an older version of gcc in order to compile.

One more thing, I compiled gcc with ./configure --prefix=/usr && make && sudo make install

---

### Post by Neo_The_User on 2009-03-09
***SOLVED*** GCC 4.4 is default the primary one if --prefix=/usr

I am experienced with mainly C and C++. I recently compiled GCC 4.4 March 6 2009 snapshot from source. I was planning on make a guide on compiling a kernel using the compiled version of GCC. Unfortunately, I do not know how to specify the Makefile to use that particular version of gcc.

Thanks in advance.

Also, my dad is trying to compile flashrom using gcc 4.1 and he has it installed from the ubuntu repository but flashrom uses the gcc-4.3 version from the repos. The new version of flashrom requires an older version of gcc in order to compile.

One more thing, I compiled gcc with ./configure --prefix=/usr && make && sudo make install

---

### Post by bodhi.zazen on 2009-03-09
gcc is a link ...

so ...

unlink /usr/bin/gcc

Then link to the new version :twisted:

---

### Post by geraldm on 2009-03-09
The correct answer depends on how you have set  up various gcc compilers on
your  system, as well as how the Makefile is written.
I have sometimes installed multiple gcc executables in /usr/bin and add version names after e.g. gcc-4.3 gcc-4.3.2.  There is a link from /usr/bin/gcc to /etc/alternatives/gcc which in turn is a link pointing to /usr/bin/gcc-VERSION_TO_USE

The Makefile would have a line like
CC = gcc

The system links, and the Makefile need to be coordinated.

regards,
Gerald

---

### Post by Neo_The_User on 2009-03-09
Thank you but all that work for nothing. It automatically made GCC 4.4 from source the default but...

[http://ubuntuforums.org/showthread.php?t=1091997](http://ubuntuforums.org/showthread.php?t=1091997)

eeeYeah, got some serious issues.

---

### Post by Neo_The_User on 2009-03-09
gcc 4.4 broke my system anyway.

---

### Post by bapoumba on 2009-03-10
Threads merged.

---

