---
title: "Help with installing gtkwave with cygwin"
date: 2009-04-02
forum: General Help
---

### Post by Lionheartilly on 2009-04-02
I'm doing research for a professor using iVerilog and gtkwave. I downloaded the gtkwave files and followed this little tutorial to try and install it:

tar xvf gtkwave-1.3.86.tar.gz.gz
    cd gtkwave-1.3.86
    ./configure
    make

I'm running this code in cygwin and it works up to ./configure. In the gtkwave-1.3.86 folder, i see the Makefile and makefile.in files. However, when I type make inside that folder, I get the following error:

#compiling GTKwave...
make.exe: #: Command not found
make.exe [bin/gtkwave] error 127
no targets specified and no makefile found. stop.

I researched online a little bit and tested my version of the gcc compilers and they all tested out OK. Basically, i ran these tests from cygwin

gdb --version
make --version
g++ --version
gcc --version

If I'm in the wrong place, please help and redirect me somewhere as there is very little support with gtkwave. Thanks.

Oky

---

### Post by Simian Man on 2009-04-02
Hello.  I am also a Verilog programmer and gtkwave user.  However, I have never had any luck compiling and running graphical programs under Cygwin.  You will need to get X Windows working among other things.  Is there any way you can run Linux under a virtual machine.  This would be a much easier solution honestly.

As for your error, I am a little confused.  It says "make.exe: #: Command not found" but goes on to say "no targets specified and no makefile found. stop." which indicates that make.exe is there but the makefile isn't.  Is there a file called 'Makefile' or 'makefile' in the directory you're working in?

---

### Post by Lionheartilly on 2009-04-02
Yea there is a Makefile and a Makefile.in inside the folder which is why I'm really confused. I'm wondering if it's something to do with setting the environment variables such that the make command will work. I had to do that while compiling c++ code with the Windows command line but since this is cygwin, I wouldn't know.

Thanks for the quick response,

:)

I will try to set up virtual Linux or just try Linux because Vista can really really mess up my day. I had to reboot 5 times in 1 day just to get things working. :(

---

