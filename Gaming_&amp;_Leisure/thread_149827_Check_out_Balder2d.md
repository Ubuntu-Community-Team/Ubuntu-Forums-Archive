---
title: "Check out Balder2d"
date: 2006-03-24
forum: Gaming &amp; Leisure
---

### Post by holomorph on 2006-03-24
Hey,  I just released version 0.9 of [balder2d]("http://balder.sourceforge.net/balder2d/"), which adds AI so you don't need friends to play with anymore, among other cool enhancements.

Balder2d is a 2d shooter, in zero gravity.  Players control probes which can stick to (and push off again from) walls, rotate, and fire projectiles.  The objective is, of course, to destroy the other probes and earn points.

Installation on an Ubuntu system should be fairly simple.  You need to make sure you have SDL, SDL_image, SDL_mixer, SDL_gfx, Python, and boost filesystem installed:

```
$ sudo apt-get install libsdl1.2 libsdl-image1.2 libsdl-mixer1.2 libsdl-gfx1.2 python libboost-filesystem 
```

then you need to go to the [Downloads]("http://sourceforge.net/project/showfiles.php?group_id=49631") page, and grab the guichan and hawkNL .deb packages from the 0.8 release, and balder2d_0_9.tar.gz from the 0.9 release.  Go to the directory where you downloaded those two debs and type:

```
$ sudo dpkg -i hawknl_HawkNL1.70-1_i386.deb guichan-0.4.0_0.4.0-1_i386.deb
```

then unzip balder2d_0_9.tar.gz wherever you like, and run './balder2d' from the bin/ directory wherever you unziped it.  

I hope you enjoy it.  I'd really like some feedback about the installation, if it works for you or not, etc.  Also Feedback on the game is welcome.  Thanks!

Bjorn

[IMG]http://balder.sourceforge.net/balder2d/balder2d_0_9-1.png[/IMG]

---

### Post by Duncan_Idaho on 2006-03-24
sounds like a fun game to me
I gonna try the installation, thanks for the game :-D

---

### Post by Duncan_Idaho on 2006-03-25
ok, I installed it and the debs
but then I tried to run the bin, and then...```
vault-dweller@Vault-13:~/balder2d/bin$ ./balder2d
./balder2d: error while loading shared libraries: libguichan_sdl.so.0: cannot open shared object file: No such file or directory

```

how can I fix taht?:confused:

---

### Post by holomorph on 2006-03-25
I thought libguichan_sdl.so.0 should be installed in /usr/local/lib by the guichan .deb package, but if it's not there, in should be a simlink to /usr/local/lib/libguichan_sdl.so.0.0.0

So:
```

sudo ln -s /usr/local/lib/libguichan_sdl.so.0.0.0 /usr/local/lib/libguichan_sdl.so.0

```
should fix it.

If that libguichan_sdl.so.0.0.0 is also not there, then either there is something wrong with the guichan package, or you didn't install it right.  

I'm pretty much a novice as far as making .deb packages, so it's quite possible I screwed something up.  Must learn more :)

Let me know how it goes.

Bjorn

---

### Post by holomorph on 2006-03-25
ok, I checked the .deb, and it definately should install the symlink as well in /usr/local/lib so, check and see if those files are there, if not, guichan didn't get installed correctly.  If they are, then for some reason /usr/local/lib is not in the library search path (?).

I just had a thought, perhaps you can't do two packages at once with 'dpkgs -i ...'

so you might have to install the hawknl and guichan packages one at a time:

```

$  sudo dpkg -i hawknl_HawkNL1.70-1_i386.deb
$  sudo dpkg -i guichan-0.4.0_0.4.0-1_i386.deb

```

---

### Post by Duncan_Idaho on 2006-03-26
I tried both of your suggestions, but didn't have any luck
first I tried "dpkg -i"ing both pakages one by one, tried to run the game and tells me the  same error  :-k 
then I tried the simlink, but it tell me that the target lib already was there ](*,) 
so I don't know what to do now :confused:

---

### Post by holomorph on 2006-03-27
So apparently it's not looking in /usr/loca/lib for shared libraries; check your /etc/ld.so.conf file.  Here's what mine looks like:
```

/usr/X11R6/lib
/usr/lib/atlas
/usr/local/lib

```

add /usr/local/lib to that file, and you probably have to run ldconfig again:
```

$ sudo ldconfig

```

Does anyone know a way around having to update ldconfig?

---

