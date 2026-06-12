---
title: "problem installing zsnes"
date: 2009-01-12
forum: General Help
---

### Post by WIndows to LInux on 2009-01-12
Hello!
I've been trying to install the zsnes emulator (I don't believe the Wii's virtual console will be supporting the games that needed the SuperFX chip) and I'm having trouble.

After looking at synaptic, I believe I have SDL, which the install is complaining about not being installed, but I still can't install it.
Heres the error output

checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: SDL >= 1.2.0 is required

I have the correct version...

By the way, would anyone know where to find a legal copy of a game ROM?

Help me, please

---

### Post by WIndows to LInux on 2009-02-19
never mind, found out that I was missing a libary, and that I could get it with apt-get/synaptic

---

### Post by Yellow Pasque on 2009-02-19
So did you get zsnes to compile successfully on x86_64?

---

### Post by WIndows to LInux on 2009-02-21
never bothered after I found out that it was on synaptic, but I've been unable to compile even after I got the library
I can't wait until the assembler is converted to C
maybe they should modify the install script... AMD64 is 100% i386 compatible*, it works fine when running
*at least for an Intel Core 2 Duo*

---

### Post by WIndows to LInux on 2009-06-22
....except when using a Ubuntu admin account (for those who don't know, I'm talking about ones that can use sudo, not the root account)

P.S. I've decided to uninstall, because of the above, and playing games on an emulator is not easy

---

### Post by Tipped OuT on 2009-06-22
Well I know you kinda "solved" the problem already but...

Go to Add/Remove programs, search for zsnes. Install it, download a ROM of a game that you legitimately already own, then load it up in zsnes. Not hard in my opinion.

---

### Post by WIndows to LInux on 2009-07-06
My account is the only one that can use sudo, and when I play a game, the keyboard and mouse freeze up, along with the rest of X11, and the emulator goes along like nothing happened, not responding to the keyboard, until I hit ctrl-alt-backspace to log out (not to sure even that worked, been to long scene)

---

