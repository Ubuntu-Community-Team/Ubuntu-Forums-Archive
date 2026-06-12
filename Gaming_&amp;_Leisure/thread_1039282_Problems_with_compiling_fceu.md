---
title: "Problems with compiling fceu"
date: 2009-01-14
forum: Gaming &amp; Leisure
---

### Post by khelben1979 on 2009-01-14
I get this when I try to compile the latest version of fceu 2.0.3:

81-224-174-203-o1123:/home/bear/fceu# sudo scons install
scons: Reading SConscript files ...
platform:  posix
Checking for C library SDL... (cached) yes
Checking for C library z... (cached) yes
Checking for C library lua5.1... (cached) yes
Checking for C library lua... (cached) no
Checking for zenity... yes
Checking for C function asprintf()... (cached) yes
Checking for C++ library GL... (cached) yes
base CPPDEFINES: ['PSS_STYLE=1', ['_GNU_SOURCE', '1'], '_REENTRANT', '_S9XLUA_H', 'FRAMESKIP']
base CCFLAGS: -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL
$__RPATH
scons: done reading SConscript files.
scons: Building targets ...
g++ -o src/state.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1
 -D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr
/include/lua5.1 src/state.cpp
src/state.cpp: In function 'int SubWrite(std::ostream*, SFORMAT*)':
src/state.cpp:121: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:121: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp:132: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:132: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
src/state.cpp: In function 'bool ReadStateChunk(std::istream*, SFORMAT*, int)':
src/state.cpp:200: error: invalid conversion from 'void*' to 'uint8*'
src/state.cpp:200: error:   initializing argument 1 of 'void FlipByteOrder(uint8*, uint32)'
scons: *** [src/state.o] Error 1
scons: building terminated because of errors.

With Debian Etch I was able to use an older version of the fceu emulator, but when I recently upgraded to Lenny this emulator stopped working, unfortunately. And now I'm trying to get the latest version working because of this.

The version which is supplied with Debian Lenny haven't worked for me with this cpu platform.

Is there anyone here who has any suggestion on how I should solve this?

(Right now I have a source package from Ubuntu which has been labeled 0.6.1, but I'm more keen on getting this new version working, if it's possible.)

---

### Post by donkyhotay on 2009-01-14
According to your scons output you're missing the lua library. Try installing that and trying again.
```
sudo apt-get install liblua50-dev
```
If this doesn't work there is another version on liblua available in the repos which may work instead.
```
sudo apt-get install liblua40-dev
```
I'm not certain which version fceu requires to compile correctly.

---

### Post by khelben1979 on 2009-01-14
I already have them installed.

However I have another problem which I'm trying to solve related to this. I need python header files in order to compile libgtk. Do you know where I can find them? (I've search the distro without any luck)

I need libgtk to work in order to run the python gui for this fceu emulator.

---

### Post by donkyhotay on 2009-01-14
I don't know about your second post but the problem with compiling is with liblua. Not only do you have 
Checking for C library lua... (cached) no
but you also have 
g++ -o src/state.o -c -Wall -Wno-write-strings -Wno-sign-compare -O2 -DHAVE_ASPRINTF -DOPENGL -DPSS_STYLE=1
-D_GNU_SOURCE=1 -D_REENTRANT -D_S9XLUA_H -DFRAMESKIP -I/usr/include/SDL -I/usr/local/include/lua5.1 -I/usr
/include/lua5.1 src/state.cpp
right before all of the errors with state.cpp finally cause the compiler to fail completely. There are many different versions of liblua-dev available in the repos so my guess is still having the wrong version. Beyond installing all of them and trying again or reading through the fceu compiling instructions I don't know how to resolve your issue.

---

### Post by khelben1979 on 2009-01-14
Okay.

Another thing which is important in this is that it really doesn't matter what version of fceu it comes down to and installing it from source isn't that important either.

I only want a working 8 bit emulator on this Debian Lenny system. Are there any alternatives to the fceu emulator for this hardware platform? Do you know? (I have spent hours looking for alternatives on this myself..)

---

### Post by Grishka on 2009-01-14
mednafen. in addition to NES, it also emulates many other systems.

---

### Post by khelben1979 on 2009-01-15
The version of Mednafe which came with Debian Lenny haven't been working.

---

### Post by Grishka on 2009-01-15
> **khelben1979 said:**
> The version of Mednafe which came with Debian Lenny haven't been working.

what's wrong with it? bear in mind that mednafen is a cli application. post errors or try to compile from source. anyway, lenny is a future debian release. since you installed a testing distro, you might want to report broken packages, starting here: [http://www.debian.org/Bugs/](http://www.debian.org/Bugs/). also, you might have more luck with solving your problems if you inquire on debian forums: [http://forums.debian.net/](http://forums.debian.net/). also, there are quite a few NES emulators available, check out this post: [http://ubuntuforums.org/showthread.php?t=612289](http://ubuntuforums.org/showthread.php?t=612289).

---

### Post by khelben1979 on 2009-03-28
I still don't have a working fceu emulator in the Debian Lenny system over here. And fceu can't be executed from an x terminal either, because it can't find the command, although it is installed according to the dselect installer. Oh well... Some day I might get this working again. :confused: It worked very good in the older version of Debian, but with Lenny it just don't work and I have other problems as well, but that's a different chapter.

---

