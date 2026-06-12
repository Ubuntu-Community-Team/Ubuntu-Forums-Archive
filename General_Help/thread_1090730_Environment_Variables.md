---
title: "Environment Variables"
date: 2009-03-08
forum: General Help
---

### Post by sdp on 2009-03-08
I'm making utilities for LaTeX. To make it work on several platforms (MAC, Ubuntu and Windows), I use an environment variable APPDATA (adopted from Windows). In Ubuntu it is made by putting this line into etc/environment: APPDATA=~/prgdata where prgdata is a directory placed in HOME directory.

It works, but it is not perfect. The problem is that '~' is not expanded until it is used in a shell. To be sure that a command works even with spaces in names (in Windows HOME is placed in 'Documents an Settings'), I have to place quotes (") around parameters. But then '~' is NOT expanded :(

In Emacs Lisp I have solved the problem using a hack. But in my makefiles I cannot find a solution. The result is that this line (from a makefile):

 g++ -c -x c++ test.cpx -o test.o -I $(APPDATA)/emacs/texdpix/include

works in Ubuntu, but not in Windows (because of spaces in HOME)

and this line

 g++ -c -x c++ test.cpx -o test.o -I "$(APPDATA)/emacs/texdpix/include"

works in Windows but not in Ubuntu (because of quotes).

Although they are almost identical, I need sparate platform dependant makefiles (and the Ubuntu version would'nt even work in Ubuntu if HOME had spaces in the name).

Anybody have a good idea?

Svend Daugaard Pedersen
Denmark

---

### Post by dcstar on 2009-03-08
> **sdp said:**
> I'm making utilities for LaTeX. To make it work on several platforms (MAC, Ubuntu and Windows), I use an environment variable APPDATA (adopted from Windows). In Ubuntu it is made by putting this line into etc/environment: APPDATA=~/prgdata where prgdata is a directory placed in HOME directory.

It works, but it is not perfect. The problem is that '~' is not expanded until it is used in a shell. To be sure that a command works even with spaces in names (in Windows HOME is placed in 'Documents an Settings'), I have to place quotes (") around parameters. But then '~' is NOT expanded :(

In Emacs Lisp I have solved the problem using a hack. But in my makefiles I cannot find a solution. The result is that this line (from a makefile):

 g++ -c -x c++ test.cpx -o test.o -I $(APPDATA)/emacs/texdpix/include

works in Ubuntu, but not in Windows (because of spaces in HOME)

and this line

 g++ -c -x c++ test.cpx -o test.o -I "$(APPDATA)/emacs/texdpix/include"

works in Windows but not in Ubuntu (because of quotes).

Although they are almost identical, I need sparate platform dependant makefiles (and the Ubuntu version would'nt even work in Ubuntu if HOME had spaces in the name).

Anybody have a good idea?

Svend Daugaard Pedersen
Denmark

Try single quotes or the "`" delimiter.

---

### Post by sdp on 2009-03-09
Single quotes does'nt work.

But I solved the problem my self by using the make-function $(shell ..). The assignment APDATA = $(shell echo $(APPDATA)) passes APPDATA through the shell and '~' is expanded to the absolote path. Now I can put quotes around.

Svend Daugaard Pedersen

---

