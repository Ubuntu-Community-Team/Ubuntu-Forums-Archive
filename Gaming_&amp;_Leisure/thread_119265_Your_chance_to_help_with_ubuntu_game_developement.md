---
title: "Your chance to help with ubuntu game developement"
date: 2006-01-19
forum: Gaming &amp; Leisure
---

### Post by holomorph on 2006-01-19
Hi,
I've been working on a game for the past 16 months or so (on and off).  It's called [Balder2d]("http://balder.sourceforge.net/balder2d/index.php") and is a 2d shooter in zero gravity (inspired by "Ender's Game"). 

(Instructions for installing if you want to try it out are included at the bottom of this post)
[Edit] I have built some binary packages, which should make things a bit easier if you just want to try playing.  See [this]("http://ubuntuforums.org/showthread.php?t=122253") thread.
[end Edit]

Balder2d is nearing completion, but is still lacking that polish which
would give it a "finished" feel. An experienced developer (or two) is
desired to help clean up, test, and add finishing touches to the code.

It would also be quite nice if someone would be willing to make packages so it's easy for people to install.

Although Balder2d is primarily for playing against your friends, there
is also the opportunity (it would be really nice to have the option of
playing alone) of adding some AI players to the game.

The current state of the code in CVS is up to the version 0.8 goals (see
the roadmap) 


Anyway, here is what you'll have to do if you'd like to try Balder2d (grab a friend, it's not much fun by yourself).  You'll have to build it yourself, so here's what you need:

First, you'll need SDL and SDL_image and SDL_mixer developement libraries:
```

 $ sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev
```

You'll also need boost filesystem:
```
$ sudo apt-get install libboost-filesystem-dev
```

You also need the [guichan]("http://guichan.sourceforge.net/") library, [download]("http://guichan.sourceforge.net/downloads.shtml") the cvs snapshot (the 0.4 release is actually what I use, but it has a small bug that makes it fail to compile with gcc 4.0, which is fixed in cvs).
Unzip that somewhere convenient and run:
```

$ ./autogen.sh
$ ./configure
$ make
$ sudo make install

```
alternatively you can grab the 0.4 release, and add a "virtual ~ListModel() {};" to the ListModel class in include/guichan/listmodel.hpp.  Then skip the autogen step in the above commands.

Also note (as pointed out by Harleen below) that you can use 'sudo checkinstall' instead of 'sudo make install' which will build and install a standard binary package, which means you can use your standard package management utilities to uninstall.

The last library that balder2d needs is GNE (which depends on HawkNL) so:
[download]("http://www.hawksoft.com/download/") HawkNL 1.7 beta 1 (HawkNL17b1src.zip).  
Unzip that somewhere convenient and do:
```

$ make -f makefile.linux
$ sudo make -f makefile.linux install
$ cp include/*.h /usr/local/include/

```
The last step is necesarry because there is an error in the makefile; it fails to copy all of the hawknl headers.  Only nl.h is copied.

now that you have HawkNL installed, you can build and install GNE:
```

$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gnelib login
$ cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gnelib co -P gnelib
$ cd gnelib
$ ./fixlinux.sh
$ make
$ sudo make install 

```
Just press enter when prompted for a password (leave it blank).

Whew!
hopefully all that worked and I haven't forgotten anything.  It's finally time to grab and build balder2d:
```

$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/balder login
$ cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/balder co -P balder2d
$ cd balder2d
$ jam

```
 
That should do it, though, if you don't have jam installed you will have to install that (there is a package so just apt-get install jam) before building balder.

If all went well, you should be able to run balder2d by:
```

$ cd bin
$ ./balder2d

```


That's it.  If it didn't work for you I'd really like to hear about it, so I can update these instructions, make them more clear and/or add things that I missed.  

I hope you enjoy it, and if you get inspired to help that's even better!

Bjørn

---

### Post by holomorph on 2006-01-21
also, if the above instructions do work for you, I would like to know that too.

---

### Post by Harleen on 2006-01-23
I think the effort to get this program running is scaring people away. But I just tried it.

[QUOTE=holomorph]also, if the above instructions do work for you, I would like to know that too.[/QUOTE]

OK, here's the story of my miserable failure.

Since you already pointed out, that guichan 0.4 won't compile on gcc4 I took the CVS snapshot and generated a configure file for it (with lots of error messages). Configure went fine, but couldn't generate the Makefiles (failed to open Makefile.in). As I'm not too familar with automake & Co. I stopped at that point and just used the .deb files from that site.

The HawkNL library installed just fine.

The last step I've done was this:

```
$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gnelib login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/gnelib
CVS password:
cvs [login aborted]: end of file from server (consult above messages if any)
```

Why it it asking for a password for an anonymous login?

---

### Post by simplyw00x on 2006-01-23
You press enter when the password question appears; it's part of CVS to ask for a pass.

---

### Post by Harleen on 2006-01-23
I've already tried that - of course. Also "anonymous" won't work, just like a mail address.

---

### Post by holomorph on 2006-01-23
Hi, 
First of all I want to say thanks for giving this a try and letting me know what didn't work.  It's very helpful for me in writing a set of instructions that will work (maybe even a script to make it easier eventually).

> **Harleen]
Since you already pointed out, that guichan 0.4 won't compile on gcc4 I took the CVS snapshot and generated a configure file for it (with lots of error messages). Configure went fine, but couldn't generate the Makefiles (failed to open Makefile.in). As I'm not too familar with automake & Co. I stopped at that point and just used the .deb files from that site.
[/QUOTE]
Hmm,  unfortunately those .deb files won't work because they were build with a 3.x series version of gcc.   When you compile balder with gcc 4, the libraries it links with need to use the same.

If you can't get the CVS snapshot to build, it's pretty easy to fix the 0.4 source release so that it does (I probably should have pointed this out before). 
From the guichan bugs forum:
[QUOTE]Just a very quick bug: compiling Guichan (release and snapshot) fails when using gcc 4.0, because of a minor warning that is treated as an error. Gcc is simply warning about a class with virtual functions that doesn't have an explicitely defined virtual destructor. The incriminated class is gcn::ListModel, in include/guichan/listmodel.hpp.

Adding a "virtual ~ListModel() {} said:**
> 
I've ammended the instructions in my first post to mention this option, and noticed I forgot the './autogen.sh' step if you use the cvs version.

[QUOTE=Harleen]
The last step I've done was this:

```
$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/gnelib login
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/gnelib
CVS password:
cvs [login aborted]: end of file from server (consult above messages if any)
```

As simplyw00x has pointed out, you should just have to press enter, leaving the password blank.  I don't know why that won't work for you :(

you might just try the next step, and check out the module.  It's been my experience that the login step is not really necesarry, but it is in the sourceforge instructions on how to check things out, so it seems like there must be a reason for that.

I hope that helps, and thanks again for giving it a shot.

Bjørn

---

### Post by Harleen on 2006-01-23
For some strange reason CVS is working now. I'd blame sourceforge for the previous error. Back to start and next try...

---

### Post by Harleen on 2006-01-23
The installation of the HawkNL library didn't went so smooth as I thought. The file libhawk.h is not copied during install, so I had to do it manually. This looks to me like a mistake in the Makefile.
Other than that, everything worked without any problem:
[ATTACH]5509[/ATTACH]

Just a ittle note to your installation guide: You sometimes missed the "sudo" before "make install". And I'd prefer "sudo checkinstall", or "sudo checkinstall make -f makefile.linux install" for HawkNL.

---

### Post by holomorph on 2006-01-23
Great, thanks!
I'm glad you got it to work.  

I hadn't heard of checkinstall, that's pretty nifty.  I'll make note of that.

---

