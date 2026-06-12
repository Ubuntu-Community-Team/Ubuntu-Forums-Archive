---
title: "Problems installing Wargus"
date: 2007-12-20
forum: Gaming &amp; Leisure
---

### Post by Grout58 on 2007-12-20
Im having some problems installing wargus under gutsy.  So I installed stratagus from the repo and downloaded wargus from the site.  The readme says run ./build.sh -p /media/cdrom0  Thats where my wacraft 2 cd is.  When I run it I get permission denied so I use sudo ./build.sh -p /media/cdrom0 and that gives me sudo: ./build.sh: command not found.  So then I used sh build.sh -p /media/cdrom0 and that gives me
grout@ubuntu:~/Desktop/wargus-2.2.4$ sudo sh build.sh -p /media/cdrom0/ /home/grout/wargus
: not found7: 
: not found1: 
: not found4: 
: not found7: 
: not found0: 
: not found3: 
: not found5: 
build.sh: 47: Syntax error: word unexpected (expecting "in")
So now im really not sure what to do.. Anyone got any ideas?

---

### Post by Perfect Storm on 2007-12-21
Are you sure that the command shall have: /home/grout/wargus ?
Also if you are installing the game locally there's no need of sudo, also check if the script you want to execute is set for it.

---

### Post by disturbedite on 2007-12-21
you shouldn't use the stratagus package from the ubuntu repo, its seriously outdated.  (as a matter of fact, i don't think the latest release of wargus works with older versions of stratagus, i believe it requires stratagus 2.2.4).
you should compile stratagus 2.2.4 yourself and *then* compile wargus 2.2.4.

---

### Post by jestin on 2008-01-29
You will need to run
```
dos2unix build.sh
```

If you don't have dos2unix, run
```
sudo apt-get install tofrodos
```

---

### Post by jestin on 2008-02-13
I finally got the whole thing working, so I figure I should post how to do it.

First, the wartool application that comes with wargus was always compiling to use file names like rezdat.war instead of REZDAT.WAR (which is what my CD had on it).  My quick fix was to do a find and replace in the wartool.c file of any filename that isn't upper case.  After that, I typed 'make' to recompile, and the script worked beautifully.

Once it finally ran, sound wan't working.  This is because I needed the package libsdl1.2debian-all.  So I installed it:

```
sudo apt-get install libsdl1.2debian-all
```

This will remove libsdl1.2debian-alsa, but you won't need that anymore anyways.

Now Wargus works.  I still don't have music or videos, but I'm not sure that's a part of wargus anyways.  I hope this helps someone.

---

### Post by disturbedite on 2008-02-13
no, its not that its "not a part of wargus", its just that the project was never fully completed before it was abandoned.  (the devs are working on bos wars & stargus now).
i think its mostly complete, i'd say 95% complete, maybe even more.  but of course there are minor things here & there one might notice that weren't finished/implemented.

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

