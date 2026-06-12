---
title: "OOOQS - KDE outdated"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Chareos on 2005-10-14
Hi there,

I was trying to install the qucklauncher for openoffice, oooqs-kde.

Then I noticed it depends on oo1 while breezy has oo2.

Any updete would be very appreciated, that little app is very useful for who have 512+MB RAM.


Thanks
Fabio

---

### Post by z_pod on 2005-10-14
[QUOTE=Chareos]Hi there,

I was trying to install the qucklauncher for openoffice, oooqs-kde.

Then I noticed it depends on oo1 while breezy has oo2.

Any updete would be very appreciated, that little app is very useful for who have 512+MB RAM.


Thanks
Fabio[/QUOTE]

Hi,

Not kubuntu issue, it seems. Ask nicely to the mantainer to update the package.

Regards

---

### Post by Chareos on 2005-10-14
I'll do that. Do you suggest to file a bug or...?

---

### Post by robert114 on 2006-01-30
I've tried the package as well and it still depends on OpenOffice 1

I've also tried to compile the source code
Compiling worked and installing after i've installed kdebase-dev went all well
and the program did start well with this command: /usr/local/kde/bin/oooqs 
The only problem is it doesn't start OpenOffice2 :-k

---

### Post by f1dave on 2006-01-30
Well, I would say thats to be expected...?

If you can't alter it yourself, it might be an idea to ask the developer(s) as mentioned.

---

### Post by robert114 on 2006-02-02
I've fixed my problem, i've made 2 minor changes the source code so the code works for me right now.

I have attached my code so you folks can compile it for your self. 
But i have to mention, I am not an experiensed programmer so if you run into problem's i'm keen to help you. But i cannot guearantee if i am able to do so!

I will inform the maintainer(s) of the original source code of my change's so let's hope they will update their code and we all can enjoy the quickstarter.

---

### Post by jetpeach on 2006-03-09
thanks, does anyone know if this is fixed now?  i wonder if I can get the update in the repositories now?

---

### Post by Jucato on 2006-03-09
Nope, not yet fixed. It actually isn't just a Kubuntu/KDE situation. I'm not sure if the devs will be fixing it for now, since Dapper is just a month away.

---

### Post by robert114 on 2006-03-09
I'm on dapper and I've just installed the oooqs and it works fine for me right now!

So i think you should be patient for the dapper release!

---

### Post by robert114 on 2006-03-11
I was a little bit to fast with my conclusion, the oooqs wich can be installed from the repos's does indeed install, but from my point of view it doesn't load OpenOffice faster!

So i compiled the new oooqs from [URL="http://segfaultskde.berlios.de/index.php?content=oooqs2"]http://segfaultskde.berlios.de/index.php?content=oooqs2 
[/URL]

This version does work on my system and i'm realy pleased with it!

Before you can compile it for yourself you need to install some dev packages
You need to have the following packages installed on your system:
qt-mt-dev
xlibs-dev
kdelibs-dev

If somebody can give me a very easy and quick how to compile a debian package i'm willing to build a .deb
But i'm affraid this isnt' easy

---

### Post by Jucato on 2006-03-11
um... I wonder if this oooqs will also work in Breezy? And is the loading time reduced considerably?

The loading time of OO.o is one of the things that's making me stick to KOffice. That and the fact that it doesn't start with a "K" :D

---

### Post by JAwuku on 2006-03-19
[QUOTE=robert114]If somebody can give me a very easy and quick how to compile a debian package i'm willing to build a .deb
But i'm affraid this isnt' easy[/QUOTE]

If you enable the "universe" repositories, you can install a program called **checkinstall**. This enables you to compile source code and installs a .deb package on the system.

It's used in place of make install,

so instead of typing

```
./configure
make
sudo make install
```

you just type

```
./configure
make
sudo checkinstall
```

A menu of options comes up, such as name of maintainer, version, name of package, source location etc. which you can alter.

Once finished, it automatically installs the package, and you can use dpkg -r, apt-get remove, adept etc. to remove it.

---

### Post by robert114 on 2006-03-23
I've tried the checkinstall, but it ran into some problem's. I've prelinked my computer! so i'm affraid that's the problem

it stopped with the following error

========================= Installation results ===========================
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/installwatch.so' from LD_PRELOAD cannot be preloaded: ignored.

Copying documentation directory...
/var/tmp/JCfkYkKKjDBEUqjrbCNC/installscript.sh: line 13: 22750 Segmentation fault      mkdir -p "/usr/share/doc/oooqs2-1.0"

****  Installation failed. Aborting package creation.

Cleaning up...OK

---

### Post by robert114 on 2006-07-08
I've made an package based on the latest source code!
But I need somebody to test it! for needed depencies and other unknown problems by me!

JAwuku thanks for your small how-to it worked for me

**Package info**

The package is build for dapper drake
So, it won't work on Breezy

Required depencies are unknown to me!

---

### Post by robert114 on 2006-07-12
Wel, I had 1 unsolved problem: 
OOOQS does starts and loads OpenOffice perfectly but when you close OOo OOOQS doesn't reload OpenOffice.

---

### Post by SURESH123 on 2006-07-12
tRY & tRY TILL U SUCCEED

---

### Post by SURESH123 on 2006-07-12
Sdfgsdfgsdfgsfdg

---

