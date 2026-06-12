---
title: "Zsnes Sound Fix, End All"
date: 2008-06-07
forum: Gaming &amp; Leisure
---

### Post by Heggerud on 2008-06-07
ok i know many people have had sounds problems (me also) with zsnes libao,alsa,oss,esd,etc.
 i have put together a fix, if installing libao-all or oss etc, does not work and you don't like using SDL cuz it sounds like crap try this!

you can download the zsnes source
[http://prdownloads.sourceforge.net/zsnes/zsnes151src.tar.bz2](http://prdownloads.sourceforge.net/zsnes/zsnes151src.tar.bz2)

then down load my audio.c file, extract it and the zsnes src then put audio.c in to the extracted zsnes folder replacing the existing audio.c file I.E. "zsnes_1_51/src/linux/audio.c"
and when you compile it make sure to add --enable-libao
should look something like "./configure --enable-release --enable-libao
"
or if your lazy, download my compiled zsnes bin, extract it and replace your zsnes bin you already have
 /usr/local/bin/ or /usr/bin/  deferent for deferent people:)
i compiled it under hardy 32-bit i686

p.s. i did not make that audio.c file, but i just put it and a fix together!

Hope This Helps, it worked awesome for me!

---

### Post by Heggerud on 2008-06-08
if this works for you or does not, let me know or drop a thanks :)

---

### Post by dfreer on 2008-06-10
I was just wondering, did you use the patch for the audio.c file found here:
[http://board.zsnes.com/phpBB2/viewtopic.php?p=168952#168952](http://board.zsnes.com/phpBB2/viewtopic.php?p=168952#168952)

If so, I wanted to let you know that Nach already compiled some binaries with the updated source code, found here:
[http://board.zsnes.com/phpBB2/viewtopic.php?p=168959](http://board.zsnes.com/phpBB2/viewtopic.php?p=168959)

This is probably a better link to the source code as well:
[http://zsnes.sf.net/zsnes151bsrc.tar.bz2](http://zsnes.sf.net/zsnes151bsrc.tar.bz2)

---

### Post by Heggerud on 2008-06-10
i used the audio.c from that 1.51b src, the bins on that site did not work for me very well(sound, scratching poping and crap) and some smaller errors, so i just made my own with the normal source and that audio.c file

---

### Post by doggyworld on 2008-06-12
Thanks.. I just downloaded the binary and it works great for me on Hardy!!!

---

### Post by Heggerud on 2008-06-14
you are very welcome

---

### Post by sivadnaes on 2008-06-14
Thanks a bunch!  Back to Terranigma!

---

### Post by ShadowMKII on 2008-06-14
So far, I have got to the point where I have the audio.c file and the zsnes_1_51 file on my Desktop. I want to make sure that when I install this that it ends up where it is supposed to end up.

The reason why I am right here is because I have a big weakness: compiling. I have never really got it down right.

How do you compile this? I clicked on the configure file in the src folder and told it to run, but that was it. Now I do not know where to go from here.

---

### Post by Fingel on 2008-06-14
ShadowMKII,
replace the old audio.c file with the new one you downloaded. It will be somehere in the zsnes folder. Then open a termianl and cd to where the configure file is. Type ./configure --enable-release --enable-libao
When that finishes, type "make" and then "sudo make install" and you should have zsnes installed :D

---

### Post by PrimoTurbo on 2008-06-14
I just use wine with zsnes it runs better then native imo.

---

### Post by ShadowMKII on 2008-06-14
The script finished, but once I typed in "make", Terminal said that 

"*** No targets specified and no makefile found.  Stop."

Terminal said an almost identical message after I typed in sudo make install. What happened?

---

### Post by ShadowMKII on 2008-06-14
Hold that thought.

Terminal said that I required NASM just before it declared the error, so I installed it via Synaptic. Now it says that I require "initscr" to run the debugger, but I do not plan to use the debugger. Even though I do not plan on using it, the cofiguring stopped.

Here is the code after I finished downloaded NASM:

```
jordi@Shadow-Slate:~/Desktop/zsnes_1_51/src$ ./configure --enable-release --enable-libao
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
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger
jordi@Shadow-Slate:~/Desktop/zsnes_1_51/src$ make
make: *** No targets specified and no makefile found.  Stop.
jordi@Shadow-Slate:~/Desktop/zsnes_1_51/src$ 
jordi@Shadow-Slate:~/Desktop/zsnes_1_51/src$ 

```

---

### Post by ShadowMKII on 2008-06-14
Well, I have downloaded those other files (took some time to find (involved about 3 packages)), but now I am told that Terminal cannot find "libao." _Now_ I think I do not know what is going on.

---

### Post by ShadowMKII on 2008-06-14
Okay, I went to another thread and found out that there is something called a "Multimedia Systems Selector" on Ubuntu, so I went to it and made my driver ALSA instead of OSS, which is what the default was. I tested the test sound and it was clear, but I was not able to get the input to make a test sound (probably because it was input and not output.)

Now sound works in ZSnes, but that still does not answer why "zsnes -ad sdl" and all of those other things do not work. I also have the issue that now I have some type of Zsnes_1_51 file on my Desktop and a .zsnes file in my home folder. What now?



(Sorry about all of the bloody spamming by the way!) ^^;;

---

### Post by Heggerud on 2008-06-14
you need Curses/NCurses, install it in synaptic, but you don't need to compile it, just goto if you have not already, open "ADD/REMOVE" in your gnome menu, and make sure you have "All available applications" on the bar left of the search bar, then search for ZSNES, install it, then download my ZSNES.tar.gz extract it and put it into your zsnes bin folder, should be /usr/bin/ or /usr/local/bin/ take a look
but you need admin rights, so do a sudo cp command and replace the zsnes bin file in /usr/bin/ or /usr/local/bin/

that should be correct? :lolflag:

then you should be golden! :)

---

### Post by ShadowMKII on 2008-06-15
Haha, I was pretty much golden before, but after doing a couple of tweaks here and there, now I am shining _and_ golden!!

Thanks, mate! ^^

---

### Post by Heggerud on 2008-06-15
glad to be of help, and thanks for the thanks :)

---

### Post by Horomancer on 2008-06-17
How do I extract your pre-compiled zsnes bin in the command line? If i try to extract from the GUI i just get an error that permission is denied.

---

### Post by Heggerud on 2008-06-18
you get a denied error with the tar.gz?
 that is really odd, i packed it pretty normal under Ubuntu 8.04
 you could try "tar -xf zsnes.tar.gz" that works for me, let me know how that goes

---

### Post by Horomancer on 2008-06-18
I got a denial for write permission to /usr/bin
Look around the ubuntu docs and saw how to move a file in command line so i could use sudo
I used the file you had listed and there is no difference in sound.
it works but sounds realy shitty.
The first time i ran zsnes i had zero sound, so i used a fix from another thread that said to run

zsnes -ad sdl

in the command line. This gave me shitty sound. should i switch back to using oss or alsa with you compiled zsnes?

---

### Post by Heggerud on 2008-06-18
i use OSS, make sure you install "libsdl1.2debian-oss" in Synaptic Package manager, then use "zsnes -ad oss"

do other sounds, sound crappy? such as playing music mp3,ogg,wav, or in other games or programs?, it could also be your sound card is not set up right, or it is not well supported under linux,

---

### Post by Horomancer on 2008-06-22
My sound works great on all other apps.
I ran-

zsnes -ad alsa

in the command line and now the sound works great.
Thanks for all the help

---

### Post by Heggerud on 2008-06-30
you are welcome, lol i have not been on for a week!

---

### Post by thrasher6900 on 2008-08-11
Still no sound.

All other sounds work on other games.

What's some other ideas please.

I have a presario c552 if that helps anything.

---

### Post by quanumphaze on 2008-08-29
Your binary didn't work for me. Kept returning "Illegal instruction".
I assume that has something to do with the CPU architecture, but I'm running a Celeron. Something you may want to look into.

Your patch however did work, thanks.

---

### Post by growingneeds on 2008-09-09
I installed ZSNES Emulator in Hardy Heron via Synaptic Package Manager. However, ROMs loaded had no sound. The following steps remedied the situation:

With the Text Editor (gedit), navigate to **~/.zsnes/zsnesl.cfg**
Locate the phrase **libAoDriver="auto"** and change to **libAoDriver="sdl"**
Fire up ZSNES Emulator, and change the sampling rate to **48000Hz** (Under Config, Sound).

---

### Post by Heggerud on 2008-09-17
> **quanumphaze said:**
> Your binary didn't work for me. Kept returning "Illegal instruction".
I assume that has something to do with the CPU architecture, but I'm running a Celeron. Something you may want to look into.

Your patch however did work, thanks.
I compiled my binary on a AMD64 Athlon 3000+, download the source(make sure to add the patched file i have there on page 1) and compile it on your system, compile info is in the docs folder, i would my self but i do not own any intel CPU's with linux on them to try and compile and test my self

---

### Post by Heggerud on 2008-09-17
> **growingneeds said:**
> I installed ZSNES Emulator in Hardy Heron via Synaptic Package Manager. However, ROMs loaded had no sound. The following steps remedied the situation:

With the Text Editor (gedit), navigate to **~/.zsnes/zsnesl.cfg**
Locate the phrase **libAoDriver="auto"** and change to **libAoDriver="sdl"**
Fire up ZSNES Emulator, and change the sampling rate to **48000Hz** (Under Config, Sound).
after you installed zsnes did you replace the installed binary file with my patched binary file?, and set the audio to a lower setting then 48k try 32k, and changing it from SDL to OSS or ALSA using "zsnes -ad oss" or replace oss with alsa if that did not work

---

### Post by Heggerud on 2008-09-17
> **thrasher6900 said:**
> Still no sound.

All other sounds work on other games.

What's some other ideas please.

I have a presario c552 if that helps anything.
having libsdl1.2debian-oss installed worked for me, or install libsdl1.2debian-all
 you can install them from synpatic.
then set the audio driver in zsnes, "zsnes -ad oss" or "zsnes -ad alsa" and make sure the rate is not to high or low under zsnes sound settings in the gui, 22k/32k is good or 44k which ever works and sounds good

---

### Post by Darth Shuttleworth on 2008-10-26
Thank you so much.  I've just been using the provided binary, but if the developers don't fix this in intrepid, I'll just compile it and install that way.  Chrono Trigger time! w00tness!!!

PS:  Speaking of Chrono Trigger, that game is coming out on the Nintendo DS in a month.  I encourage everyone on the planet with a DS to buy it.  If you live in the US, get it then.  If you live in Europe, it will be coming to your continent for the first time next year.

---

### Post by dfreer on 2008-10-27
> **Heggerud said:**
> I compiled my binary on a AMD64 Athlon 3000+, download the source(make sure to add the patched file i have there on page 1) and compile it on your system, compile info is in the docs folder, i would my self but i do not own any intel CPU's with linux on them to try and compile and test my self

If you are intending to distribute binaries of zsnes, compile like so:
```
./configure --enable-release --disable-cpucheck force_arch=i586
``` Would also recommend putting --enable-libao in there as well. This produces a binary that should work on pretty much any cpu type nowindays.

As for those with sound issues still, this thread of mine hopefully might help:
[http://ubuntuforums.org/showthread.php?t=851396](http://ubuntuforums.org/showthread.php?t=851396)

---

