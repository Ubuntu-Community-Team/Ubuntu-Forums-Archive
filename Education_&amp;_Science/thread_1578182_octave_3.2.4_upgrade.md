---
title: "octave 3.2.4 upgrade??"
date: 2010-09-20
forum: Education &amp; Science
---

### Post by apchar on 2010-09-20
I'm using octave 3.2.3 in Ubuntu 10.04. 3.2.3 is the latest octave package in the synaptic database even though it's a little old now. 3.2.3 has a killer bug in (ironically) the debugger that has been fixed in 3.2.4. But I can't find an Ubuntufied upgrade. Does anyone know where I can find one? I'd hate to have to compile octave 3.2.4 from source.](*,)
Thanks,
apchar

---

### Post by beew on 2010-09-20
Go to this link, add the ppa to synaptic and upgrade and you get Octave 3.2.4. :)
[URL="https://launchpad.net/~lucid-bleed/+archive/ppa"]
https://launchpad.net/~lucid-bleed/+archive/ppa[/URL]

---

### Post by apchar on 2010-09-25
I added the ppa.  A lot of new packages appeared. Octave 3.2.4 isn't among them. What would prevent me from seeing it in the list? Can it be because I'm using an AMD cpu?
Apchar

---

### Post by beew on 2010-09-27
I don't know.  As you can see from the list of packages in the PPA, Octave3.2.4.6 is right there. I installed it from this ppa with no problem.  I have Intel 32 bit CPU if that is of any significance.

There is another way though. You can snatch it from Maverick's repo but you have to be careful. Add Maverick's main and universe repositories to your sources list. Then update the sources and upgrade  the Octave packages. After that you should disable the Maverick repository so that you wouldn't be prompted to upgrade things that may give you troubles down the line. I have upgraded a few packages this way, but only for end user programs that don't have a lot of external dependencies, I wouldn't try to upgrade softewares pertaining to system functions or packages that have a lot of extra dependencies (so Octave is ok)

To add the Maverick repository (AMD64 is the same) :
[http://packages.ubuntu.com/hu/maverick/i386/octave-parallel/download](http://packages.ubuntu.com/hu/maverick/i386/octave-parallel/download)

---

