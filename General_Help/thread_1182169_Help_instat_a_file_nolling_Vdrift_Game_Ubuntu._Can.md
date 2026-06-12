---
title: "Help instat a file nolling Vdrift Game Ubuntu. Cannot install it!!"
date: 2009-06-08
forum: General Help
---

### Post by scrypt on 2009-06-08
Hi All.

Can somebody help me to install Vdrift in Ubuntu 9.04.

I have spent an age trying to correctly Configure, Make and install the tar.bz2 files. But cannot seem to do it.

I have read numerous posts and even tried to use and install the Vdrift auto-installer from the Vdrift web site.

But it did not work!

Has anybody had any joy instaling Vdrift?

Also can anybody show me how to correctly configure and install Vdrift??

I have downloded the file called vdrift-2009-02-15.tar.bz2, and extracted it to my Desktop.

Ans as I mentioned I have followed supposedly correct tutorials to configure and install it.

But the main issue I have, is that. When I try to do any thing with the vdrift-2009-02-15.tar.bz2 file

I keep getting the repeat error that it is 'No Such File Or Directory'

any help would be greatly appreciated!!

Thank's

---

### Post by Goddard on 2009-06-08
I know a lot of people are having this problem.

[http://ubuntuforums.org/showthread.php?t=574024](http://ubuntuforums.org/showthread.php?t=574024) or [http://watteimdocht.de/autopackage/forum/viewtopic.php?f=4&t=41](http://watteimdocht.de/autopackage/forum/viewtopic.php?f=4&t=41)

It looks like a fun game I will install and let you know how it went.

This is probably the best source - [http://wiki.vdrift.net/Installing_on_Linux](http://wiki.vdrift.net/Installing_on_Linux)

- Dependencies -
Libraries
You must have libsdl ([http://www.libsdl.org/](http://www.libsdl.org/)), libsdl-image, libsdl-net,
libopenal ([http://openal.org/](http://openal.org/)) or libfmod ([http://fmod.org/](http://fmod.org/)), and the
OpenGL libraries installed to play VDrift. To compile, you must also have
the headers (usually the -dev packages, consult your distro's docs) for
these libraries.

The default sound library used by VDrift is OpenAL. FMOD is also supplied
in the Linux release as libfmod-3.74.so. See "FAQ: How to enable FMOD?" if
you'd like to use it. VDrift has not been tested with OpenAL 1.1, only
1.0.

---

### Post by scrypt on 2009-06-08
Hey Goddard..

That's a record reply for me :)

Okay mate, let me know how you get on.

It's driving me about bonkers....

---

### Post by Goddard on 2009-06-08
This might help you...not sure if you used this package or not, but I am running into a different problem then you...mine is a open gl error I am sure, but this installed perfectly on my system and I can get to the main menu of Vdrif - [http://downloads.sourceforge.net/vdrift/VDrift-2007-03-23-minimal.package](http://downloads.sourceforge.net/vdrift/VDrift-2007-03-23-minimal.package)

---

### Post by scrypt on 2009-06-08
. I used these instructions from:-

[http://wiki.vdrift.net/Compiling#Bullet](http://wiki.vdrift.net/Compiling#Bullet)

Make sure you right click on downloaded vdrift folder and go to permissions tab and make executionable""

To configure and install vdrift you need all of these packages:
Use terminal terminaland run:-
 sudo apt-get install libsdl-gfx1.2-4 libsdl-gfx1.2-4-dev libsdl-image1.2 libsdl-image1.2-dev  libsdl-net1.2 libsdl-net1.2-dev libvorbisfile3 bjam jam ftjam 

To get these needed code!!

libsdl-gfx1.2-4
libsdl-gfx1.2-4-dev
libsdl-image1.2
libsdl-image1.2-dev
libsdl-net1.2
libsdl-net1.2-dev
libvorbisfile3
bjam
jam
ftjam
libvorbis-dev
libglew-dev


I downloaded vdrift-2009-02-15.tar.bz2 then opened containing folder by right clicking the vdrift file in the new downloaded box and just dragged it to my Desktop to Extract it the easy way.

then I ran these commands curtesy of:- [http://wiki.vdrift.net/Compiling#Bullet](http://wiki.vdrift.net/Compiling#Bullet)

Eveything seems to be going to plan until I run the last code:- sudo scons install
and I get this error:- 
you do not have the SDL/SDL_net.h headers installed

Here are the commands i run that are okay untill I get to the last one!!

cd ~/Desktop

tar zxvf bullet-2.73-sp1.tgz


tar jxvf vdrift-2009-02-15-src.tar.bz2

Enter Directory:- cd vdrift-2009-02-15

scons

scons release=1

sudo scons install

---

### Post by scrypt on 2009-06-08
Thank's for the link Goddard.

It is the same one I am using but had no l;uck with

---

### Post by scrypt on 2009-06-08
Does anybody know why I could be getting this error. among others when I run this in terminal:-

scrypt-laptop:~/Desktop/vdrift-2009-02-15$ scons

include/collision_detection.h:249: error: ‘class COLLISION_OBJECT’ has no member named ‘GetBulletObject’
scons: *** [build/ai.o] Error 1
scons: building terminated because of errors.

---

### Post by scrypt on 2009-06-08
Any help would be gratly appreciated, before my lapy goes straight out my window.

this is driving me up the wall

i have installed vdrift to my desktop, and all is sweet, right up to sudo scons install

Here are the commands i run that are okay untill I get to the last one!!

cd ~/Desktop

tar zxvf bullet-2.73-sp1.tgz


tar jxvf vdrift-2009-02-15-src.tar.bz2

Enter Directory:- cd vdrift-2009-02-15

scons

scons release=1

sudo scons install

BUT I must admit from here on I'm lost.

Can anyone shed some light and help me get this vdrift game started.

---

### Post by scrypt on 2009-06-08
I use this command to install it-

sudo scons install /home/scrypt/Desktop/vdrift-2009-02-15

and it runs and installs.

Here is the later part of the terminal output after running the above command:-

pleBroadphase.o bullet-2.73/src/BulletCollision/BroadphaseCollision/btDbvtBroadphase.o bullet-2.73/src/BulletCollision/BroadphaseCollision/btAxisSweep3.o bullet-2.73/src/BulletCollision/BroadphaseCollision/btBroadphaseProxy.o bullet-2.73/src/BulletCollision/BroadphaseCollision/btOverlappingPairCache.o -Lbuild -Lsrc -Llib -L/usr/lib -L/usr/X11R6/lib -lSDL -lGL -lGLU -lGLEW -lSDL_image -lSDL_net -lSDL_gfx -lvorbisfile
Install file: "build/vdrift" as "share/games/vdrift/bin/vdrift"
scons: done building targets.

Can anybody with more expierience help me to see where I am going wrong please??

---

### Post by scrypt on 2009-06-08
Im pretty sure this, what was at the bottom of the terminal means something. But I am onsure how to execute it.

Can anyone help??

---

### Post by scrypt on 2009-06-09
Can anybody tell me how to run vdrift???

---

### Post by scrypt on 2009-06-09
Okay I have finally sussed it

I used this site for help :- [http://wiki.vdrift.net/Compiling](http://wiki.vdrift.net/Compiling)

Here are the comands I used to Run Vdrift :-

Because my Desktop is where I downloaded vdrift-2009-02-15  to  :-

Extracted to Desktop

sudo cd ~/Desktop 

tar zxvf bullet-2.73-sp1.tgz  extracted bullet folder

tar jxvf vdrift-2009-02-15-src.tar.bz2  unpacked archive


cd vdrift-2009-02-15    :- change diectory to downloaded vdrift folder

sudo scons
 
sudo scons install

And finally to run game i Use this command:-

scrypt@mark-laptop:~/Desktop/vdrift-2009-02-15$ '/home/srypt/Desktop/vdrift'

Done and dusted

SOLVED by scrypt  :)

---

