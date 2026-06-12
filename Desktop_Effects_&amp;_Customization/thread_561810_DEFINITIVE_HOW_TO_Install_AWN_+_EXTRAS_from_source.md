---
title: "DEFINITIVE HOW TO: Install AWN + EXTRAS from source"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by narehart on 2007-09-28
I've read a couple of guides on here and other places describing how to install AWN in all it's glory.  While all right, I feel most of these guides were incomplete and one of them absolutely refused to work on Gutsy.  So, in response, I've made this guide.  I'll show you how to install AWN plus the EXTRAS from source.
[B]
1. Install AWN[/B]

First, prepare your system. Open a terminal and enter the following:

```
sudo apt-get install build-essential subversion automake1.9
```

Next, Install the dependencies:

```
sudo apt-get install bzr libgtk2.0-dev libwnck-dev libwnck-common  librsvg2.0-c libgconf2-dev libglib2.0-dev libgnome2-dev libgnome-desktop-2 librsvg2.0-c libgnome-desktop-dev libdbus-glib-1-dev gnome-common libxcomposite-dev libxdamage-dev librsvg2-dev libgtop2-dev libgnome-menu-dev libgnome-menu2 libgnome-menu-dev librsvg2.0-cil librsvg2-2 librsvg2-common librsvg2-dev libgtop2-7 libgtop2-common libgtop2-dev python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
```
 
Finally, open a terminal and build AWN from source like so:

```
bzr co http://bazaar.launchpad.net/~awn-core/awn/trunk avant-window-navigator
cd avant-window-navigator
./autogen.sh && make && sudo make install
```

Next we'll install the AWN-Extras so keep that terminal open.

**2. Install AWN-Extras**

First install the dependencies: 

```
sudo apt-get install build-essential automake1.9 autotools-dev bzr libgnome-menu-dev librsvg-dev
```

Get the source code from BZR:

```
bzr co http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk awn-extras
```

Move to the applets directory:

```
cd awn-extras/awn-applets/awn-core-applets/
```

Compile and install:

```
./autogen.sh && make && sudo make install
```

Then simply type this to start AWN:

```
avant-window-navigator
```

**3. Some Final Notes**

If you would like to add a Control Applet for your media player to the AWN dock as well as some other more experimental applets, check out my other guide here:[http://ubuntuforums.org/showthread.php?t=561495]("http://ubuntuforums.org/showthread.php?t=561495")

Remember, AWN and the AWN-Extras are constantly being updated so it's a good idea to recompile this every once in a while to make sure have the latest and greatest AWN Bling. Check out Fizz's post below for auto update script.

Thanks!

---

### Post by DeusExodos on 2007-09-28
I can get up to ./autogen.sh perfectly fine. When I actually do type in ./autogen.sh i get:

checking for headers required to compile python extensions... not found
configure: error: could not find Python headers

When I then type in make or sudo make install it says:

pedro@pedrolaptop:~/avant-window-navigator$ make
make: *** No targets specified and no makefile found.  Stop.

I'm not sure what to do from here on. Thanks.

---

### Post by narehart on 2007-09-28
I edited the post to add the dependencies.  See if that helps.

---

### Post by waldorsockbat on 2007-09-28
-laptop:/$ bzr co [http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk](http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk) awn-extras
bzr: ERROR: [Errno 13] Permission denied: 'awn-extras'


Awn is working but I get this error when I move on to the extras.

---

### Post by gmc on 2007-09-28
Hi

Thought I'd try out your howto. compiling avant went well, but trying to compile the extra's I get the following error:

```

checking for DEPS... configure: error: Package requirements (gtk+-2.0
                  awn
                  libwnck-1.0
                  libglade-2.0
                  libgnome-menu
                  gnome-desktop-2.0
                  librsvg-2.0
                  libgtop-2.0) were not met:

No package 'libgnome-menu' found
No package 'librsvg-2.0' found
No package 'libgtop-2.0' found

```Gord

Edited: Above problem is solved by apt-get install librsvg2-dev libgtop2-dev libgnome-menu-dev 

You'll also want to run ldconfig (as root). This will allow avant to see the linavn.so library that was built.

Enjoy & Thanks

---

### Post by fizz on 2007-09-28
a little script I made to update bzr and compile..
```

cd ~
nano updateawn.sh

```
Enter the following into that file..
```

cd awn-extras
bzr update
cd awn-applets/awn-core-applets
./autogen.sh ; make ; sudo make install
cd ~/avant-window-navigator
bzr update
./autogen.sh ; make ; sudo make install
cd ..
echo "complete"

```
ctrl-x  then y to save

```
chmod 755 updateawn.sh
```

then to update and install the updates, simply do
```
cd ~
./updateawn.sh
```

Have fun :)

---

### Post by narehart on 2007-09-28
> **waldorsockbat said:**
> ERROR: [Errno 13] Permission denied: 'awn-extras'

Errno 13 means permission denied.  Check to make sure you have the appropriate permissions to create the folder and try running with sudo.

---

### Post by narehart on 2007-09-28
> **gmc said:**
> Hi

Thought I'd try out your howto. compiling avant went well, but trying to compile the extra's I get the following error:

```

checking for DEPS... configure: error: Package requirements (gtk+-2.0
                  awn
                  libwnck-1.0
                  libglade-2.0
                  libgnome-menu
                  gnome-desktop-2.0
                  librsvg-2.0
                  libgtop-2.0) were not met:

No package 'libgnome-menu' found
No package 'librsvg-2.0' found
No package 'libgtop-2.0' found

```Gord

Edited: Above problem is solved by apt-get install librsvg2-dev libgtop2-dev libgnome-menu-dev 

You'll also want to run ldconfig (as root). This will allow avant to see the linavn.so library that was built.

Enjoy & Thanks

Thanks.  I edited the dependencies to include the mentioned files.

---

### Post by lichtgestalt on 2007-09-28
bzr is also missing in the dependencies even so its no real dependency you need it to install.

---

### Post by narehart on 2007-09-28
Thanks, Fizz.  I edited the original post to mention your script.  Very nice!

---

### Post by narehart on 2007-09-28
> **lichtgestalt said:**
> bzr is also missing in the dependencies even so its no real dependency you need it to install.

Thanks, added bzr.

---

### Post by IceReaver75 on 2007-09-28
I got everything installed and running but some of the extra applets wont run.  I just get a line on the bar or nothing at all.  Those that don't run are:  

Workspace Switcher
Notification Area
Stack
Volume Control Applet
Gmail

Any help on fixing this will be greatly appreciated.

I got Stack to work on a system restart but the others still won't work

---

### Post by DeusExodos on 2007-09-28
I still get the error:

autoreconf: automake failed with exit status: 1

when I type in ./autogen.sh

---

### Post by waldorsockbat on 2007-09-28
Forgive me for the first post  it was like 5am and I am still new at compiling. aia tried again but this is what I got.

~/awn-extras/awn-applets/awn-core-applets$ sudo ./autogen.sh && make && sudo make install
Password:
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac: installing `./install-sh'
configure.ac: installing `./missing'
src/Makefile.am:1: whitespace following trailing backslash
src/clock/Makefile.am: installing `./compile'
src/clock/Makefile.am: installing `./depcomp'
src/stack/Makefile.am:14: whitespace following trailing backslash
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.34... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtk+-2.0
                  awn
                  libwnck-1.0
                  libglade-2.0
                  libgnome-menu
                  gnome-desktop-2.0
                  librsvg-2.0
                  libgtop-2.0) were not met:

No package 'libgnome-menu' found
No package 'librsvg-2.0' found
No package 'libgtop-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more detail


I ran the dependencys again and got this

/$ sudo apt-get install build-essential automake1.9 autotools-dev bzr libgnome-menu-dev librsvg-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
automake1.9 is already the newest version.
autotools-dev is already the newest version.
autotools-dev set to manual installed.
bzr is already the newest version.


Yes I am a noob at this and I am sure I missed 1 simple thing.lol

---

### Post by narehart on 2007-09-28
Waldorsockbat

```
 sudo apt-get install libgnome-menu2 libgnome-menu-dev librsvg2.0-cil librsvg2-2 librsvg2-common librsvg2-dev libgtop2-7 libgtop2-common libgtop2-dev
```

Try installing these packages and see if that works. I am going to add them to the dependencies. Oh, and don't worry about being a "noob".  That's what these forums are for.

---

### Post by narehart on 2007-09-28
> **DeusExodos said:**
> I still get the error:

autoreconf: automake failed with exit status: 1

when I type in ./autogen.sh

Are you in the correct directory? Are you running the whole line? ```
 ./autogen.sh && make && sudo make install
```

---

### Post by narehart on 2007-09-28
> **IceReaver75 said:**
> I got everything installed and running but some of the extra applets wont run.  I just get a line on the bar or nothing at all.  Those that don't run are:  

Workspace Switcher
Notification Area
Stack
Volume Control Applet
Gmail

Any help on fixing this will be greatly appreciated.

I got Stack to work on a system restart but the others still won't work

Unfortunately, none of those work for me either but these are still experimental applets.  I'm sure they  will be functioning correctly in the near future.

---

### Post by IceReaver75 on 2007-09-28
> **narehart said:**
> Unfortunately, none of those work for me either but these are still experimental applets.  I'm sure they  will be functioning correctly in the near future.

Alright thanks.  Like I stated before I got the stack to work with a system reboot.  You can also get the Notifacation Area applet to work if you delete the Notifacation Area from your Gnome panel.  I found that out by going to the Avant Forums.

---

### Post by waldorsockbat on 2007-09-28
$ sudo apt-get install libgnome-menu2 libgnome-menu-dev librsvg2.0-cil librsvg2-2 librsvg2-common librsvg2-dev libgtop2-7 libgtop2-common libgtop2-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnome-menu2 is already the newest version.
E: Couldn't find package librsvg2.0-cil

I am trying to install this on my wife's laptop with 32 bit. I have this on my 64 bit gusty box that was installed from the repos  and works fine. I love stacks awesome feature!

---

### Post by narehart on 2007-09-28
> **waldorsockbat said:**
> $ sudo apt-get install libgnome-menu2 libgnome-menu-dev librsvg2.0-cil librsvg2-2 librsvg2-common librsvg2-dev libgtop2-7 libgtop2-common libgtop2-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnome-menu2 is already the newest version.
E: Couldn't find package librsvg2.0-cil

I am trying to install this on my wife's laptop with 32 bit. I have this on my 64 bit gusty box that was installed from the repos  and works fine. I love stacks awesome feature!

sudo apt-get install librsvg2.0-cil.  See if that works.

---

### Post by waldorsockbat on 2007-09-29
no go, Couldn't find

---

### Post by narehart on 2007-09-29
Well. I'm sorry my guide failed you. I don't know why you couldn't find the package.  It's in the repositories.  Maybe someone else looking on this thread will be able to help you.

---

### Post by ST.x on 2007-10-01
> **waldorsockbat said:**
> no go, Couldn't find

Get it from here: [http://packages.ubuntu.com/gutsy/libs/librsvg2.0-cil](http://packages.ubuntu.com/gutsy/libs/librsvg2.0-cil)
edit: oh with [librsvg2.0-cil]("http://packages.ubuntu.com/gutsy/libs/librsvg2.0-cil") since its only for gutsy, do we really need that one? 
Meanwhile do we need **librsvg2.0-c** ? I cant find that one anywhere.

---

### Post by narehart on 2007-10-02
> **ST.x said:**
> Get it from here: [http://packages.ubuntu.com/gutsy/libs/librsvg2.0-cil](http://packages.ubuntu.com/gutsy/libs/librsvg2.0-cil)
edit: oh with [librsvg2.0-cil]("http://packages.ubuntu.com/gutsy/libs/librsvg2.0-cil") since its only for gutsy, do we really need that one? 
Meanwhile do we need **librsvg2.0-c** ? I cant find that one anywhere.

thanks I added it.

---

### Post by ST.x on 2007-10-02
> **narehart said:**
> thanks I added it.
So for feisty 64bit do I still need to install [http://packages.ubuntu.com/gutsy/libs/librsvg2.0-cil](http://packages.ubuntu.com/gutsy/libs/librsvg2.0-cil)

And also what's up with **librsvg2.0-c**, I cant find that anywhere?

---

### Post by ST.x on 2007-10-02
Well I went on to compile awn anyway and that seemed to go well (but I didn't install **librsvg2.0-c or **[librsvg2.0-cil]("http://packages.ubuntu.com/gutsy/libs/librsvg2.0-cil") since I couldn't find versions for feisty).

I haven't done the extras yet but I get this when launching awn:

> seynthan@seynthan-lappy:~$ avant-window-navigator
avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

---

### Post by Y2J on 2007-10-07
@ST.x:
i got rid of this problem, simply some dependency where missing, after nstalling the list of package in this post:
[https://answers.launchpad.net/awn/+question/10821](https://answers.launchpad.net/awn/+question/10821)

which is:

$ sudo apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common

and recompiled awn-curves everything seems ok:

$ cd avant-window-navigator

$ ./autogen.sh && make && sudo make install

$ cd awn-extras/awn-applets/awn-core-applets/

$ ./autogen.sh && make && sudo make install

$avant-window-navigator

---

### Post by TedGarvin on 2007-10-27
> **narehart said:**
> Waldorsockbat

```
 sudo apt-get install libgnome-menu2 libgnome-menu-dev librsvg2.0-cil librsvg2-2 librsvg2-common librsvg2-dev libgtop2-7 libgtop2-common libgtop2-dev
```

Try installing these packages and see if that works. I am going to add them to the dependencies. Oh, and don't worry about being a "noob".  That's what these forums are for.

Thanks.  That worked, but i'm still having problems with some applets appearing only as lines and I can't get any launchers to appear.  Other than that, it seems to work great.

---

### Post by ebe326 on 2007-10-28
I'm getting the same error as st.x. I tried the recommended fix but still get the same error.

david@home-desktop:~$ avant-window-navigator
avant-window-navigator: error while loading shared libraries: libawn.so.0: cannot open shared object file: No such file or directory

I think the install went ok. Just this error when trying to run. Thanks for any help.

david

---

### Post by grizzlylock on 2007-10-29
Hi, I'm a noob, but thanks to your forum I think I'm moving up in the ranks.  Anyways, I can't get this to compile right.  I have 7.04 and here is the output I'm receiving.



steven@steven-desktop:~/awn-extras/awn-applets/awn-core-applets$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
src/stacks/Makefile.am:4: whitespace following trailing backslash
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gconftool-2... /usr/bin/gconftool-2
./configure: line 20096: syntax error near unexpected token `0.34'
./configure: line 20096: `IT_PROG_INTLTOOL(0.34)'



I would appreciate any help.

---

### Post by jal4568 on 2007-10-29
Hi, I installed AWN over the weekend and tried to install EXTRAS today. However, I keep getting this error on the last step: 
```
jessica@user-12lm5oe:~/awn-extras/awn-applets/awn-core-applets$ ./autogen.sh && make && sudo make install
./autogen.sh: 2: autoreconf: not found
jessica@user-12lm5oe:~/awn-extras/awn-applets/awn-core-applets$ 
```

I've gone back and double-check my dependencies. I have everything but something's going wrong in this last step. I'm a bit new to Ubuntu so it's entirely possible I'm missing something obvious. :)

---

### Post by grizzlylock on 2007-10-30
I think I had the same problem at one point while trying to install the extras.  Although, now I'm stuck on another roadblock with that, I believe installing automake  and autotools-dev fixed that problem.  The long apt-get commands like 
sudo apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common

didn't seem to work right for me because the command would stop when it reached one it couldn't find and the rest in the command would be ignored.  I ended up running apt-get install on every one individually to make sure the depends were there.  That fixed the error for me, and I believe it was the same error.  Also, I believe I installed a program called csh and that also made things go a little further in the compilation.  You can get that with apt-get csh also.

---

### Post by jal4568 on 2007-10-30
Thank you Grizzlylock! I apparently had the same problem. When I ran sudo apt-get in smaller groups, they installed fine (apparently I did NOT have all my dependencies). 

However, now I'm getting this error after the ./autogen.sh command. It works for a bit and then provides this:

```
checking for DEPS... configure: error: Package requirements (gtk+-2.0
                  awn
                  libwnck-1.0
                  libglade-2.0
                  libgnome-menu
                  gnome-desktop-2.0
                  librsvg-2.0
                  libgtop-2.0
                  glib-2.0
                  dbus-1
                  dbus-glib-1
                  libsexy
                  gconf-2.0
                  gdk-2.0
                  gdk-pixbuf-2.0
                  libnotify) were not met:

No package 'awn' found
No package 'libgnome-menu' found
No package 'libsexy' found
No package 'libnotify' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

Grizzlylock, you mentioned another roadblock? Is this where you are getting stuck now?  If adjusting the environment variables is necessary, how would I do that? Or would it be better to try something else? :confused:

Sorry for all the questions but I really am new to the whole installing from source experience.

---

### Post by deusxechelon on 2007-10-30
Ouch. I got this:

```

deusxechelon@deuslinux:~/avant-window-navigator/avant-window-navigator$ ./autogen.sh && make && sudo make install
/usr/bin/gnome-autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.61
checking for automake >= 1.9...
  testing automake-1.10... not found.
  testing automake-1.9... found 1.9.6
checking for libtool >= 1.5...
  testing libtoolize... found 1.5.24
checking for glib-gettext >= 2.2.0...
  testing glib-gettextize... found 2.14.1
checking for intltool >= 0.30...
  testing intltoolize... found 0.36.2
checking for pkg-config >= 0.14.0...
  testing pkg-config... found 0.22
Checking for required M4 macros...
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./configure.in
Running libtoolize...
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Running glib-gettextize... Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize...
Running aclocal-1.9...
aclocal:configure.in:93: warning: macro `AM_GCONF_SOURCE_2' not found in library
Running autoconf...
configure.in:93: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
deusxechelon@deuslinux:~/avant-window-navigator/avant-window-navigator$ 



```

Translation?

---

### Post by deusxechelon on 2007-10-30
::sigh::

Okay resolved that with

```

sudo apt-get install libgconf2-dev

```

now im getting:

configure: error: could not find Python headers

---

### Post by grizzlylock on 2007-10-30
Re: DEFINITIVE HOW TO: Install AWN + EXTRAS from source
Thank you Grizzlylock! I apparently had the same problem. When I ran sudo apt-get in smaller groups, they installed fine (apparently I did NOT have all my dependencies).

However, now I'm getting this error after the ./autogen.sh command. It works for a bit and then provides this:

Code:

checking for DEPS... configure: error: Package requirements (gtk+-2.0
                  awn
                  libwnck-1.0
                  libglade-2.0
                  libgnome-menu
                  gnome-desktop-2.0
                  librsvg-2.0
                  libgtop-2.0
                  glib-2.0
                  dbus-1
                  dbus-glib-1
                  libsexy
                  gconf-2.0
                  gdk-2.0
                  gdk-pixbuf-2.0
                  libnotify) were not met:

No package 'awn' found
No package 'libgnome-menu' found
No package 'libsexy' found
No package 'libnotify' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Grizzlylock, you mentioned another roadblock? Is this where you are getting stuck now? If adjusting the environment variables is necessary, how would I do that? Or would it be better to try something else?

Sorry for all the questions but I really am new to the whole installing from source experience.


No worries about the questions.  I'm very, very new myself and this forum almost single handedly taught me all i've learned so far ( not much).  That's what it's for and this is the first time I've had to post because usually someone else is having the same probs.


I did actually just have that problem and this is how i got past that:
I used synaptic and installed anything (regardless of versions) that were related to the deps.
(this might not be a good idea, but synaptic seems to warn you when it's an older version and so on)

I also ran:

sudo apt-get install libawn-bzr
sudo apt-get install libawn-bzr-dev

apparently I hadn't met those deps either.

after all of that ./autogen.sh worked, but now my make is messed up

---

### Post by grizzlylock on 2007-10-30
Now this is the error I'm running into when I run make

daemon.c:85: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'G_awn_border'
daemon.c:86: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'G_awn_bg'
daemon.c:87: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'G_awn_text'
daemon.c: In function 'notify_daemon_notify_handler':
daemon.c:1002: warning: passing argument 1 of 'set_notification_arrow' from incompatible pointer type
daemon.c:1004: warning: passing argument 1 of 'move_notification' from incompatible pointer type
daemon.c:1012: warning: passing argument 1 of 'set_notification_arrow' from incompatible pointer type
daemon.c: In function 'awn_applet_factory_initp':
daemon.c:1249: error: 'G_awn_bg' undeclared (first use in this function)
daemon.c:1249: error: (Each undeclared identifier is reported only once
daemon.c:1249: error: for each function it appears in.)
daemon.c:1257: error: 'G_awn_text' undeclared (first use in this function)
daemon.c:1268: error: 'G_awn_border' undeclared (first use in this function)
make[6]: *** [awnnotificationdaemon_la-daemon.lo] Error 1
make[6]: Leaving directory `/home/steven/Desktop/awn-extras/awn-applets/awn-core-applets/src/awn-notification-daemon/src/daemon'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/steven/Desktop/awn-extras/awn-applets/awn-core-applets/src/awn-notification-daemon/src/daemon'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/steven/Desktop/awn-extras/awn-applets/awn-core-applets/src/awn-notification-daemon/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/steven/Desktop/awn-extras/awn-applets/awn-core-applets/src/awn-notification-daemon'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/steven/Desktop/awn-extras/awn-applets/awn-core-applets/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steven/Desktop/awn-extras/awn-applets/awn-core-applets'
make: *** [all] Error 2
steven@steven-desktop:~/Desktop/awn-extras/awn-applets/awn-core-applets$ 

any ideas?


btw how do you guys get the code in a little window of its own?

---

### Post by ANtrah on 2007-10-30
ATI X1300 APG + 7.10 :guitar:

---

### Post by jal4568 on 2007-10-30
Well, it's not working for me yet......But I have made progress. Grizzlylock's last bit of advice got me to some similar error messages he was getting: 
```

daemon.c:100: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'G_awn_border'
daemon.c:101: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'G_awn_bg'
daemon.c:102: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'G_awn_text'
daemon.c: In function 'notify_daemon_notify_handler':
daemon.c:1019: warning: passing argument 1 of 'set_notification_arrow' from incompatible pointer type
daemon.c:1021: warning: passing argument 1 of 'move_notification' from incompatible pointer type
daemon.c:1029: warning: passing argument 1 of 'set_notification_arrow' from incompatible pointer type
daemon.c: In function 'awn_applet_factory_initp':
daemon.c:1294: error: 'G_awn_bg' undeclared (first use in this function)
daemon.c:1294: error: (Each undeclared identifier is reported only once
daemon.c:1294: error: for each function it appears in.)
daemon.c:1302: error: 'G_awn_text' undeclared (first use in this function)
daemon.c:1313: error: 'G_awn_border' undeclared (first use in this function)
daemon.c:1365: warning: passing argument 2 of 'g_timeout_add' from incompatible pointer type
make[6]: *** [awnnotificationdaemon_la-daemon.lo] Error 1
make[6]: Leaving directory `/home/jessica/awn-extras/awn-applets/awn-core-applets/src/awn-notification-daemon/src/daemon'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/jessica/awn-extras/awn-applets/awn-core-applets/src/awn-notification-daemon/src/daemon'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/jessica/awn-extras/awn-applets/awn-core-applets/src/awn-notification-daemon/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jessica/awn-extras/awn-applets/awn-core-applets/src/awn-notification-daemon'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jessica/awn-extras/awn-applets/awn-core-applets/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jessica/awn-extras/awn-applets/awn-core-applets'
make: *** [all] Error 2
jessica@user-12lm5oe:~/awn-extras/awn-applets/awn-core-applets$ 

```

Right now, I'm kinda at a loss. I'm going to dig through the forums to see if anyone's had a similar problem. :-k

PS - Grizzlylock, you can add the format your code in a box by (1) selecting the code text and (2) clicking the '#' button at the top of the post entry form. The code should show up in a box when you preview the post.

---

### Post by grizzlylock on 2007-10-31
I think I'm just going to give up on compiling extras from source.  It compiled without a glitch in gutsy, but I reverted back to feisty because I couldn't get other things such as macmenu to compile right in gutsy.  

You can, however, make some of the links that the extra applets provide right in awn.  i.e. the link that takes you directly to 'my computer' or home, whatever location you wish by creating a launcher with the command nautilus /home/[username].

Does anyone have any idea how to make a launcher for the show desktop feature?

---

### Post by jmariani on 2007-11-04
Try:

$ sudo apt-get install libsexy-dev
$ sudo apt-get install libnotify-dev
$ ./configure
$ make
$ sudo make install

and there you go.

---

### Post by alize on 2007-11-05
i tried this but it didn't work for me, how do i uninstall everything i just did so I can start from scratch from the beginning.

Thanks

---

### Post by jmariani on 2007-11-05
That's what I did:

1) Download AWN
[https://launchpad.net/awn/0.2/0.2.1/+download/avant-window-navigator-0.2.1.tar](https://launchpad.net/awn/0.2/0.2.1/+download/avant-window-navigator-0.2.1.tar)
2) Unzip it.
3) Go to the folder.
4) Run ./configure
5) Run make
6) Run sudo make install

It should overwrite everything.

Same for the extras. Download them from:

[https://launchpad.net/awn-extras/0.2.1/0.2.1/+download/awn-extras-applets-0.2.1.tar](https://launchpad.net/awn-extras/0.2.1/0.2.1/+download/awn-extras-applets-0.2.1.tar)

And do the same.

---

### Post by mattchess on 2007-11-25
I don't get an awn-core-applets subdirectory....I get an awn-extras-applets sub instead

assume that is where I should be doing the final steps from?

EDIT:  Did not work for me - see below...

autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --copy
/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/gconf-1.m4:4: warning: underquoted definition of AM_PATH_GCONF
/usr/share/aclocal/gconf-1.m4:71: warning: underquoted definition of AM_GCONF_SOURCE
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.ac: installing `./install-sh'
configure.ac: installing `./missing'
src/awn-notification-daemon/src/daemon/Makefile.am: installing `./compile'
src/awn-notification-daemon/src/daemon/Makefile.am: installing `./depcomp'
src/lastfm/icons/Makefile.am:2: whitespace following trailing backslash
autoreconf: Leaving directory `.'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.34... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... yes
checking dbus version... 1.1.1
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating src/arss/Makefile
config.status: creating src/arss/Core/Makefile
config.status: creating src/awn-meebo/Makefile
config.status: creating src/awn-meebo/profile/Makefile
config.status: creating src/awn-notification-daemon/Makefile
config.status: creating src/awn-notification-daemon/data/Makefile
config.status: creating src/awn-notification-daemon/po/Makefile.in
config.status: creating src/awn-notification-daemon/src/Makefile
config.status: creating src/awn-notification-daemon/src/daemon/Makefile
config.status: creating src/awnsystemmonitor/Makefile
config.status: creating src/battery-applet/Makefile
config.status: creating src/battery-applet/icons/Makefile
config.status: creating src/BlingSwitcher/Makefile
config.status: creating src/cairo-menu/Makefile
config.status: creating src/calendar/Makefile
config.status: creating src/calendar/google/Makefile
config.status: creating src/calendar/google/atom/Makefile
config.status: creating src/calendar/google/gdata/Makefile
config.status: creating src/calendar/google/gdata/apps/Makefile
config.status: creating src/calendar/google/gdata/base/Makefile
config.status: creating src/calendar/google/gdata/calendar/Makefile
config.status: creating src/calendar/google/gdata/docs/Makefile
config.status: creating src/calendar/google/gdata/spreadsheet/Makefile
config.status: creating src/calendar/images/Makefile
config.status: creating src/comic/Makefile
config.status: creating src/comic/images/Makefile
config.status: creating src/digg/Makefile
config.status: creating src/digg/profile/Makefile
config.status: creating src/digg/profile/Cache/Makefile
config.status: creating src/digitalClock/Makefile
config.status: creating src/filebrowser/Makefile
config.status: creating src/gmail/Makefile
config.status: creating src/gmail/Themes/Makefile
config.status: creating src/gmail/Themes/Default/Makefile
config.status: creating src/lastfm/Makefile
config.status: creating src/lastfm/icons/Makefile
config.status: creating src/main-menu/Makefile
config.status: creating src/media-control/Makefile
config.status: creating src/media-control/icons/Makefile
config.status: creating src/media-icon-back/Makefile
config.status: creating src/media-icon-back/icons/Makefile
config.status: creating src/media-icon-next/Makefile
config.status: creating src/media-icon-next/icons/Makefile
config.status: creating src/media-icon-play/Makefile
config.status: creating src/media-icon-play/icons/Makefile
config.status: creating src/MiMenu/Makefile
config.status: creating src/MiMenu/icons/Makefile
config.status: creating src/showdesktop/Makefile
config.status: creating src/notification-area/Makefile
config.status: creating src/plugger/Makefile
config.status: creating src/PyClock/Makefile
config.status: creating src/PyClock/Themes/Makefile
config.status: creating src/PyClock/Themes/Plain-Clock/Makefile
config.status: creating src/PyClock/Themes/SBB/Makefile
config.status: creating src/PyClock/Themes/Tango/Makefile
config.status: creating src/python-test/Makefile
config.status: creating src/quit-applet/Makefile
config.status: creating src/quit-applet/icons/Makefile
config.status: creating src/separator/Makefile
config.status: creating src/volume-control/Makefile
config.status: creating src/volume-control/Themes/Makefile
config.status: creating src/volume-control/Themes/Black/Makefile
config.status: creating src/volume-control/Themes/Tango/Makefile
config.status: creating src/stacks/Makefile
config.status: creating src/stacks/icons/Makefile
config.status: creating src/switcher/Makefile
config.status: creating src/trash/Makefile
config.status: creating src/trasher/Makefile
config.status: creating src/tsclient-applet/Makefile
config.status: creating src/tsclient-applet/icons/Makefile
config.status: creating src/weather/Makefile
config.status: creating src/weather/images/Makefile
config.status: creating src/weather/locale/Makefile
config.status: creating src/weather/locale/es/Makefile
config.status: creating src/weather/locale/es/LC_MESSAGES/Makefile
config.status: creating src/weather/locale/fr/Makefile
config.status: creating src/weather/locale/fr/LC_MESSAGES/Makefile
config.status: creating src/weather/locale/nb/Makefile
config.status: creating src/weather/locale/nb/LC_MESSAGES/Makefile
config.status: creating src/weather/locale/nn/Makefile
config.status: creating src/weather/locale/nn/LC_MESSAGES/Makefile
config.status: creating src/weather/locale/pt/Makefile
config.status: creating src/weather/locale/pt/LC_MESSAGES/Makefile
config.status: creating src/wobblyzini/Makefile
config.status: creating src/wobblyzini/icons/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
cd . && /bin/bash /home/matthew/awn-extras/awn-applets/awn-extras-applets/missing --run autoheader
autom4te: cannot open autom4te.cache/requests: Permission denied
autoheader: '/usr/bin/autom4te' failed with exit status: 1
make: *** [config.h.in] Error 1


Not sure what I am doing wrong...seemed to work fine on my laptop (this is my desktop).  I am running 64 bit gutsy

Thanks for your help...

---

### Post by Evelyn on 2008-02-07
I keep on getting the "make: *** No targets specified and no makefile found.  Stop." whenever I try to run "make"  below is what was in terminal hoping it will help solve the problem.



rie-rie@dell:~$ sudo apt-get install build-essential automake1.9 autotools-dev bzr libgnome-menu-dev librsvg-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
automake1.9 is already the newest version.
autotools-dev is already the newest version.
bzr is already the newest version.
E: Couldn't find package librsvg-dev
rie-rie@dell:~$ sudo apt-get install build-essential automake1.9 autotools-dev bzr libgnome-menu-dev librsvg2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
automake1.9 is already the newest version.
autotools-dev is already the newest version.
bzr is already the newest version.
The following packages were automatically installed and are no longer required:
  libclan2c2a-jpeg libclan2c2a-sound libclanlib2c2a libclan2c2a-vorbis
  libclan2c2a-gui libclan2c2a-png libmikmod2 libssl0.9.7 libclan2c2a-mikmod
  hermes1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libbz2-dev libcroco3-dev libgsf-1-dev
The following NEW packages will be installed:
  libbz2-dev libcroco3-dev libgnome-menu-dev libgsf-1-dev librsvg2-dev
0 upgraded, 5 newly installed, 0 to remove and 1 not upgraded.
Need to get 630kB of archives.
After unpacking 2695kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libbz2-dev 1.0.3-6build1 [31.9kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libcroco3-dev 0.6.1-1build1 [138kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgnome-menu-dev 2.18.0-0ubuntu3 [73.1kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgsf-1-dev 1.14.3-1ubuntu2 [228kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main librsvg2-dev 2.16.0-0ubuntu2 [159kB]
Fetched 630kB in 14s (43.0kB/s)                                                
Selecting previously deselected package libbz2-dev.
(Reading database ... 154141 files and directories currently installed.)
Unpacking libbz2-dev (from .../libbz2-dev_1.0.3-6build1_i386.deb) ...
Selecting previously deselected package libcroco3-dev.
Unpacking libcroco3-dev (from .../libcroco3-dev_0.6.1-1build1_i386.deb) ...
Selecting previously deselected package libgnome-menu-dev.
Unpacking libgnome-menu-dev (from .../libgnome-menu-dev_2.18.0-0ubuntu3_i386.deb) ...
Selecting previously deselected package libgsf-1-dev.
Unpacking libgsf-1-dev (from .../libgsf-1-dev_1.14.3-1ubuntu2_i386.deb) ...
Selecting previously deselected package librsvg2-dev.
Unpacking librsvg2-dev (from .../librsvg2-dev_2.16.0-0ubuntu2_i386.deb) ...
Setting up libbz2-dev (1.0.3-6build1) ...

Setting up libcroco3-dev (0.6.1-1build1) ...
Setting up libgnome-menu-dev (2.18.0-0ubuntu3) ...
Setting up libgsf-1-dev (1.14.3-1ubuntu2) ...

Setting up librsvg2-dev (2.16.0-0ubuntu2) ...

rie-rie@dell:~$ bzr co [http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk](http://bazaar.launchpad.net/~awn-extras/awn-extras/trunk) awn-extras
rie-rie@dell:~$ cd awn-extras/awn-applets/awn-core-applets/                    
bash: cd: awn-extras/awn-applets/awn-core-applets/: No such file or directory
rie-rie@dell:~$ sudo -i
root@dell:~# cd awn-extras/awn-applets/awn-core-applets/
-bash: cd: awn-extras/awn-applets/awn-core-applets/: No such file or directory
root@dell:~# apt-get install awn-extras/awn-applets/awn-core-applets/
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package awn-extras
root@dell:~# sudo apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgnome-vfs-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev libgnomevfs2-0 libgnome-desktop-2 libgnome2-0 libwnck-common python-gtk2 python-gconf bzr gnome-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
automake1.9 is already the newest version.
autotools-dev is already the newest version.
libxdamage-dev is already the newest version.
libxcomposite-dev is already the newest version.
libgnome2-common is already the newest version.
libgnome2-dev is already the newest version.
libgnome-desktop-dev is already the newest version.
libgtk2.0-dev is already the newest version.
libgtk2.0-dev set to manual installed.
libwnck-dev is already the newest version.
libgconf2-dev is already the newest version.
libgconf2-dev set to manual installed.
libglib2.0-dev is already the newest version.
libglib2.0-dev set to manual installed.
libdbus-glib-1-dev is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnome-desktop-2 is already the newest version.
libgnome2-0 is already the newest version.
libwnck-common is already the newest version.
python-gtk2 is already the newest version.
python-gconf is already the newest version.
bzr is already the newest version.
gnome-common is already the newest version.
The following packages were automatically installed and are no longer required:
  libclan2c2a-jpeg libclan2c2a-sound libclanlib2c2a libclan2c2a-vorbis
  libclan2c2a-gui libclan2c2a-png libmikmod2 libssl0.9.7 libclan2c2a-mikmod
  hermes1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gconf indent libdb3 libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-vfs-common libgnome-vfs0 libgtk1.2 libgtk1.2-common liboaf-dev
  liboaf0 liborbit-dev liborbit0 libwrap0-dev libxml1 oaf
Suggested packages:
  nfs-common gnome-vfs-extfs
Recommended packages:
  orbit
The following NEW packages will be installed:
  gconf indent libdb3 libgconf-dev libgconf11 libglib1.2 libglib1.2-dev
  libgnome-vfs-common libgnome-vfs-dev libgnome-vfs0 libgtk1.2
  libgtk1.2-common liboaf-dev liboaf0 liborbit-dev liborbit0 libwrap0-dev
  libxml1 oaf
0 upgraded, 19 newly installed, 0 to remove and 1 not upgraded.
Need to get 3957kB of archives.
After unpacking 14.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main libwrap0-dev 7.6.dbs-11ubuntu0.1 [34.4kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgtk1.2-common 1.2.10-18 [158kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libglib1.2 1.2.10-17build1 [123kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libgtk1.2 1.2.10-18 [837kB]     
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libdb3 3.2.9+dfsg-0.1build1 [243kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe liborbit0 0.5.17-11.1ubuntu3 [188kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe liboaf0 0.6.10-8 [70.6kB]   
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libxml1 1:1.8.17-14build1 [216kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe oaf 0.6.10-8 [122kB]        
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libgconf11 1.0.9-7.2 [102kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe gconf 1.0.9-7.2 [393kB]    
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main indent 2.2.9-7 [102kB]         
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main libglib1.2-dev 1.2.10-17build1 [177kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe liborbit-dev 0.5.17-11.1ubuntu3 [403kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe liboaf-dev 0.6.10-8 [87.7kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libgconf-dev 1.0.9-7.2 [142kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libgnome-vfs-common 1.0.5-5.3 [259kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libgnome-vfs0 1.0.5-5.3 [92.0kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe libgnome-vfs-dev 1.0.5-5.3 [208kB]
Fetched 3957kB in 1m38s (40.3kB/s)                                             
Selecting previously deselected package libgtk1.2-common.
(Reading database ... 154329 files and directories currently installed.)
Unpacking libgtk1.2-common (from .../libgtk1.2-common_1.2.10-18_all.deb) ...
Selecting previously deselected package libglib1.2.
Unpacking libglib1.2 (from .../libglib1.2_1.2.10-17build1_i386.deb) ...
Selecting previously deselected package libgtk1.2.
Unpacking libgtk1.2 (from .../libgtk1.2_1.2.10-18_i386.deb) ...
Selecting previously deselected package libdb3.
Unpacking libdb3 (from .../libdb3_3.2.9+dfsg-0.1build1_i386.deb) ...
Selecting previously deselected package liborbit0.
Unpacking liborbit0 (from .../liborbit0_0.5.17-11.1ubuntu3_i386.deb) ...
Selecting previously deselected package liboaf0.
Unpacking liboaf0 (from .../liboaf0_0.6.10-8_i386.deb) ...
Selecting previously deselected package libxml1.
Unpacking libxml1 (from .../libxml1_1%3a1.8.17-14build1_i386.deb) ...
Selecting previously deselected package oaf.
Unpacking oaf (from .../archives/oaf_0.6.10-8_i386.deb) ...
Selecting previously deselected package libgconf11.
Unpacking libgconf11 (from .../libgconf11_1.0.9-7.2_i386.deb) ...
Selecting previously deselected package gconf.
Unpacking gconf (from .../gconf_1.0.9-7.2_i386.deb) ...
Selecting previously deselected package indent.
Unpacking indent (from .../indent_2.2.9-7_i386.deb) ...
Selecting previously deselected package libglib1.2-dev.
Unpacking libglib1.2-dev (from .../libglib1.2-dev_1.2.10-17build1_i386.deb) ...
Selecting previously deselected package libwrap0-dev.
Unpacking libwrap0-dev (from .../libwrap0-dev_7.6.dbs-11ubuntu0.1_i386.deb) ...
Selecting previously deselected package liborbit-dev.
Unpacking liborbit-dev (from .../liborbit-dev_0.5.17-11.1ubuntu3_i386.deb) ...
Selecting previously deselected package liboaf-dev.
Unpacking liboaf-dev (from .../liboaf-dev_0.6.10-8_i386.deb) ...
Selecting previously deselected package libgconf-dev.
Unpacking libgconf-dev (from .../libgconf-dev_1.0.9-7.2_i386.deb) ...
Selecting previously deselected package libgnome-vfs-common.
Unpacking libgnome-vfs-common (from .../libgnome-vfs-common_1.0.5-5.3_i386.deb) ...
Selecting previously deselected package libgnome-vfs0.
Unpacking libgnome-vfs0 (from .../libgnome-vfs0_1.0.5-5.3_i386.deb) ...
Selecting previously deselected package libgnome-vfs-dev.
Unpacking libgnome-vfs-dev (from .../libgnome-vfs-dev_1.0.5-5.3_i386.deb) ...
Setting up libgtk1.2-common (1.2.10-18) ...

Setting up libglib1.2 (1.2.10-17build1) ...

Setting up libgtk1.2 (1.2.10-18) ...

Setting up libdb3 (3.2.9+dfsg-0.1build1) ...

Setting up liborbit0 (0.5.17-11.1ubuntu3) ...

Setting up liboaf0 (0.6.10-8) ...

Setting up libxml1 (1.8.17-14build1) ...

Setting up oaf (0.6.10-8) ...
Setting up indent (2.2.9-7) ...

Setting up libglib1.2-dev (1.2.10-17build1) ...

Setting up libwrap0-dev (7.6.dbs-11ubuntu0.1) ...
Setting up liborbit-dev (0.5.17-11.1ubuntu3) ...

Setting up liboaf-dev (0.6.10-8) ...
Setting up libgconf11 (1.0.9-7.2) ...

Setting up libgnome-vfs-common (1.0.5-5.3) ...
Setting up libgnome-vfs0 (1.0.5-5.3) ...

Setting up gconf (1.0.9-7.2) ...

Setting up libgconf-dev (1.0.9-7.2) ...
Setting up libgnome-vfs-dev (1.0.5-5.3) ...
root@dell:~# make
make: *** No targets specified and no makefile found.  Stop.
root@dell:~# cd awn-extras/awn-applets/awn-extras-applets
root@dell:~/awn-extras/awn-applets/awn-extras-applets# pkg-config --modversion awn
0.2.1
root@dell:~/awn-extras/awn-applets/awn-extras-applets# ./configure
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
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gconftool-2... /usr/bin/gconftool-2
checking for intltool >= 0.34... 0.35.5 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking for iconv... /usr/bin/iconv
checking for msgfmt... /usr/bin/msgfmt
checking for msgmerge... /usr/bin/msgmerge
checking for xgettext... /usr/bin/xgettext
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for DEPS... configure: error: Package requirements (gtk+-2.0
                  awn
                  libwnck-1.0
                  libglade-2.0
                  libgnome-menu
                  gnome-desktop-2.0
                  librsvg-2.0
                  libgtop-2.0
                  glib-2.0
                  dbus-1
                  dbus-glib-1
                  libsexy
                  gconf-2.0
                  gdk-2.0
                  gdk-pixbuf-2.0
                  libnotify
                  vte) were not met:

No package 'libgtop-2.0' found
No package 'libsexy' found
No package 'libnotify' found
No package 'vte' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

root@dell:~/awn-extras/awn-applets/awn-extras-applets# make
make: *** No targets specified and no makefile found.  Stop.
root@dell:~/awn-extras/awn-applets/awn-extras-applets#

---

### Post by vgrisham on 2008-02-29
I'm having a hard time getting the tsclient applet to do anything. Where I've placed it on the dock, I see a line/separator, but I'm unable to access the tsclient applet.

Any ideas?

SOLVED: I restarted the dock and it popped up.

---

