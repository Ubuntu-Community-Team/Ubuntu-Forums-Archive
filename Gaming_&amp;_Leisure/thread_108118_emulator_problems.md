---
title: "emulator problems"
date: 2005-12-25
forum: Gaming &amp; Leisure
---

### Post by Deneb Algedi on 2005-12-25
I've already tried many to install emulators(GnomeBoyAdvance, Gens&Zsnes). I've search this forum many times used google.
But still nothing works.
The repo-versions don't work, I can't find any deb packages, and I have no idea how the create one from source.
Would there be anybody be so kind to help me?

---

### Post by bunutu on 2005-12-25
emulators can be a pain.  I would recommend you just compile your favorite emulator(s) from source.  stuff like gnuboy, stella, snes9x, etc. usually are just one binary file and maybe a .rc file of some sort. 

Getting gcc working on ubuntu is a breeze. Just apt-get install build-essential and the necessary -dev packages to build your emulator.  When you run ./configure in the source directory, the script will fail and tell you what libraries and headers (contained in -dev packages) are needed. Once you can run ./configure w/o errors, try running make to build the emulator.

I couldn't figure out how to apt-get install basilisk2, a 68k macintosh emulator, so I built it from source. The ./configure script said I needed SDL and GTK. So I apt-get installed them.  It only took about 10 mins to compile on an ancient Pentium coppermine laptop 900MHz.

If this isn't clear, pick a specific emulator like say gnuboy and try to compile it.  Search the forums and ask questions.  Doing this the first time may seem pretty hard, but your learn a lot that can be used over and over again.  Unless you are trying to resurrect some ancient game like XMrIs, compiling stuff is easy.

---

