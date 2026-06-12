---
title: "alien arena doesn't work"
date: 2008-01-06
forum: Gaming &amp; Leisure
---

### Post by docorange on 2008-01-06
Hi
I just downloaded from the net the zip file which contains alien arena's newest version. I read the "readme" file, which says "Type ./crx to run the game". I did so, but what I get is this
error while loading shared libraries: libXxf86dga.so.1: cannot open shared object file: No such file or directory
I got two questions
1 what the hell is that?
2 How can I fix it?
Thanks
docorange

---

### Post by Hightide on 2008-01-06
HI docorange

find the the alien arena folder on your system

mine is in   /home/paul/games/alienarena2007

click twice on the crx file in the folder . thats it!

i downloaded game today and its running fine.

---

### Post by DoktorSeven on 2008-01-06
Whenever you get those kinds of errors, you're missing a library that the game needs to run.

Your friend in these cases is **apt-file** -- it will search for a file name that is inside of a package.

```

sudo apt-get install apt-file
sudo apt-file update 
(this goes to grab things from the repositories like apt-get update, but for the files contained in those packages, and will take a while)
apt-file search libXxf86dga.so.1

```

This brings back the following:
```

$ apt-file search libXxf86dga.so.1
libxxf86dga1: usr/lib/libXxf86dga.so.1
libxxf86dga1: usr/lib/libXxf86dga.so.1
libxxf86dga1: usr/lib/libXxf86dga.so.1
libxxf86dga1: usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1: usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1: usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1-dbg: usr/lib/debug/usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1-dbg: usr/lib/debug/usr/lib/libXxf86dga.so.1.0.0
libxxf86dga1-dbg: usr/lib/debug/usr/lib/libXxf86dga.so.1.0.0

```

Ignore any that end in -dev or -dbg and install the one it finds:

**sudo apt-get install libxxf86dga1**

---

### Post by docorange on 2008-01-07
well, I tried to do as you suggested me, Doktorseven, but what seems weird to me is that apt tells me I already have this package, so I don't understand what the problem can be.
thanks
docorange

---

### Post by Cappy on 2008-01-07
Perhaps you are running 64-bit ubuntu. If ```
uname -m
```
returns x86_64 you are.

Try getlibs available from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by docorange on 2008-01-07
I knew perfectly well I was running ubuntu amd64. What puzzles me is that those problems shouldn't arise, as I installed every i386 library and all this 32 bit stuff
docorange

---

### Post by Cappy on 2008-01-07
> **docorange said:**
> I knew perfectly well I was running ubuntu amd64. What puzzles me is that those problems shouldn't arise, as I installed every i386 library and all this 32 bit stuff
docorange

The 32-bit library you need cannot be installed using apt-get because it is not included in the ia32-libs package and nor is it in any of the lib32* packages.

Install getlibs, change to the game directory where crx is located and run
```
sudo getlibs crx
```

If you have problems with that you can also use
```
sudo getlibs -p libxxf86dga1
```

---

### Post by docorange on 2008-01-08
Thanks cappy, alien arena works now... but only graphically, sound effects and music suck a lot... Do you know some way I can fix them?
Thanks again
docorange

---

### Post by kvonb on 2008-01-08
-

---

### Post by docorange on 2008-01-08
well, I didn't mean to be rude. If I seemed so, I'm sorry. Anyway, I didn't mention I was using ubuntu 64-bit, just because I thought it was an unimportant detail.
docorange

---

### Post by kvonb on 2008-01-08
-

---

### Post by Butthead on 2008-01-08
> **docorange said:**
> Thanks cappy, alien arena works now... but only graphically, sound effects and music suck a lot... Do you know some way I can fix them?
Thanks again
docorange

Hmm, did you try running it using the ./crx-sdl command (as listed in the README file)? :confused:

---

### Post by docorange on 2008-01-09
sure, using the standard crx, I get a really bad and trashy sound. Using crx.sdl, I get a better sound, but it's still very trashy
docorange

---

### Post by Brebs on 2008-01-09
alienarena works fine on 64-bit - [example](http://aur.archlinux.org/packages.php?do_Details=1&ID=14398) (which compiles from source).

Its sound effects are not top-quality yet, though ;)

---

