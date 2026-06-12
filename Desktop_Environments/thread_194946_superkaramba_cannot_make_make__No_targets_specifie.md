---
title: "superkaramba cannot make? make: *** No targets specified and no makefile found.  Stop"
date: 2006-06-12
forum: Desktop Environments
---

### Post by ade234uk on 2006-06-12
I downloaded the source for superkaramba

I then ./configure
ade@ade-desktop:~/Desktop/superkaramba-0.39$ ./configure


And then when I enter the make command in the terminal ade@ade-desktop:~/Desktop/superkaramba-0.39$ make

And I get the following error

make: *** No targets specified and no makefile found.  Stop.

Has anyone else experienced this. look forward to your help.

Many Thanks

---

### Post by chavo on 2006-06-12
Sounds like you don't have development tools installed.

Why don't you just apt-get install superkaramba?

---

### Post by ade234uk on 2006-06-12
I tried that but get the following message

ade234uk@ade234uk-desktop:/$ sudo apt-get install superkaramba
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package superkaramba

Do I need to add more respositories?

---

### Post by Jucato on 2006-06-12
I would recommend installing superkaramba from the repositories, as they will save you a lot of trouble, and the one in repositories and the one you are compiling are the same. You can use your favorite package manager (Adept or Synaptic or something else), or you can do what chavo said.

But if you really want to compile superkaramba, and you know what you are doing, you have to install the metapackage named *build-essential*. This will install everything you need to compile from source code. But again, do this only if you are absolutely sure that this is what you want to do.

---

### Post by bikeman on 2006-06-12
As an earlier poster noted, you will need to install additional packages if you want to use make.
**sudo apt-get install build-essential**
should take care of everything, but you might want to run
**sudo apt-get install make**
after build-essentials to be sure (if it is already installed it will tell you), and a lot of people like to install automake
**sudo apt-get install automake**

Once you have done the above, you should be okay.  If you have any other unmet dependencies, the error messages will tell you - just install all of those as well.  Good luck.

---

### Post by ade234uk on 2006-06-12
Thank you for all your help. I found superKaramba in the respositiries by unmasking some of the urls in the sources list. However I will try the methods of building packages by source using the example above. There are some other things that I cannot find in the repositries like

ksmoothdock

[http://www.kde-apps.org/content/show.php?content=6585](http://www.kde-apps.org/content/show.php?content=6585)

---

### Post by Jucato on 2006-06-12
there's no ksmoothdock in the repositories. There is, however, a KoolDock.
> Dock for KDE with cool visual enhancements
 KoolDock is a fork of the original work of Dang Viet Dung, KSmoothDock 2.1. KoolDock is a dock for KDE with cool visual enhancements and effects.
 Some of it features are: 
 * Display quick launchers to your favourite apps * A builtin task bar * Pager and clock. (Not done yet) * Smooth zooming effect (like Apple's OS X dock) * Transparent Background 
 Homepage: [http://ktown.kde.cl/kooldock/](http://ktown.kde.cl/kooldock/)

It's also in the universe repository. It should be visible now that you've enabled the universe repository (which is what you did when you "unmasked" them).

---

### Post by the_analyzer on 2007-10-16
> **bikeman said:**
> As an earlier poster noted, you will need to install additional packages if you want to use make.
**sudo apt-get install build-essential**
should take care of everything, but you might want to run
**sudo apt-get install make**
after build-essentials to be sure (if it is already installed it will tell you), and a lot of people like to install automake
**sudo apt-get install automake**

Once you have done the above, you should be okay.  If you have any other unmet dependencies, the error messages will tell you - just install all of those as well.  Good luck.

hello, i installed those (so i think, but was a percentage numbers when I pressed enter), anyway, im trying to install anjuta and is very difficult. I unpacked to a directory. I went to the directory with terminal,I wrote

./configure

then when i pressed 

make

was ** No targets specified and no makefile found.



Please help me. I need Anjuta.

---

