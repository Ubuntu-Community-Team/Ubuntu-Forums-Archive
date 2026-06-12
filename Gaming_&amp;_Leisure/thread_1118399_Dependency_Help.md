---
title: "Dependency Help"
date: 2009-04-06
forum: Gaming &amp; Leisure
---

### Post by deamon_knight on 2009-04-06
So i was digging through my old games and found Terminus, which has a native linux binary so I thought I'd give it a try on Ubuntu.

After the install I'm getting:

"terminus: error while loading shared libraries: libstdc++.so.2.8: cannot open shared object file: No such file or directory"

Since synaptic shows libstdc++5 installed and 6 available I guess this old game is looking for an Old C++ library. Am I stuck? Or is tere some way to get libstdc++2.8 installed, or get this to work with the current library?

Thanks

---

### Post by wingnux on 2009-04-07
Search the forum for "getlibs", install it and then run "getlibs -32 libstdc++.so.2.8"

(Change 32 to 64, depending on your system's architecture)

---

### Post by deamon_knight on 2009-04-07
Thanks wingnut, but no luck. "getlibs -32 libstdc++.so.2.8" just sits doing nothing, no output at all. pointing getlibs to the binary returns "No match for libstdc++.so.2.8"

Any suggestions?

---

### Post by Vadi on 2009-04-07
No, getlibs wont help you get an older version of it. Best thing you can do is find an .so of it and place it into the same folder, I think that might work.

(rather windows-like, heh)

---

### Post by deamon_knight on 2009-04-08
Well, looking here:

[http://www.linuxfromscratch.org/pipermail/blfs-support/2002-May/021952.html](http://www.linuxfromscratch.org/pipermail/blfs-support/2002-May/021952.html)

it looks like I should download:
[ftp://ftp.gnu.org/gnu/libstdc++/libstdc++-2.8.1.1.tar.gz](ftp://ftp.gnu.org/gnu/libstdc++/libstdc++-2.8.1.1.tar.gz)

 untar it and "make" it. What happens when I do that? Will I have to worry about overwriting current Libraries?

---

### Post by Vadi on 2009-04-08
no copy the resulting .so you get after *make*ing it into the same place where the binary is.

if it doesnt find it, I think there is a little script you can do to help it find.

You dont need to worry about overwring your current stuff or having other programs be affected.

it seems its on sale too: [http://www.tuxgames.com/details.cgi?gameref=41](http://www.tuxgames.com/details.cgi?gameref=41) but a tad pricey

---

### Post by deamon_knight on 2009-04-08
Well, tying to make from that .tar just gave a pile of errors. I'm not sure where to go from here.

---

### Post by Vadi on 2009-04-08
Paste it here. Maybe you're missing some development libraries which need to be installed (best case).

Worse would be that the new libraries are incompatible with the old ones it was coded for back in the day.

---

### Post by deamon_knight on 2009-04-09
Thanks Vadi. Here are the instructions in INSTALL. I it talks about building this alongside gcc, but since I'm not doing that I'm ignoring that section.

"To configure libstdc++:

  % mkdir objdir
  % cd objdir
  % srcdir/configure [target] [options]


target specification

  libstdc++ has code to correctly determine the correct value for
  target for nearly all native systems.  Therefore, we highly
  recommend you not provide a configure target when configuring a
  native package.

  target must be specified when configuring a cross package;
  examples of valid targets would be i960-rtems, m68k-coff, sh-elf, etc.
" 
then
 "Now that libstdc++ is configured, you are ready to build the compiler
(if you unpacked the compiler sources as recommended above) and
runtime libraries.  If you've arranged your compiler and library sources
in the `one tree' proposal, you should call `make bootstrap'; this will
bootstrap the compiler and the runtime libraries in one shot. If you don't
want to build the compiler, simply call `make all'.

We highly recommend that libstdc++ be built using gnu-make; other
versions may work, then again they might not.  To be safe build with gnu-make."

so I'm making a subdirectory of ~/Downloads/libstdc++2.8.1.1 called /liboutput, then cd-ing to /liboutput, then ~/Downloads/libstd++2.8.1.1/configure , then "make all"

and here is the result:

make[1]: Entering directory `/home/jay/Downloads/libstdc++-2.8.1.1/liboutput/libiberty'
if [ x"no" = xyes ] && [ ! -d pic ]; then \
	  mkdir pic; \
	else true; fi
touch stamp-picdir
echo "# !Automatically generated from ../../libiberty/functions.def"\
	  "- DO NOT EDIT!" >needed2.awk
grep '^DEFVAR(' < ../../libiberty/functions.def \
	 | sed -e '/DEFVAR/s|DEFVAR.\([^,]*\).*|/\1/ { printf "#ifndef NEED_\1\\n#define NEED_\1\\n#endif\\n" }|' \
	 >>needed2.awk
grep '^DEFFUNC(' < ../../libiberty/functions.def \
	 | sed -e '/DEFFUNC/s|DEFFUNC.\([^,]*\).*|/\1/ { printf "#ifndef NEED_\1\\n#define NEED_\1\\n#endif\\n" }|' \
	 >>needed2.awk
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/dummy.c 2>/dev/null
(gcc -o dummy -g -O2   dummy.o  ) >errors 2>&1 || true
echo "/* !Automatically generated from ../../libiberty/functions.def"\
	  "- DO NOT EDIT! */" >lconfig.h
awk -f needed2.awk <errors >>lconfig.h
cp lconfig.h config.tmp
/bin/sh ../../libiberty/../move-if-change config.tmp config.h
touch stamp-config
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/argv.c -o pic/argv.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/argv.c
../../libiberty/argv.c: In function ‘dupargv’:
../../libiberty/argv.c:122: warning: incompatible implicit declaration of built-in function ‘strcpy’
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/basename.c -o pic/basename.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/basename.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/choose-temp.c -o pic/choose-temp.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/choose-temp.c
../../libiberty/choose-temp.c: In function ‘choose_temp_base’:
../../libiberty/choose-temp.c:127: warning: incompatible implicit declaration of built-in function ‘strlen’
../../libiberty/choose-temp.c:130: warning: incompatible implicit declaration of built-in function ‘strcpy’
../../libiberty/choose-temp.c:145: warning: incompatible implicit declaration of built-in function ‘abort’
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/concat.c -o pic/concat.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/concat.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/cplus-dem.c -o pic/cplus-dem.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/cplus-dem.c
../../libiberty/cplus-dem.c: In function ‘mop_up’:
../../libiberty/cplus-dem.c:622: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/cplus-dem.c:630: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/cplus-dem.c: In function ‘demangle_template’:
../../libiberty/cplus-dem.c:1075: warning: incompatible implicit declaration of built-in function ‘abort’
../../libiberty/cplus-dem.c:1231: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/cplus-dem.c:1235: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/cplus-dem.c: In function ‘gnu_special’:
../../libiberty/cplus-dem.c:1766: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/cplus-dem.c: In function ‘forget_types’:
../../libiberty/cplus-dem.c:2599: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/cplus-dem.c: In function ‘string_delete’:
../../libiberty/cplus-dem.c:2959: warning: incompatible implicit declaration of built-in function ‘free’
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/fdmatch.c -o pic/fdmatch.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/fdmatch.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/fnmatch.c -o pic/fnmatch.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/fnmatch.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/getopt.c -o pic/getopt.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/getopt.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/getopt1.c -o pic/getopt1.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/getopt1.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/getruntime.c -o pic/getruntime.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/getruntime.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/hex.c -o pic/hex.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/hex.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/floatformat.c -o pic/floatformat.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/floatformat.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/objalloc.c -o pic/objalloc.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/objalloc.c
../../libiberty/objalloc.c: In function ‘objalloc_create’:
../../libiberty/objalloc.c:91: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/objalloc.c: In function ‘objalloc_free’:
../../libiberty/objalloc.c:176: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/objalloc.c:180: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/objalloc.c: In function ‘objalloc_free_block’:
../../libiberty/objalloc.c:214: warning: incompatible implicit declaration of built-in function ‘abort’
../../libiberty/objalloc.c:239: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/objalloc.c:242: warning: incompatible implicit declaration of built-in function ‘free’
../../libiberty/objalloc.c:277: warning: incompatible implicit declaration of built-in function ‘free’
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/obstack.c -o pic/obstack.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/obstack.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/pexecute.c -o pic/pexecute.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/pexecute.c
../../libiberty/pexecute.c: In function ‘pexecute’:
../../libiberty/pexecute.c:596: warning: incompatible implicit declaration of built-in function ‘exit’
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/spaces.c -o pic/spaces.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/spaces.c
test x"no" != xyes || \
	  gcc -c -g -O2 -I. -I../../libiberty/../include  -fpic ../../libiberty/strerror.c -o pic/strerror.o
gcc -c -g -O2 -I. -I../../libiberty/../include  ../../libiberty/strerror.c
../../libiberty/strerror.c:460: error: static declaration of ‘sys_nerr’ follows non-static declaration
/usr/include/bits/sys_errlist.h:27: error: previous declaration of ‘sys_nerr’ was here
../../libiberty/strerror.c:461: error: conflicting types for ‘sys_errlist’
/usr/include/bits/sys_errlist.h:28: error: previous declaration of ‘sys_errlist’ was here
make[1]: *** [strerror.o] Error 1
make[1]: Leaving directory `/home/jay/Downloads/libstdc++-2.8.1.1/liboutput/libiberty'
make: *** [all-libiberty] Error 2

Thanks

---

### Post by Grishka on 2009-04-10
man, 2.8 is awfully old. you'll have a terrible time compiling it today. basically, you'd have to create a separate build environment.
the easiest thing you can try to play this, is finding some very old linux distro, installing it in virtualbox, and running your game in a virtual system.
if you'd rather not, you can try compiling stdc++ with an old version of gcc. for example, grab gcc-3.4, configure stdc++ with "CC="gcc-3.4" ./configure", and make.
you can also try a workaround. try creating a symlink to your current libstdc++.so in your /usr/lib, and change it's name to libstdc++.so.2.8. this will fool the game into trying to use your current libs. be sure not to touch your current libraries, though. just the symlink you made. stdc++ is a vital system library, so you'll probably break your system if you overwrite it by mistake or something. anyway, if that won't either, try downloading stdc++ 2.10 from here: [http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download](http://packages.ubuntu.com/dapper/i386/libstdc++2.10-glibc2.2/download). unpack the deb and rename the .so file to libstdc++.so.2.8. then put it in /usr/lib. maybe the game will run.

---

### Post by deamon_knight on 2009-04-10
Well, its as much an exercise in seeing if it can work as much as wanting to play the game. I wonder if running the windows version in wine would work.

Lets try the simplest solution, create a file in the game directory called libstdc++.so.2.8. I would go to the game directory and do:

"ln -sT /usr/lib/libstdc++.so.5 libstdc++.so.2.8"

Correct?

---

### Post by Grishka on 2009-04-10
> **deamon_knight said:**
> Well, its as much an exercise in seeing if it can work as much as wanting to play the game. I wonder if running the windows version in wine would work.

Lets try the simplest solution, create a file in the game directory called libstdc++.so.2.8. I would go to the game directory and do:

"ln -sT /usr/lib/libstdc++.so.5 libstdc++.so.2.8"

Correct?

it'll work if the game looks in it's own directory for library files. which is rare. I was thinking rather of making the symlink in /usr/lib, to make it systemwide. "sudo ln -sT /usr/lib/libstdc++.so.5 /usr/lib/libstdc++.so.2.8" will do it in your case.

---

### Post by deamon_knight on 2009-04-14
Tried but didn't work. Now running program reports this error:

"terminus: symbol lookup error: terminus: undefined symbol: cerr"

I did find this:

[http://rpmseek.com/rpm-dl/compat-libstdc%5C%5C-7.3-2.96.118.i386.html?hl=com&cx=0:-:0:557789:0:0:0](http://rpmseek.com/rpm-dl/compat-libstdc%5C%5C-7.3-2.96.118.i386.html?hl=com&cx=0:-:0:557789:0:0:0)

and suggestions that I "alien" it to a .deb and install it that way. Any risks to that approach?

---

### Post by deamon_knight on 2009-04-18
Well, I rolled the dice with the .rpm&ailen and it worked! Game runs, looks good but for one problem, it crashes with 

"terminus: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.
Aborted
" 
When every you have to enter text into a prompt in game. Otherwise the game plays normally, but you can't enter a name for a saved game or such.

---

### Post by deamon_knight on 2009-04-19
Also tried the Windows binary with Wine, but no luck. Looks like an X problem, maybe, but I can't find anyone who has it working.

---

### Post by Grishka on 2009-04-19
> **deamon_knight said:**
> Also tried the Windows binary with Wine, but no luck. Looks like an X problem, maybe, but I can't find anyone who has it working.

try checking up the system requirements for terminus. maybe you can dig up some old linux distro that it supports, and install your game with virtualbox.

---

