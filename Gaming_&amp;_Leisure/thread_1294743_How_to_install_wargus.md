---
title: "How to install wargus"
date: 2009-10-18
forum: Gaming &amp; Leisure
---

### Post by TomVocke on 2009-10-18
Hello everyone, after some solid google research I finally managed to get my wargus installation running. Here's how i got it done.

Make sure you have GCC and autoconf installed.

Download the source codes for stratagus and wargus versions 2.2.4
Insert or mount your warcraft 2 cd and write down the path

Step1 : Compiling stratagus:

>>open \stratagus\docs\install.hmtl
>>open terminal and navigate to stratagus folder
>>run fromdos configure (removes ^M), if command is not recognized: sudo apt-get install tofrodos
>>run ./configure
>>if depencies missing, find out which in install.html, and run again.
>>run make depend && make

Step2 : Compiling wargus:

>>open terminal and navigate to wargus folder
>>check wether the files on your CD are lower or upper case
>>if filenames are upper case, open wartool.c and replace all lower case file names with higher case ones or rename all the files on your cd to lower case files names if this is possible.
>>run make
>>if depencies are missing (i had a problem with libpng) install missing libraries

Step3 : Extracting warcraft 2 data:
>>open terminal and navigate to wargus folder
>>run fromdos build.sh (removes ^M), if command is not recognized: sudo apt-get install tofrodos
>>type: ./build.sh -p [/path/to/warcraft/cd] -o [/path/to/stratagus]/data

Step4 : Adding background music
>>find warcraft2 OST or rip music from original CD
>>add all the music into one file with audacity, nero wave editor or any decent sound editor
>>save as 8 bit mono PCM wave file 44100 samplerate
>>add to *.gz archive using archive manager or other software
>>rename archive to 'default.mod.gz'
>>replace default.mod.gz in stratagus/data/music/ folder with the one just made

Step5 : Removing folders
>>Everything but the contents of the stratagus folder can now be deleted

Step6 : Enjoy!
>>run wargus by starting stratagus!
(navigate to stratagus folder and execute stratagus binary)

---

### Post by TomVocke on 2009-10-20
Packages i used:

Zlib1g-dev
libpng12-dev
libbz2-dev
liblua50-dev
liblualib50-dev (extension library)
libsdl1.2-debian-all

---

### Post by Jamiethm on 2010-08-29
I have followed your instructions I got to running sudo make depend && make and it was working for about 5-6 minutes then I got the following! :-(

clude -O2 -pipe -fsigned-char -fomit-frame-pointer -fexpensive-optimizations -ffast-math src/stratagus/translate.cpp -o src/stratagus/obj/translate.o
g++ -c -DHAVE_CONFIG_H  -DUSE_BZ2LIB -DUSE_VORBIS -DUSE_MIKMOD -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DUSE_ZLIB -I. -I./src/include -I./src/guichan/include -O2 -pipe -fsigned-char -fomit-frame-pointer -fexpensive-optimizations -ffast-math src/stratagus/util.cpp -o src/stratagus/obj/util.o
src/stratagus/util.cpp: In function ‘int UTF8GetPrev(const std::string&, int)’:
src/stratagus/util.cpp:490: error: ‘stderr’ was not declared in this scope
src/stratagus/util.cpp:490: error: ‘fprintf’ was not declared in this scope
src/stratagus/util.cpp: In function ‘int UTF8GetNext(const std::string&, int)’:
src/stratagus/util.cpp:510: error: ‘stderr’ was not declared in this scope
src/stratagus/util.cpp:510: error: ‘fprintf’ was not declared in this scope
make: *** [src/stratagus/obj/util.o] Error 1


Any idea what it could be?

I have Stratagus 2.1 already installed with 2.1 wargus but it wont let me attack (break down) the wall to release the Elves on the 2nd level of the campaign (Ambush at Tarren Mill)  So im stuck here!!

---

