---
title: "Can't play new alien arena 7.20"
date: 2008-10-22
forum: Gaming &amp; Leisure
---

### Post by Rotarychainsaw on 2008-10-22
Hey, Wanted to try out the new alien arena, but I get an error when trying to run it. 

./crx: error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory

I checked synaptic and the packages are installed, so I don't know whats up. Anyone else seeing this?

---

### Post by Perfect Storm on 2008-10-23
Are you running 64-bit?

---

### Post by Rotarychainsaw on 2008-10-23
Yeah, I didn't see any seperate DLs for 64 bit on the AA page.

---

### Post by Irritant on 2008-10-23
You need to compile the binaries yourself.  Cd to source and type make; make install

---

### Post by Rotarychainsaw on 2008-10-23
Ah you were right! Thanks. Is that common knowledge? I didn't see it mentioned anywhere. 

On another note, If they could get those effects into urban terror, I'd be a happy camper.

---

### Post by MaxIBoy on 2008-10-23
I've suggested building a seperate 64-bit binary on the Alien Arena forums: [http://corent.proboards42.com/index.cgi?action=display&board=aatech&thread=3303](http://corent.proboards42.com/index.cgi?action=display&board=aatech&thread=3303)



As for getting the good graphics into UrT:


Urban Terror uses pure Q3 graphics (ioQ3.) Alien Arena was originally Q2 based (still has pure Q2 physics, uses the Q2 map format and model format,) but the rest of the engine is completely overhauled. 

I bet you there are some drop-in replacement Q3 engines that would improve the graphics somewhat, but especially since the latest version, Alien Arena has better graphics than most other free FPSs. Its closest rival (nexuiz) actually uses an overhauled Q1 engine. 

There's really been very little development with Q3, because the Q3 engine hasn't been open source for as much time as Q2 or Q1.



Urban Terror is not really a graphics-focused game.

---

### Post by Perfect Storm on 2008-10-23
[A guide to compile it](http://gaming.gwos.org/doku.php/guides:64bit:alien_arena)

---

### Post by MaxIBoy on 2008-10-23
I'd actually recommend crx.sdl-- if crx works, fine, but for many people there will be no sound. Crx.sdl doesn't have that problem.

---

### Post by Perfect Storm on 2008-10-23
Hmm...thanks, will write that in. Though I never had problems with sound in AA.

---

### Post by MaxIBoy on 2008-10-23
All right.


And as soon as I get a 64-bit OS dual booting on my computer, I'll be making pre-built 64-bit Alien Arena tarballs.

---

### Post by Perfect Storm on 2008-10-24
> **MaxIBoy said:**
> I'd actually recommend crx.sdl-- if crx works, fine, but for many people there will be no sound. Crx.sdl doesn't have that problem.

Fixed.

---

### Post by MaxIBoy on 2008-10-24
Cool.

---

### Post by munkee on 2008-10-26
I have just compiled AA from source but it didn't make a crxsdl file.  All I got was crx and crxed.  I'm stumped, any ideas?

---

### Post by Perfect Storm on 2008-10-26
Make sure you have installed all the required -dev files when compiling.

---

### Post by munkee on 2008-10-27
Please can you clarify what dev files I would need?  I did follow the guide on Ubuntu Gamers Arena.  I will try again later on, and see if I missed any error messages during the compiling

---

### Post by Perfect Storm on 2008-10-27
Can you please post in/output when you do the guide, and afterwards **ls -a** in AA directory.

---

### Post by munkee on 2008-10-27
Thanks Artifical Intelligence.  You pointed me in the right direction.  When I did the compiling I noticed that the crx.sdl file got wiped when I ran the make install command.  

I'm not sure that is supposed to happen, but I'm now up and running with sound in AA 2008.

Again, thanks for you assistance. :)

---

