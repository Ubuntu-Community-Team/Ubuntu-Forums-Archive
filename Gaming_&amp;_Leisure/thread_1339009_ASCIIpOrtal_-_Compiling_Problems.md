---
title: "ASCIIpOrtal - Compiling Problems"
date: 2009-11-27
forum: Gaming &amp; Leisure
---

### Post by EmperorWilli on 2009-11-27
Hey,
I just found the game "ASCIIpOrtal" [http://cymonsgames.com/asciiportal/](http://cymonsgames.com/asciiportal/)
and wanted to install it on my PC (eeePC, Ubuntu NetbookRemix with Fluxbox as a windowmanager). Therefore I downloaded the actual versions sources (there are only binarys of an outdated linux version) and tried to compile them.. but I got some problems..

```

pirat@Black-Pearl ~/Games/asciiportal1.2c-src (git)-[master] % make
make: *** No rule to make target `al_input.o', needed by `asciiportal'.  Stop.

```

So therefore I'm wondering which packets I need to be able to compile the game... I already installed SDL and also tried installing PDCurses (but didn't succeed compiling it...)

Greetings Tobias

---

### Post by lloyd_b on 2009-11-27
> **EmperorWilli said:**
> Hey,
I just found the game "ASCIIpOrtal" [http://cymonsgames.com/asciiportal/](http://cymonsgames.com/asciiportal/)
and wanted to install it on my PC (eeePC, Ubuntu NetbookRemix with Fluxbox as a windowmanager). Therefore I downloaded the actual versions sources (there are only binarys of an outdated linux version) and tried to compile them.. but I got some problems..

```

pirat@Black-Pearl ~/Games/asciiportal1.2c-src (git)-[master] % make
make: *** No rule to make target `al_input.o', needed by `asciiportal'.  Stop.

```

So therefore I'm wondering which packets I need to be able to compile the game... I already installed SDL and also tried installing PDCurses (but didn't succeed compiling it...)

Greetings Tobias

You don't need PDCurses - that's for Windows boxes that don't have a native Curses library.  Ubuntu has the Ncurses library, which provides those functions. 

First, install some support packages:```
sudo apt-get install build-essential libsdl1.2-dev libsdlmixer1.2-dev liballegro4.2-dev libncurses5-dev
```Note that some of these may already be installed - I've included every package I could think of.

Second, edit the Makefile to fix the #$%*^ typo - at line 39, where it has "al_input.o", change it to "ap_input.o" (leaving the rest of the line alone).

At this point, "make" should build it correctly.

Lloyd B.

---

### Post by EmperorWilli on 2009-11-27
Ok thanks a lot, i got it to work.... stupid typo ... how should i have known .... .

I had to install the libsdl-mixer1.2-dev aswell.. if somebody here has the same problems

---

### Post by lloyd_b on 2009-11-27
> **EmperorWilli said:**
> Ok thanks a lot, i got it to work.... stupid typo ... how should i have known .... .

I had to install the libsdl-mixer1.2-dev aswell.. if somebody here has the same problems

Oops - typo on my part (libsdlmixer1.2-dev versus libsdl-mixer1.2-dev).  Sorry.

Lloyd B.

---

