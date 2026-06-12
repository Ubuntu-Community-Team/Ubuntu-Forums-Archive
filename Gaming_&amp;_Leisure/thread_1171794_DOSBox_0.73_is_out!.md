---
title: "DOSBox 0.73 is out!"
date: 2009-05-27
forum: Gaming &amp; Leisure
---

### Post by BoyOfDestiny on 2009-05-27
So a new version is out (look at the changelog at dosbox.com)

I wanted to provide a way for any Ubuntu user (this includes multiple architectures) to use it right away. 

Disclaimer: I've had the dependencies (read as what you need to build dosbox) installed for years, so if I forgot one, let me know.

Just cut n' paste this into terminal

```
sudo apt-get install build-essential autoconf automake
sudo apt-get build-dep dosbox
wget "http://superb-west.dl.sourceforge.net/sourceforge/dosbox/dosbox-0.73.tar.gz"
tar -xvf dosbox-0.73.tar.gz
cd dosbox-0.73
./autogen.sh
./configure
make
sudo make install 
```

What this does, gets build dependencies (let me know if one is missing)
Downloads the tarball from sourceforge, extracts it, builds it then installs.

This should be completely automatic, perhaps move it to Guides/Tutorials.

Thanks in advance regarding feedback

P.S. There are some DOS games here 
[http://liberatedgames.com/](http://liberatedgames.com/)
The games there have been licensed to be at least free to download, and some completely open sourced. :)

---

### Post by rCXer on 2009-05-27
Thanks.  Your instructions worked perfectly :popcorn:

---

### Post by CharmyBee on 2009-05-27
The best part of this release is the scancode fix for ubuntu so the keys actually operate like they should since 8.10 broke it.

> **BoyOfDestiny said:**
> 
P.S. There are some DOS games here 

[http://classicdosgames.com](http://classicdosgames.com) has all the shareware essentials that made DOS gaming what it is. Recommended (and not illegal either, probably one of the only legal dos games sites on earth)

---

### Post by Junkieman on 2009-05-30
Compiled and running :) Had this urge to play Warcraft II again ;) Hahaha!

---

### Post by Dark Aspect on 2009-05-30
> apt-get: build-dep dosbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list


Remember to check Source Code in System-->Administration-->Software Sources. Great little howto, worked great. thxs

---

### Post by Grishka on 2009-05-30
alright! I've put packages for jaunty in [my ppa](https://launchpad.net/~thir/+archive/ppa).

---

### Post by ZX3Junglist on 2009-07-11
> **Grishka said:**
> alright! I've put packages for jaunty in [my ppa](https://launchpad.net/~thir/+archive/ppa).

Thanks!

---

### Post by Grishka on 2009-07-11
note that 0.73 is in Karmic now, you can [grab that version](http://packages.ubuntu.com/karmic/dosbox), if you'd rather not use some random guy's PPA. :)

---

### Post by tznomani on 2009-08-16
Can you tell me where to look for the executable after I've followed your instructions to configure, compile, and install DOSBox 0.73 ?

Thanks

---

### Post by Perfect Storm on 2009-08-16
just type **dosbox**

If you want it with game launcher (comes included latest dosbox): [http://gwos.org/doku.php/guides:64bit:dosboxgui](http://gwos.org/doku.php/guides:64bit:dosboxgui)

---

### Post by tarun1793 on 2009-08-24
mine is giving up an error 

```

checking for ranlib... ranlib
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: *** SDL version 1.2.0 not found!

```

what to do???

---

### Post by whaevr on 2009-08-24
@tarun1793
```

sudo apt-get install libsdl1.2-dev

```

---

### Post by SolarOnline on 2009-08-24
Dosbox support forums should cover all these issues?

---

### Post by tarun1793 on 2009-08-25
now it has stopped at : 
```


make[3]: Entering directory `/home/tarun/Desktop/dosbox-0.73/src/gui'
g++ -DHAVE_CONFIG_H -I. -I../..  -I../../include -I/usr/local/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -g -O2  -MT sdl_mapper.o -MD -MP -MF .deps/sdl_mapper.Tpo -c -o sdl_mapper.o sdl_mapper.cpp
sdl_mapper.cpp: In function ‘void MAPPER_StartUp(Section*)’:
sdl_mapper.cpp:2389: error: ‘struct SDL_SysWMinfo’ has no member named ‘info’
sdl_mapper.cpp:2390: error: ‘struct SDL_SysWMinfo’ has no member named ‘info’
sdl_mapper.cpp:2391: error: ‘struct SDL_SysWMinfo’ has no member named ‘info’
make[3]: *** [sdl_mapper.o] Error 1
make[3]: Leaving directory `/home/tarun/Desktop/dosbox-0.73/src/gui'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tarun/Desktop/dosbox-0.73/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tarun/Desktop/dosbox-0.73'
make: *** [all] Error 2


```

---

### Post by Junkieman on 2009-08-25
> **tarun1793 said:**
> now it has stopped at : 
```
‘struct SDL_SysWMinfo’ has no member named ‘info’
```

That obviously means that your version of SDL does not have the required structures in the headers that Dosbox is looking for.

I suggest opening a new thread, or going to the [Dosbox forums ]("http://vogons.zetafleet.com/index.php?c=7")for support, you will get much better feedback that way :)

When you do, keep these in mind: What version of SDL did you install, the latest is 1.2.13. I can't check the requirements for Dosbox right now, check the README or INSTALL files and make sure you have the required version.

---

### Post by rCXer on 2010-05-14
DOSBox 0.74 has been released!
```

sudo apt-get install build-essential autoconf automake
sudo apt-get build-dep dosbox
wget "http://downloads.sourceforge.net/project/dosbox/dosbox/0.74/dosbox-0.74.tar.gz"
tar -xvf dosbox-0.74.tar.gz
cd dosbox-0.74
./autogen.sh
./configure
make
sudo make install

```

---

