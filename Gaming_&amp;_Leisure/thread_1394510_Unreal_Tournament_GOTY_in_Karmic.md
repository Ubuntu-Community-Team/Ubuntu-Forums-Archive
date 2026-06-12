---
title: "Unreal Tournament GOTY in Karmic"
date: 2010-01-30
forum: Gaming &amp; Leisure
---

### Post by earthman on 2010-01-30
Install seems to be broken again:

error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS32

This is after installing the libgtk1.2 package which seems to be necessary to use the "unreal.tournament_436-multilanguage.goty.run" script which seems to be the right one.
Is it my imagination, or does every new release break this game?

---

### Post by ELD on 2010-01-31
Well it is an extremely old game, maybe someone can come up with an installer that can utilise newer software? It is a downside to closed-source games, but hey some of the best games available are closed-source, we just have to deal with it.

---

### Post by pribina on 2010-01-31
Unreal Tournament is one of those native games that run in newer distros without any problems. All you need is an UT GOTY cd and a loki installer for GOTY edition (there is also an installer for standard version and it doesn't work with GOTY). Then you have to install libsdl1.2. That library is necesarry to run most of native linux games.

---

### Post by earthman on 2010-02-01
It's telling me I have the wrong ELF type.

"error while loading shared libraries: libgtk-1.2.so.0: wrong ELF class: ELFCLASS32"

---

### Post by JacobK on 2010-02-11
I finally managed to run it on Karmic, but it's extremely choppy. Extremely as in: 1 frame a second. Does anyone know how to fix this?

---

### Post by OCEAN11 on 2010-03-21
From loading UTgoty in current versions of Ubuntu 64 bit only, this error I believe is the problem with a 32 bit game and a 64 bit extensions operating system.
 
I was able to download the loki installer and type: sh unreal.tournament_436-multilanguage.goty.run and this worked flawlessly in a 32 but version of Ubuntu, there is even problems with 64 bit Windows7 as well, there are native issues with shutting down 1 core for dual core processors, or 3 for quad core processors, also shutting down resources in the background where Windows7 had so many things running in the background, UT99 would not be playable.  I will try to find a solution to this, but from my previous experiences find an older copy of 32 bit Ubuntu, 8.10, 7.10 etc, and this should work without problem, as it did for me.  

One solution would be to partition hard drive and have two installations on same hard drive, and grub menu loader, select which version you want, unless someone can find a way to fix the error: error while loading libraries: libgtk-1.2.so.0:

Here are full instructions to make it work here: [http://ubuntuforums.org/showthread.php?t=289796](http://ubuntuforums.org/showthread.php?t=289796)

---

### Post by Brebs on 2010-03-21
> **OCEAN11 said:**
> shutting down 1 core for dual core processors
Use taskset, to limit the app to 1 core. Example:

taskset -c 1 /usr/bin/wine thief2

---

### Post by OCEAN11 on 2010-04-04
Thanks Brebs,

Where do I add that line or use that?

---

### Post by Brebs on 2010-04-04
In whatever your startup script for the wine program is.

---

### Post by quadomatic on 2010-04-07
I bought UT GOTY on GOG.com, and I was told that the linux installer would work, but I don't really see how...any advice?

---

### Post by earthman on 2010-04-08
Isn't there a way to backport these libraries or something? This game runs on other distros so there must be a way?

---

### Post by quadomatic on 2010-04-10
I got an install working:

> 
If you must then you'll have to get the jaunty packages - 3 in total I think
( in this order for install

[http://packages.ubuntu.com/en/jaunty/libgtk1.2-common](http://packages.ubuntu.com/en/jaunty/libgtk1.2-common)

[http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/en/jaunty/libglib1.2ldbl)

[http://packages.ubuntu.com/en/jaunty/libgtk1.2](http://packages.ubuntu.com/en/jaunty/libgtk1.2)


[http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.goty.run](http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.goty.run)

cd to installer

export SETUP_CDROM=/path/to/cdrom

./unreal.tournament_436-multilanguage.goty.run

this was on Ubuntu 10.04 btw

...Now, my question is, can anyone compile the updated OpenGL renderer for linux?

[http://www.cwdohnal.com/utglr/utglr36src.zip](http://www.cwdohnal.com/utglr/utglr36src.zip)

---

### Post by rasmus91 on 2010-05-14
I'd really like a complete guide on how to get this running on 10.04 64 bit

---

### Post by earthman on 2010-05-14
It's actually not THAT hard, I simply had to download (from debian.org) whichever packages it said was missing. It ended up being 4 or 5. Some have 64-bit versions, some don't. Anyway, the game runs pretty well, though the gamma is kind of dark. Anyone know how to increase gamma in the nvidia driver?

---

