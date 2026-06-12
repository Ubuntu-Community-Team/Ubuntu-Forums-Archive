---
title: "C++ Compiler"
date: 2009-04-24
forum: General Help
---

### Post by letmekilluplz on 2009-04-24
I need a good C++ compiler. I've heard about G++ but can't figure out how to install it. 

An off topic question. I have no problems with Intrepid Ibex(8.10 i think) Is there anythin outstanding about 9.04 that I should know. I heard evloution and other software has had upgrades and have no problems with them. Is there anyway I can get them without upgrading?

---

### Post by M4rotku on 2009-04-24
I know that you can get g++ from the build essentials package:

> sudo apt-get install build-essential

---

### Post by Iowan on 2009-04-24
I (or you) might need to look up details, but **build-essential** is the package you need to install.
[http://www.ubuntux.org/how-to-install-basic-compilers-build-essential]("http://www.ubuntux.org/how-to-install-basic-compilers-build-essential")

---

### Post by paradigm2 on 2009-04-24
> **letmekilluplz said:**
> I need a good C++ compiler. I've heard about G++ but can't figure out how to install it. 

An off topic question. I have no problems with Intrepid Ibex(8.10 i think) Is there anythin outstanding about 9.04 that I should know. I heard evloution and other software has had upgrades and have no problems with them. Is there anyway I can get them without upgrading?


I'm not sure but I always thought g++ was installed by default?

Anyway go to a terminal and type:

```

g++

```

If you get told no input files or such then ti is in there already.  If not, just install the g++ package and there you go (edit: Go with what Iowan said regarding installing build-essentials... that will install g++ as well as all sorts of other needed things).

About Jaunty and/or keeping what you have and upgrading individual programs, you might be able to get a lot of updated software using PPA's  (see: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA) ) or by downloading .deb files from projects, or perhaps compiling them yourself.  But such is risky.  Also sometimes Backports (see: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports) ) are made vailable of newer software.  

Common Issues with Jaunty that I have seen:

1. Audio problems related to pulseaudio and alsa (especially Intel HDA cards)

2. Video issues, especially with Intel and ATI cards.

3. WIFI related issues. (much less common)

4. Upgrading issues for people not doing a clean install.


I recommend posting the output of 

```

lspci

```

And see if anyone comments on issues, or perhaps manually check your hardware using search on this forum (especially the old jaunty forum) and see what issues come up with it.

---

### Post by letmekilluplz on 2009-04-24
> **M4rotku said:**
> I know that you can get g++ from the build essentials package:

Says it's already installed how do I run it its not in the menus that I can see

---

### Post by snova on 2009-04-24
> **letmekilluplz said:**
> Says it's already installed how do I run it its not in the menus that I can see

There is a difference between a compiler and and IDE, and GCC is the former.

Search Synaptic for an IDE; Geany comes to mind, there are others.

---

### Post by Sub101 on 2009-04-24
If im understanding you correctly then the compiler would be run from the terminal. ie
```
g++ "name of file"
```

---

### Post by jespdj on 2009-04-24
> **paradigm2 said:**
> I'm not sure but I always thought g++ was installed by default?
Yes, but not the header files and other stuff that you need to compile programs that use the standard C or C++ libraries - for that you need to install build-essential.
> **letmekilluplz said:**
> Says it's already installed how do I run it its not in the menus that I can see
That's because the compiler is a command line program, not an [IDE](http://en.wikipedia.org/wiki/Integrated_development_environment). There are several IDEs available for C++, have a look through the forums, people have asked the question "which IDE for C++" many times before.

---

### Post by DGortze380 on 2009-04-24
gcc is a command line utility.

usage

```

gcc myProgram.c -o myProgram

```

or 

```

g++ myProgram.cpp -o myProgram

```

You can certainly get an IDE that utilizes gcc in a GUI environment.

---

### Post by letmekilluplz on 2009-04-24
Thanks I see now I was thinking that G++ was like bloodshed for windows

---

