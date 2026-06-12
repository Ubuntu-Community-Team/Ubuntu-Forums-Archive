---
title: "gcc cannot create executables..."
date: 2005-11-11
forum: Desktop Environments
---

### Post by anarchojens on 2005-11-11
Hello :)

my gcc always returns the message, that it cannot create executables. That happens, when I want to create a very very simple hello-world Programm in kdevelop and also when I want to compile a programm that I downloaded, then the message is returned when I run the .configure. Gcc is installed, also make... 

can anyone help me with that?

Thanks

Jens

---

### Post by PaganHippie on 2005-11-11
Have you tried using gcc from the command line, rather than from within kdevelop? Try opening a terminal, cd'ing to the directory containing your source code, and invoking gcc directly, such as:
```
gcc hello.c
``` If this works, then the trouble is plainly not with gcc. If it doesn't work, try using Synaptic to re-install gcc.

---

### Post by Ubuntist on 2005-11-11
I had that problem.  It turned out that I didn't have all of the necesssary libraries installed -- it might have been something along the lines of libc that was missing.  Anyway, using Synaptic to install it solved the problem.

---

### Post by Roobert on 2005-11-11
[QUOTE=Ubuntist]I had that problem.  It turned out that I didn't have all of the necesssary libraries installed -- it might have been something along the lines of libc that was missing.  Anyway, using Synaptic to install it solved the problem.[/QUOTE]

Isn't clicking on gcc 4.0 in Synaptic supposed to automatically select all related and required packages? I have been trying to compile Grass GIS 6.1cvs from the command line, and I get the same reply, that "configure: error: installation or configuration problem: C compiler cannot create executables."

But strangely, I can compile regular C-type programs....:confused:

---

### Post by codejunkie on 2005-11-11
[quote=anarchojens]Hello :)

my gcc always returns the message, that it cannot create executables. That happens, when I want to create a very very simple hello-world Programm in kdevelop and also when I want to compile a programm that I downloaded, then the message is returned when I run the .configure. Gcc is installed, also make... 

can anyone help me with that?

Thanks

Jens[/quote] this might help ```
sudo apt-get install build-essential linux-headers-`uname -r`
``` this will install the basic compilers and kernel headers hope it helps.

---

