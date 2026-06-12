---
title: "Installed XFCE...now what?"
date: 2004-12-09
forum: Desktop Environments
---

### Post by tbonejo on 2004-12-09
I installed xfce with no problems using their graphical installers, however now it doesnt show up as a session and theres nothing in the menu. What to do?


Thanks,

Tom

---

### Post by WiLLiE on 2004-12-09
sudo nano -w /usr/share/xsessions/xfce.desktop

If you installed XFCE for all then insert this:
```
[Desktop Entry]
Encoding=UTF-8
Name=XFCE4
Comment=This logs you into XFCE4.
Exec=/usr/local/bin/startxfce4
TryExec=/usr/local/bin/startxfce4
Icon=
Type=Application
```
or If you installed XFCE for current user only then insert this (Replace _USER_ with current user name)
```
[Desktop Entry]
Encoding=UTF-8
Name=XFCE4
Comment=This logs you into XFCE4.
Exec=/home/_USER_/local/bin/startxfce4
TryExec=/home/_USER_/local/bin/startxfce4
Icon=
Type=Application
```Save the file (ctrl+o)

---

### Post by danip on 2005-01-24
I also have the issuse of xfce not appearing in my menu.  I made the file but it still does not show up.

---

### Post by poofyhairguy on 2005-01-24
[QUOTE=tbonejo]I installed xfce with no problems using their graphical installers, however now it doesnt show up as a session and theres nothing in the menu. What to do?


Thanks,

Tom[/QUOTE]

its a good idea to install XFCE from their Debian respotory.

---

### Post by danip on 2005-01-24
I found the xfce installer off of their website so i am trying to use that however i am recieveing errors here is what it says 

```
## Configuring libxfce4util
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for AIX... no
checking for library containing strerror... none required
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
!! Failed to configure libxfce4util, see the errors above
!! for details on the problem. 
```

---

### Post by doni on 2005-01-24
you probably haven't installed the c++ compiler.

switch to a terminal and type (as root)

```
apt-get install g++
``` 

this should fix your problem.

---

### Post by danip on 2005-01-24
It asks for the cd to install g++...since i dont have a copy of it anymore is there a way to tell it to get it off the internet?

---

### Post by ratpoison on 2005-01-24
[QUOTE=tbonejo]I installed xfce with no problems using their graphical installers, however now it doesnt show up as a session and theres nothing in the menu. What to do?


Thanks,

Tom[/QUOTE]
=====================
If you boot into runlevel 3, after logging in, just type startxfce4

---

### Post by danip on 2005-01-27
Ok so I have xfce working and its very nice except for a few problems i cant seem to figure out.  There is no battery moniter for my laptop, that is something I kind of need.  How can I get a wireless link indicator?  How do I access things in the computer>system configuration menu such as synaptic and networking, since I use those very frequently.

by the way id like to be able to add things like that to my panel if thats possible.  Theres other things id like to add such as gaim and dcgui-qt

---

### Post by jensyt on 2005-01-27
[QUOTE=danip]Ok so I have xfce working and its very nice except for a few problems i cant seem to figure out.  There is no battery moniter for my laptop, that is something I kind of need.  How can I get a wireless link indicator?  How do I access things in the computer>system configuration menu such as synaptic and networking, since I use those very frequently.

by the way id like to be able to add things like that to my panel if thats possible.  Theres other things id like to add such as gaim and dcgui-qt[/QUOTE]
You can add launchers to those applications by simply right-clicking one of the panel's edges and selected "Add new item". Then just select what you want, in this case a launcher.
As for those other things like wireless link indicator - I'd try to check out the XFCE Goodies package.
```
sudo apt-get install xfce4-goodies
```
Then you would add them to the panel the same way you added the launcher.

---

### Post by danip on 2005-01-27
Ok i got the xfce4-goodies package but nothings has happened.  I checked the website to see what to do and they said to do this command 

```
steve@blackbetty ~ $ killall -USR1 xfce4-panel

```

I did that and still nothing happened.

---

### Post by dis360 on 2008-02-02
Right click your panel and choose "Add New Item" the tools you installed with the goodies package are now listed here, add the items as needed..

---

