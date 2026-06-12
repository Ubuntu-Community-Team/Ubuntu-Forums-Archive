---
title: "Help me install Twinkle 1.4.2 (no sound on older Twinkle)"
date: 2009-04-29
forum: General Help
---

### Post by sookoon on 2009-04-29
I get no sound on Twinkle 1.2 VoIP, while sound works on every other program / wave file I have.  I've tried all the different output options.  

What I do notice that is interesting is in the audio properties, one of the options says:

OSS:  /dev/dsp:  Unknown name (Device is busy)

Even after a restart, and ensuring all other visible applications are closed, it still says busy. 

I have downloaded Twinkle 1.4.1, extracted the .tar to a folder, and have run the ./configure (as root) and here's what it regurgitated:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C preprocessor... gcc -E
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check

That's as far as I can get.  The same thing happens on the release before this, 1.4.1

---

### Post by ipolishchuk on 2009-09-04
[Sookoon]("http://ubuntuforums.org/member.php?u=316463"), Did you figure out how to solve your problem with either v1.2 or 1.4.2?
Interestengly, by Twinkle 1.2 worked till recently. Now the sound disappeared, apparently after some update.  I see the same "device busy" line in the System Settings for Audio.

---

### Post by ipolishchuk on 2009-09-04
Ok, I've figured it. Firefox hijacks the audio card, that why it says it is busy. When I kill Firefox, I can use Twinkle again.

---

