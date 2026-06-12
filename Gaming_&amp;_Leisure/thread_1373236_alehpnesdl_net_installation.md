---
title: "alehpne/sdl_net installation"
date: 2010-01-05
forum: Gaming &amp; Leisure
---

### Post by NS-5 on 2010-01-05
hi all, just registered here because i really need some help
i'm trying to play excalibur:mr and i have to install sdl and alpehone before i do that

i've installed sdl but when i type
./configure inside my AlephOne-20091015$  folder i get this:
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for unistd.h... (cached) yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for sdl-config... /usr/local/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking SDL_image.h usability... no
checking SDL_image.h presence... no
checking for SDL_image.h... no
checking SDL_ttf.h usability... no
checking SDL_ttf.h presence... no
checking for SDL_ttf.h... no
checking SDL_net.h usability... no
checking SDL_net.h presence... no
checking for SDL_net.h... no
configure: error: You need SDL_net to run Aleph One.

and i'm pretty sure its installed because when i look at my Synaptic Package Manager 
libsdl-net1.2 has a green box next to it, which means it's installed, same thing goes for sdl-image and sdl-ttf

i don't know whats going on.  the configure file is probablly looking in the wrong place, right??

i'm using Ubuntu 9.10 Karmic Koala
any help is greatly appreciated 
thank you

---

### Post by linuxuser9999 on 2010-01-05
Sounds like you need to install the development files. In this case, the libsdl-net1.2-dev package. Same thing for sdl_image and sdl-tff.

---

### Post by NS-5 on 2010-01-05
but i don't get it
when i look at my snyaptic package manager
it has  a green box next to all the libsdl dev packages
they are not supposed to be missing
i'll resart my system again and see what happens

---

### Post by NS-5 on 2010-01-05
no luck 
still giving same erros with everything installed
:confused::confused::confused:

---

### Post by linuxuser9999 on 2010-01-05
Try going into a terminal (Applications/Accessories/Terminal) and type **sudo apt-get install libsdl-net1.2-dev**
If it says that it's already the newest version, try removing it by typing
**sudo apt-get remove libsdl-net1.2-dev**, then try reinstalling again by typing sudo apt-get install libsdl-net1.2-dev
then try ./configure again

If you're still getting the same problem, there's probably something wrong with the package or the excalibur configure script. I wouldn't know what else to do. However I was able to install and run the game myself. Game is not bad at all.

---

### Post by NS-5 on 2010-01-05
alright, i did what you told me
yes it said it was at its newest version
this is what i got:
sudo apt-get install libsdl-net1.2-dev
[sudo] password for thor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl-net1.2-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 scorched3d-data airstrike-common libwxgtk2.6-0
  boswars-data libkdegames5 libdns50 binutils-static libalut0 libwxbase2.6-0
  libavfilter0 liblua5.1-0 linux-headers-2.6.31-14-generic libavdevice52
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

then i removed:
sudo apt-get remove libsdl-net1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 scorched3d-data airstrike-common libwxgtk2.6-0
  boswars-data libkdegames5 libdns50 binutils-static libalut0 libwxbase2.6-0
  libavfilter0 liblua5.1-0 linux-headers-2.6.31-14-generic libavdevice52
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libsdl-net1.2-dev
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 98.3kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 185129 files and directories currently installed.)
Removing libsdl-net1.2-dev ...

then i reinstalled:
sudo apt-get install libsdl-net1.2-dev
[sudo] password for thor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 scorched3d-data airstrike-common libwxgtk2.6-0
  boswars-data libkdegames5 libdns50 binutils-static libalut0 libwxbase2.6-0
  libavfilter0 liblua5.1-0 linux-headers-2.6.31-14-generic libavdevice52
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libsdl-net1.2-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/17.3kB of archives.
After this operation, 98.3kB of additional disk space will be used.
Selecting previously deselected package libsdl-net1.2-dev.
(Reading database ... 185120 files and directories currently installed.)
Unpacking libsdl-net1.2-dev (from .../libsdl-net1.2-dev_1.2.7-2_i386.deb) ...
Setting up libsdl-net1.2-dev (1.2.7-2) ...

i hit ./configure inside my AlephOne-20091015$ folder and got the same error I posted above :/
FEAKING ********

checking for SDL - version >= 1.2.0... yes
checking SDL_image.h usability... no
checking SDL_image.h presence... no
checking for SDL_image.h... no
checking SDL_ttf.h usability... no
checking SDL_ttf.h presence... no
checking for SDL_ttf.h... no
checking SDL_net.h usability... no
checking SDL_net.h presence... no
checking for SDL_net.h... no
configure: error: You need SDL_net to run Aleph One.

---

