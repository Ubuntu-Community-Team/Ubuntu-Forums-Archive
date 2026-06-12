---
title: "Compiling SDL"
date: 2009-08-13
forum: Gaming &amp; Leisure
---

### Post by shiggydiggy on 2009-08-13
I'm trying to get dosbox installed, so i found me a guide on compiling it.
[http://www.dosbox.com/wiki/BuildingDOSBox](http://www.dosbox.com/wiki/BuildingDOSBox)
It wants me to compile SDL
> ./configure
make
make install
but when i go make install, it goes
> stanley@stanley-desktop:~/Desktop/SDL-1.2.13$ make install
/bin/bash ./build-scripts/mkinstalldirs /usr/local/bin
/usr/bin/install -c -m 755 sdl-config /usr/local/bin/sdl-config
/usr/bin/install: cannot create regular file `/usr/local/bin/sdl-config': Permission denied
make: *** [install-bin] Error 1
stanley@stanley-desktop:~/Desktop/SDL-1.2.13$ 


---

### Post by rCXer on 2009-08-13
In Ubuntu you don't have build SDL.  [Here](http://ubuntuforums.org/showthread.php?p=7357952#post7357952) is a thread describing how to build DOSBox in Ubuntu.  You can also download the new DOSBox [here](http://packages.ubuntu.com/karmic/dosbox)

---

### Post by shiggydiggy on 2009-08-13
*disclaimer: i am a n00b, like still looking for the start button*
ok...
I ran that code in the terminal... where is dosbox downloaded to?

---

### Post by rCXer on 2009-08-13
> **shiggydiggy said:**
> *disclaimer: i am a n00b, like still looking for the start button*
ok...
I ran that code in the terminal... where is dosbox downloaded to?

I'm a newbie as well as my signature suggests. Welcome to freedom :P
wget should have put it in your current directory which probably is "/home/YourUserName" if you haven't changed directories. After building it just type...
```

dosbox

```
...to run it.  To find where the binary is, enter...
```

which dosbox

```
Mine is in "/usr/local/bin/dosbox"

---

### Post by Grishka on 2009-08-13
there's no need to compile, get it from [here](http://www.getdeb.net/app/Dosbox), for example.

---

### Post by rCXer on 2009-08-13
...and listen to Grishka because he's not a newbie ;)

---

### Post by Perfect Storm on 2009-08-13
You could also try Dosbox Game Launcher.

Guide; [http://gwos.org/doku.php/guides:64bit:dosboxgui](http://gwos.org/doku.php/guides:64bit:dosboxgui)

---

### Post by shiggydiggy on 2009-08-14
i want to be at least a 'bit' hardcore so i want to compile (just to make myself feel 1337 again LOL)

ok, i downloaded dosbox manually and ran

tar -xvf dosbox-0.73.tar.gz
cd dosbox-0.73
./autogen.sh
./configure
make
sudo make install

near the end it did this:

checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!
stanley@stanley-desktop:~/stuffs/dosbox-0.73$ make
make: *** No targets specified and no makefile found.  Stop.
stanley@stanley-desktop:~/stuffs/dosbox-0.73$ sudo make install
make: *** No rule to make target `install'.  Stop.
stanley@stanley-desktop:~/stuffs/dosbox-0.73$

do i need to update my sdl?

---

### Post by Grishka on 2009-08-14
you need SDL 'dev' package. [this one](apt://libsdl1.2-dev).

---

### Post by shiggydiggy on 2009-08-14
sweet!
also, how would i go about compiling it into different instruction sets like i386, i686, x86_64 etc and all the options that go with those

---

### Post by Grishka on 2009-08-14
you aim to be 1337, so... ```
./configure --help
```
should answer your question. :p
but do note that you won't be able to compile for 64-bit architecture on a 32-bit system.

---

### Post by shiggydiggy on 2009-08-15
ok, what about on a 32-bit ubuntu on a 64-bit system?

---

### Post by Sockerdrickan on 2009-08-15
use getlibs

---

