---
title: "Vegastrike installation problems"
date: 2007-05-26
forum: Gaming &amp; Leisure
---

### Post by Mr.Fahrenheit on 2007-05-26
Hello,

I downloaded the install file for Vegastrike, but when I attempt to run it, I get the following:

```
$ sh vegastrike-0.4.3-base.bz2.run 
Verifying archive integrity... All good.
Uncompressing Vegastrike Space Simulator 0.4.3 - Base...........................................................................

/home/[username removed]/.setup15225: error while loading shared libraries: libgdk-1.2.so.0: cannot open shared object file: No such file or directory

```

I'm somewhat new at this, but I'm guessing there's a missing dependency? How do I go about fixing this?

---

### Post by Mr.Fahrenheit on 2007-05-26
Nobody wants to help the newbie out?

---

### Post by yabbadabbadont on 2007-05-26
Open up synaptic and search for libgdk.  The one you need will probably be called libgdk-pixbuf2.  Also, double check the listed dependencies on the vegastrike website.

Edit: Better yet, simply install the one that is already in the Ubuntu repositories....  :p  :D

```
/home/daffy $ aptitude show vegastrike
Package: vegastrike
State: not installed
Version: 0.4.3-5ubuntu3
Priority: optional
Section: universe/games
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 12.5M
Depends: vegastrike-data (>= 0.4.3-1), vegastrike-data (< 0.4.4-1), freeglut3, libalut0, libc6 (>= 2.5-0ubuntu1), libexpat1 (>=
         1.95.8), libgcc1 (>= 1:4.1.2), libgl1-mesa-glx | libgl1, libglib1.2 (>= 1.2.0), libglu1-mesa | libglu1, libgtk1.2 (>=
         1.2.10-4), libjpeg62, libogg0 (>= 1.1.3), libopenal0a, libpng12-0 (>= 1.2.13-4), libsdl-mixer1.2 (>= 1.2.6),
         libsdl1.2debian (>= 1.2.10-1), libstdc++6 (>= 4.1.2), libvorbis0a (>= 1.1.2), libvorbisfile3 (>= 1.1.2), libx11-6,
         libxext6, libxi6, libxmu6, python2.5 (>= 2.5), zlib1g (>= 1:1.2.1)
Description: A 3d space combat game
 Vegastrike is an OpenSource 3d Space Simulator. Currently in Beta development, the project, at version 1.0, is to be a generic
 space simulator. Current features include split-screen play, trading, exploration and of course plenty of shoot 'em up action
 .

```

---

### Post by Mr.Fahrenheit on 2007-05-26
That appears to have worked, but I have no sound. Is this common?

---

### Post by yabbadabbadont on 2007-05-26
```
/home/daffy $ aptitude search vega
p   vegastrike                                              - A 3d space combat game                                           
p   vegastrike-data                                         - Data files for vegastrike                                        
p   vegastrike-music                                        - Music files for vegastrike                                       

```
Do you have all three installed?  As you can see from my first post, I do not have the game installed, so I don't know if having no sound is a common problem.  Search the forums and see what shows up.  ;)

---

