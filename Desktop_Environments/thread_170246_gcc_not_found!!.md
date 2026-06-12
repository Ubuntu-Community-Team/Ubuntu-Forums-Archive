---
title: "gcc not found!!"
date: 2006-05-04
forum: Desktop Environments
---

### Post by grontoft on 2006-05-04
I'm have some problems with installing programmes...

For example, I have downloaded a file from [www.libsdl.org](www.libsdl.org), a library to be installed to make low level access to audio, keyboard and so on...

But when I try to install like this (in the correct directory, mind you:mrgreen: )

~$ ./configure

the terminal returns this:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

I have tried to write : whereis gcc
and the terminal finds the gcc here: 
/usr/lib/gcc

What am I doing wrong??

When I go to the gcc directory, I find this file "i486-linux-gnu"

---

### Post by Sef on 2006-05-04
To compile, you need to download build-essential.

Application > Accessories > Terminal

sudo apt-get update

sudo apt-get install build-essential

---

### Post by grontoft on 2006-05-04
I'm downloading at this moment...

What is build-essential??

I know, I'm a dork... but no questions = nothing learned...

---

### Post by Sef on 2006-05-04
Build-Essential is a metapackage that has the basic tools to compile.

---

