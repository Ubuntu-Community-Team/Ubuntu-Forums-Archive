---
title: "Compiling PCSX2 0.9.1"
date: 2006-07-11
forum: Gaming &amp; Leisure
---

### Post by KLineD on 2006-07-11
First of all, sorry if I posted this in the wrong forum, I wasn't sure if this was the correct place for something like this.

I'm trying to compile PCSX2 0.9.1 which was recently released just to try out some of my PS2 games and see how well (or bad) the emulation is. Basically the post on pcsx2.net main site got me interested:

> This release brings a significant speed increase to the majority of games, this is due to a complete rewrite of the EE and VU recompilers. Various other improvements have increased compatibility with games, you will be able to check your game against the included compatibility list, which lists nearly 1000 titles (Please note at time of release list is not guaranteed 100% accurate).

So I downloaded the sources from [pcsx2.net]("http://www.pcsx2.net") and tried to compile it. In the package there's a "Linux" folder so I cd into it and there isn't any configure file, the nearest thing is a configure.in file but I don't know what to do with it. I tried to skip configure and do make as there's a Makefile there but it doesn't work, here's the output:

> make: gtk-config: Command not found
gcc -Wall -O2 -fomit-frame-pointer -finline-functions -ffast-math -fno-strict-aliasing -m128bit-long-double -I. -I.. -I../IPU -I../DebugTools -D__LINUX__ -DENABLE_NLS -DPACKAGE=\"pcsx2\" -I../ix86-32 -I../x86  -c -o ../Counters.o ../Counters.c -MD -MF ../Counters.d
In file included from ../Counters.c:23:
../PsxCommon.h:21:21: error: windows.h: No such file or directory
../Counters.c:132: error: syntax error before ‘lfreq’
../Counters.c:132: warning: type defaults to ‘int’ in declaration of ‘lfreq’

And then a bunch of errors in different files. I don't know what the gtk-config command is, or how do I install it so make finds it. Another thing that got my attention is that PsxCommon.h is trying to include windows.h I believe this header file is part of Windows API am I right? I tried to #ifndef __linux__ and the error went away but still the other errors remained.

Anyone got any clue of this? or better yet, can make a deb out of this so us with no compiling skills can try it out?

Thanks a lot.

---

### Post by The Noble on 2006-07-11
I recently tested 0.9.1 on windows on the desktop and it runs well on many games. It is indeed 4 times faster on FFX (intro video is 20-35 fps), but some other improvements are lackluster (MGS2 - I'm looking at you and your .15 fps on intro).

----
3.0 Ghz P4
----

If you didn't know that the main compiler of the pcsx2 team's linux emulator left a few months ago, that is why it hasn't been compiled.

I don't know much programming, and have been using linux for less than a year, but I know that you will have a difficult time compiling it with some minor tweeks. It's code is deeply ingrained in windows systems calls if I recall correctly, so unless you are a truly amazing programmer and know what you are doing, you will have a difficult time.

The only suggestion I do have is that you ask the pcsx2 devs for some ideas on how to compile it, and If you have the time and the know-how, they most likely will help you if you are persistent(and nice). 

I don't mean to be spewing destructive commentary, but I am just making sure you know what you are getting yourself into. ;)

All in all, good luck.

---

### Post by KLineD on 2006-07-11
> I don't know much programming, and have been using linux for less than a year, but I know that you will have a difficult time compiling it with some minor tweeks. It's code is deeply ingrained in windows systems calls if I recall correctly, so unless you are a truly amazing programmer and know what you are doing, you will have a difficult time.

Well that pretty much means that it isn't portable, which is weird because previous versions of the emulator were compiled for linux. Maybe is because linuzappz left the team now they don't have the time to make a release for linux.

It's a real shame.

---

### Post by patrick295767 on 2006-07-11
I didnt have to compile it I guess... .
no ?

Did you looked in Zophar sthg ?? 
(unix)

[http://www.zophar.net/unix/psx2.html](http://www.zophar.net/unix/psx2.html)
  
I have working in my pc ... 
So complex to connfigure.
Would you have any ideas how to ?

---

### Post by The Noble on 2006-07-11
You are exactly correct (that sounds retarded), Linuzapz left and he did a bulk, if not all of the work on compiling pcsx2 for linux. I don't know, but maybe you could try wine to see if it will install (yeah, its an exe now). 

...

And patrick....that link is to a .7 version. You'll be lucky to even get into many of the games .9.1 actually plays. I don't know, but you may be able to find a linux version of .8.1, which will be a little better than nothing. 

And I am sorry to burst you bubble guys, maybe someone who knows more, and have looked deeply at the code may be able to help more. :(

---

### Post by uzi09 on 2006-07-14
hey guys, came across this thread cuz i was running into the same problem. sucks to hear that linux lost support for yet another program ](*,) 

anyways, after reading the posts, i went looking to find the answer on pcsx2's website. came across this thread in the forums:
[http://forums.ngemu.com/pcsx2-official-forum/73612-compiling-source-code.html?highlight=linux](http://forums.ngemu.com/pcsx2-official-forum/73612-compiling-source-code.html?highlight=linux)

unfortunately, it doesn't have the answer (or not when i checked it anyway), but it does provide an alternative to pcsx2 for unix based os's. ([http://pcsxii4unix.sourceforge.net/](http://pcsxii4unix.sourceforge.net/)) unfortunately, that site doesn't have anything available for downloads yet either :(.

anyway, thought i'd let you know to keep an eye on the forums there and about the alternative.


> **The Noble said:**
> You are exactly correct (that sounds retarded)

lol, it *is* retarded cuz it should be "that is exactly right" or "that is absolutely correct" or just "EXACTLY!"
(not to be the grammer police or anything, but thought i'd just let you know ;))

---

### Post by The Noble on 2006-07-14
Meh, I was too lazy at the time to really check it (not to mention I was was work :P). I should definately watch my spelling though, being a native English speaker and all.

Thanks for the link by the way. Looks like those developers are going to have one hell of a time.

---

