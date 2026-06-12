---
title: "HOW-TO: Compile Avant Window Navigator"
date: 2007-02-01
forum: Desktop Effects &amp; Customization
---

### Post by FunnyLookinHat on 2007-02-01
[B][U]******************************************************************************
******************************************************************************
ATTENTION!!  This post is no longer being updated, please see the following post instead:
[http://ubuntuforums.org/showthread.php?p=2307772](http://ubuntuforums.org/showthread.php?p=2307772)
******************************************************************************
******************************************************************************[/U][/B]

Many of you saw the digg post recently for avant window navigator and wanted to know how to compile it and get it working on ubuntu.  It's actually quite useful and very neat eye-candy.  : )

NOTE:  You will need to be running either XGL or AIGLX along with a composite window manager (usually beryl or compiz).  I am running AIGLX and beryl, in case you were wondering.

UPDATE: Someone has posted a .deb file to make it easier for you all to install, see the bottom of my post.

Here's how I got it to compile on my edgy-eft installation.  (These should work for dapper-drake as well)
[B]
UPDATE 2: I saw that several people posted that the svn checkout works much better, this is so true!  So I've added two sections, Option 1 for stable code, and Option 2 for svn (read: better) code.[/B]
**_I strongly recommend using the SVN code, and it's still easy to do for all of you who may be new to linux!  Just follow the Option 2 instructions_**

**UPDATE 3:  The latest code release (at least as far as SVN goes) requires a few extra packages to be installed: libgnome2-dev libgnome-desktop-2 libgnome-desktop-dev**

**_Option 1_**:
Download the latest code release from the official product page:
[http://code.google.com/p/avant-window-navigator/downloads/list]("http://code.google.com/p/avant-window-navigator/downloads/list")
The file that I used was:
[http://avant-window-navigator.googlecode.com/files/avant-window-navigator-0.1.1-2.tar.gz]("http://avant-window-navigator.googlecode.com/files/avant-window-navigator-0.1.1-2.tar.gz")

You should save this file to your home directory for easy access in your console.  If not, locate the file and put it there.

Open a terminal and type the following:
> tar -zxvf avant-window-navigator-0.1.1-2.tar.gz
This might be different if you used a different version of the code.  Just type up to the avant part and hit tab and the rest of the file name should be completed.

After you have extracted (or checked out) all of the files, change to the new directory that you have created:
> cd avant-window-navigator-0.1.1/
Again, this will be easiest if you just type cd avant-window and then hit tab.

Now we have to install the essential build dependencies and programs.
> sudo apt-get install build-essential

Next we have to install a few dependent packages for the compiler that are not installed by default:
> sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev libgnome2-dev libgnome-desktop-2 libgnome-desktop-dev

Now we go through the basic compile steps...

First we configure:
> ./configure

Now we compile (make):
> make

Then we have to make install, which we have to run as root to properly complete:
> sudo make install

**_Option 2:_**
Compile from SVN:
First we need to install subversion:
> sudo apt-get install subversion
We'll also need a few additional libraries (Note: You also need gnome-common which was not required for the .tar.gz code source)
> sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev gnome-common libgnome2-dev libgnome-desktop-2 libgnome-desktop-dev
Now we check out the code:
> svn checkout [http://avant-window-navigator.googlecode.com/svn/trunk/](http://avant-window-navigator.googlecode.com/svn/trunk/) avant-window-navigator
Change into the directory the code is in:
> cd avant-window-navigator
Use his auto-gen script (instead of ./configure):
> ./autogen.sh
Compile:
> make
And install binaries:
> sudo make install


**_IMPORTANT!_**
There is one last step which many people will miss!  In order to avoid a seg-fault do the following:
> cd data
gconftool-2 --install-schema-file=avant-window-navigator.schemas

Now you can type the following command to start it:
> avant-window-navigator
You can also add this line to your startup script list under System - Preferences - Sessions

Also, on my system I found a link to start it on my menu: Applications - Accessories - Avant Window Manager

To change any preferences with the program you will have to do the following in a console:
> avant-preferences

Let me know if you guys have any problems!  I'll be watching this thread for the next week or so and try to give you all help!  Please post comments as well, my first tutorial.   :D 

Cheers,
FunnyLookinHat

***EDIT***
I listed this on digg, please digg it for the other ubuntu users who will want to use this!
[http://www.digg.com/linux_unix/Ubuntu_Tutorial_for_Avant_Window_Manager_Eye_Candy](http://www.digg.com/linux_unix/Ubuntu_Tutorial_for_Avant_Window_Manager_Eye_Candy)


******EDIT 2*********
Bugz (I think that's his name) posted a link to a .deb for all of you who would rather not compile:
[http://ubuntuforums.org/attachment.php?attachmentid=24376&d=1170430951](http://ubuntuforums.org/attachment.php?attachmentid=24376&d=1170430951)

---

### Post by patrickjst on 2007-02-01
Nice post. I tried this myself before reading and was one those dopes who got the segfault. :) Working now though. Thanks!

---

### Post by xxzeenoxx on 2007-02-01
i got past the step which installs the dependent packages, but where or how do i compile it. i was putting in ./configure but it was saying no such file or directory.  sorry, i'm VERY new to linux.  i was just copying and pasting the commands.


NEVEVRMIND...im dumb, i wasnt even in the directory.  Sorry guys, i'm slowly learning.  I'm just kicking myself in the a** for not trying linux sooner....I LOVE IT!

---

### Post by FunnyLookinHat on 2007-02-01
Sorry zeeno, I left out a step!

After you unpack the file (The line that starts with tar -zxvf) you will have to change into the directory that all the files went into.

cd avant-window-navigator-0.1.1/

---

### Post by Grog140 on 2007-02-01
I got it compiled alright, but all the icons in it seem buggy. I am not sure if it is just a bug because it is an early release or what.

But as far as I can tell, the active icon glow seems to be on top of the icon, making the acon disappear and leaving just a blank looking space.

---

### Post by pinkpanther_bc on 2007-02-01
This looks great, but cant get it to work!

frank@frank-laptop:~$ avant-window-navigator
Floating point exception (core dumped)

Avant-preferences -- the folder contents could not be displayed
error accessing 'file:///usr/local/share/avant-window-navigator/active': File not found

---

### Post by glabouni on 2007-02-01
for those sith segmentation fault or other difficulties, you'll find workarounds at: [http://code.google.com/p/avant-window-navigator/issues/detail?id=5&can=2&q=](http://code.google.com/p/avant-window-navigator/issues/detail?id=5&can=2&q=)

be sure to report any bugs you may encounter.

---

### Post by GForce0617 on 2007-02-01
:D  WOW!!

Great application. Great write up Funny!

Only a few suggestion (if anyone can answer them as well),,,

Any way that it could move to any side of the desktop (top, bottom, left, right)?

Good job and keep up the great work.

---

### Post by wormeyman on 2007-02-02
```
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'libwnck-1.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

eric@ubuntu:~/avant-window-navigator-0.1.1$ sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
libwnck-common is already the newest version.
libglib2.0-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck-dev: Depends: libwnck18 (= 2.16.1-0ubuntu1) but 2.16.1-0ubuntu1.1 is to be installed
E: Broken packages
eric@ubuntu:~/avant-window-navigator-0.1.1$ 


```

doh!

---

### Post by KiwiWifi on 2007-02-02
After following this great guide, I get this error every time I execute "avant-windows-navigator

```

(avant-window-navigator:19953): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

(avant-window-navigator:19953): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

```

Whats this?

Please advice, and keep in mind I'm a complete newbie

---

### Post by jbus on 2007-02-02
SVN works much better.
[http://code.google.com/p/avant-window-navigator/source](http://code.google.com/p/avant-window-navigator/source)

---

### Post by jbus on 2007-02-02
> **KiwiWifi said:**
> After following this great guide, I get this error every time I execute "avant-windows-navigator

```

(avant-window-navigator:19953): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

(avant-window-navigator:19953): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

```

Whats this?

Please advice, and keep in mind I'm a complete newbie

What version of Cairo are you using?

---

### Post by Stemp on 2007-02-02
> What version of Cairo are you using?

I have the same errors with libcairo2 1.2.4-1ubuntu2

---

### Post by plamoni on 2007-02-02
I'm getting the same errors...

It still launches, but is really slow and jerky and the icons are a bit funny looking. I am assuming it is not being accelerated properly and is using software acceleration for some reason...

Same version of libcairo as Stemp

---

### Post by jbus on 2007-02-02
I'm using cairo 1.2.6-1 and it compiled and runs fine. That might be your problem. I had previously compiled cairo myself though. If you have to compile cairo, be sure to use checkinstall to make a deb so you can uninstall it easily if you want to.

---

### Post by tdeverell on 2007-02-02
> **jbus said:**
> I'm using cairo 1.2.6-1 and it compiled and runs fine. That might be your problem. I had previously compiled cairo myself though. If you have to compile cairo, be sure to use checkinstall to make a deb so you can uninstall it easily if you want to.


I've got this same issue, how to I go about getting cairo 1.2.6-1?  Is there an apt-get command?  Synaptic Package?  Sorry, I'm a little green here...

I'm only finding RPMs...  I need a deb.

---

### Post by BugS on 2007-02-02
Im not really impressed. Cant even move the damn thing from the bottom of the screen.

However, here is a package for edgy that the lazy might find useful.

---

### Post by IndigoMontoya on 2007-02-02
I have everything running pretty well (i had to get the correct version of one of the software packages installed using "sudo apt-get install libwnck18=2.16.1-0ubuntu1" - sorry I forget which it was).  The onyl problem I have is my active icon is always blocked by some square.  This is kinda annoying.  I have played with a bunch of settings in the avant-preferences and cant get it to go away.  Any suggestions?

---

### Post by dxxvi on 2007-02-02
Is there any beautiful dock which doesn't require beryl or compiz (is it because it needs a composite window manager and beryl & compiz are the only one which provide that?).

I ask so because my beryl  (0.1.99) doesn't work with IntelliJ IDEA 6.0.4 (the IDEA window is blank) which I work with most of the time :(. But beryl works with Eclipse 3.2.1.

---

### Post by Platinum J on 2007-02-02
Hello all, 

I am having the same problem as shows below. Whats up with that?!? Any help is appreciated. 

Thanks, 

The Platinum One


> **wormeyman said:**
> ```
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'libwnck-1.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

eric@ubuntu:~/avant-window-navigator-0.1.1$ sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-dev is already the newest version.
libwnck-common is already the newest version.
libglib2.0-dev is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck-dev: Depends: libwnck18 (= 2.16.1-0ubuntu1) but 2.16.1-0ubuntu1.1 is to be installed
E: Broken packages
eric@ubuntu:~/avant-window-navigator-0.1.1$ 


```

doh!

---

### Post by Scotty562 on 2007-02-02
> **Platinum J said:**
> Hello all, 

I am having the same problem as shows below. Whats up with that?!? Any help is appreciated. 

Thanks, 

The Platinum One

I have the same error :(.

---

### Post by IndigoMontoya on 2007-02-02
to fix this problem run ```
sudo apt-get install libwnck-dev=2.16.1-0ubuntu1
```

---

### Post by chaoscomic on 2007-02-02
I get to make and I get this



chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.

what did I do wrong , I have no linux experience or computer code experience for that matter

---

### Post by IndigoMontoya on 2007-02-02
> **chaoscomic said:**
> I get to make and I get this



chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.

what did I do wrong , I have no linux experience or computer code experience for that matter

sounds to me you had errors in the ./configure process.  Likely unmet dependencies.  Can you paste the output of that please.

---

### Post by Scotty562 on 2007-02-02
> **IndigoMontoya said:**
> to fix this problem run ```
sudo apt-get install libwnck-dev=2.16.1-0ubuntu1
```

That didn't work for me, is there anything else to try?

---

### Post by tyce on 2007-02-02
Me either...

$ sudo apt-get install libwnck-dev=2.16.1-0ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libwnck-dev: Depends: libwnck18 (= 2.16.1-0ubuntu1) but 2.16.1-0ubuntu1.1 is to be installed
E: Broken packages

---

### Post by hanzomon4 on 2007-02-02
I got the libwnck-dev error too```
 Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libwnck-dev: Depends: libwnck18 (= 2.16.1-0ubuntu1) but 2.16.1-0ubuntu1.1 is to be installed
E: Broken packages

```

All of you folks with this error do you run beryl? If so what repo are you getting it from, I'm using  Treviño's Beryl-SVN Ubuntu Repository

---

### Post by IndigoMontoya on 2007-02-02
I'm sorry.  I must be mistaken.  Try:```
sudo apt-get install libwnck=2.16.1-0ubuntu1
```

---

### Post by rattking on 2007-02-02
Hi
I run kubuntu and was getting this error in avant-preferences after compiling svn from today

Traceback (most recent call last):
  File "/usr/bin/avant-preferences", line 35, in ?
    import gconf
ImportError: No module named gconf

installing python-gconf solved this
hope it helps someone else

---

### Post by radar_dx on 2007-02-02
> **IndigoMontoya said:**
> I'm sorry.  I must be mistaken.  Try:```
sudo apt-get install libwnck=2.16.1-0ubuntu1
```

Tried this, got the following (using the Beryl-SVN repo...):


radar@dx:~$ sudo apt-get install libwnck=2.16.1-0ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libwnck

Other thoughts? 

(Thanks for the help...)

---

### Post by IndigoMontoya on 2007-02-02
Ok, how about trying with "libwnck18".


I guess I may be more hurt then help today....

---

### Post by radar_dx on 2007-02-02
> **IndigoMontoya said:**
> Ok, how about trying with "libwnck18".


I guess I may be more hurt then help today....


Well, that looks like it's something...: 


```
radar@dx:~$ sudo apt-get install libwnck18=2.16.1-0ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ogle libimlib2 libungif4g
Use 'apt-get autoremove' to remove them.
The following packages will be DOWNGRADED:
  libwnck18
0 upgraded, 0 newly installed, 1 downgraded, 0 to remove and 0 not upgraded.
Need to get 121kB of archives.
After unpacking 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
```

Wasn't sure if i actually *should* downgrade, so i figured i'd see if that's necessary...

---

### Post by TheBlueCow on 2007-02-02
```
sudo apt-get install libwnck18=2.16.1-0ubuntu1
```

Yup, the 18 did the trick =D Thanks Indigo!

---

### Post by radar_dx on 2007-02-02
OK...the libwnk18 downgrade did work (figured i'd give it a try since it worked for TheBlueCow); i've been able to install everything correctly; only thing is, it runs real slow, the active icon disappears, and i get the Cairo errors referred to earlier in this thread...i get the feeling that i need to upgrade cairo or something, but (if it isn't painfully obvious at this point) i'm still pretty new to linux...how do i check the version/go about upgrading/compiling? 

Thanks.

---

### Post by trstn on 2007-02-02
wicked tutorial however try this: [http://blog.paulbetts.org/index.php/2007/02/01/avant-window-navigator-for-ubuntu-edgy/#comment-529](http://blog.paulbetts.org/index.php/2007/02/01/avant-window-navigator-for-ubuntu-edgy/#comment-529)

---

### Post by eightysix on 2007-02-02
Anyone running a Xinerama configuration that got AWN working properly? For me, it displays across all 3 of my screens when I only want it on my main screen. Any help?

---

### Post by chaoscomic on 2007-02-02
ok so I re did these parts to make sure I did them right and here is what I got 

I try to make and get the response at the bottom of all of this

chaos@chaos-laptop:~$ cd avant-window-navigator-0.1.1/
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$  sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev
Reading package lists... Done
Building dependency tree... Done
libgtk2.0-dev is already the newest version.
libwnck-dev is already the newest version.
libwnck-common is already the newest version.
libgconf2-dev is already the newest version.
libglib2.0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for intltool >= 0.34... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$

---

### Post by chaoscomic on 2007-02-02
> **IndigoMontoya said:**
> sounds to me you had errors in the ./configure process.  Likely unmet dependencies.  Can you paste the output of that please.

here is what happenes if you need more let me know , I appreciate the help

chaos@chaos-laptop:~$ cd avant-window-navigator-0.1.1/
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ sudo apt-get install build-essential
Password:
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$  sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev
Reading package lists... Done
Building dependency tree... Done
libgtk2.0-dev is already the newest version.
libwnck-dev is already the newest version.
libwnck-common is already the newest version.
libgconf2-dev is already the newest version.
libglib2.0-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for intltool >= 0.34... 0.35.0 found
checking for perl... /usr/bin/perl
checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ make
make: *** No targets specified and no makefile found.  Stop.
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$

---

### Post by IndigoMontoya on 2007-02-02
Sounds to me like you need the XML parser for Perl.  Try this:

```
sudo apt-get install libxml-parser-perl

```

---

### Post by NobodySpecial on 2007-02-02
Thanks for the great How-to!  I love this little program.  Between this and Kiba-dock / Gnome-dock, we may in the future break out of the old static-icon way of running things.

However, if you now have the latest Beryl which gives you a preview of the window by simply hovering the mouse over the window list, you will be disappointed to see that Avant Window Manager does not offer this functionality.

This is not at all meant to be critical of Avant - its a great program, and I hope someday it can be integrated into the whole Beryl experience.

---

### Post by mhourahine on 2007-02-02
Great article!  Thanks for the post.  I'm looking forward to getting AWN up and running.

I'm looking for some help on an error though should anyone be kind enough to help:

Installing from subversion and running the './autogen.sh' step it fails with the following:

```

checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto) were not met:

No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

If I try to apt-get install the so-called missing packages, apt-get cannot find them.

I'm running Edgy Eft with beryl / aiglx.

Any suggestions?

---

### Post by chaoscomic on 2007-02-02
here is what I get with make

chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ make
make  all-recursive
make[1]: Entering directory `/home/chaos/avant-window-navigator-0.1.1'
Making all in src
make[2]: Entering directory `/home/chaos/avant-window-navigator-0.1.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/libwnck-1.0 -I/usr/include/gconf/2 -I/usr/include/orbit-2.0    -DDATADIR=\""/usr/local/share"\" -DGNOMELOCALEDIR=\""/usr/local/share/locale"\"   -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2 -MT awn-bar.o -MD -MP -MF ".deps/awn-bar.Tpo" -c -o awn-bar.o awn-bar.c; \
        then mv -f ".deps/awn-bar.Tpo" ".deps/awn-bar.Po"; else rm -f ".deps/awn-bar.Tpo"; exit 1; fi
awn-bar.c:35: warning: type defaults to ‘int’ in declaration of ‘current_width’
awn-bar.c: In function ‘awn_bar_new’:
awn-bar.c:79: warning: passing argument 1 of ‘_position_window’ from incompatible pointer type
awn-bar.c: In function ‘_on_expose’:
awn-bar.c:259: warning: type defaults to ‘int’ in declaration of ‘oWidth’
awn-bar.c:260: warning: type defaults to ‘int’ in declaration of ‘oHeight’
awn-bar.c:260: warning: unused variable ‘oHeight’
awn-bar.c:259: warning: unused variable ‘oWidth’
awn-bar.c: In function ‘do_shape_combine_mask’:
awn-bar.c:310: error: ‘Pixmap’ undeclared (first use in this function)
awn-bar.c:310: error: (Each undeclared identifier is reported only once
awn-bar.c:310: error: for each function it appears in.)
awn-bar.c:310: error: syntax error before ‘pixmap’
awn-bar.c:315: warning: implicit declaration of function ‘XShapeQueryExtension’
awn-bar.c:315: warning: implicit declaration of function ‘GDK_WINDOW_XDISPLAY’
awn-bar.c:318: warning: implicit declaration of function ‘XShapeQueryVersion’
awn-bar.c:326: error: ‘pixmap’ undeclared (first use in this function)
awn-bar.c:326: warning: implicit declaration of function ‘GDK_DRAWABLE_XID’
awn-bar.c:331: error: ‘None’ undeclared (first use in this function)
awn-bar.c:334: warning: implicit declaration of function ‘XShapeCombineMask’
awn-bar.c:336: error: ‘ShapeInput’ undeclared (first use in this function)
awn-bar.c:340: error: ‘ShapeSet’ undeclared (first use in this function)
awn-bar.c: In function ‘awn_bar_resize’:
awn-bar.c:467: warning: ISO C forbids conversion of function pointer to object pointer type
awn-bar.c:467: warning: passing argument 2 of ‘g_timeout_add’ from incompatible pointer type
make[2]: *** [awn-bar.o] Error 1
make[2]: Leaving directory `/home/chaos/avant-window-navigator-0.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chaos/avant-window-navigator-0.1.1'
make: *** [all] Error 2
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$

*****here is what I get with sudo make install***** 

chaos@chaos-laptop:~/avant-window-navigator-0.1.1$ sudo make install
Making install in src
make[1]: Entering directory `/home/chaos/avant-window-navigator-0.1.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/libwnck-1.0 -I/usr/include/gconf/2 -I/usr/include/orbit-2.0    -DDATADIR=\""/usr/local/share"\" -DGNOMELOCALEDIR=\""/usr/local/share/locale"\"   -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2 -MT awn-bar.o -MD -MP -MF ".deps/awn-bar.Tpo" -c -o awn-bar.o awn-bar.c; \
        then mv -f ".deps/awn-bar.Tpo" ".deps/awn-bar.Po"; else rm -f ".deps/awn-bar.Tpo"; exit 1; fi
awn-bar.c:35: warning: type defaults to ‘int’ in declaration of ‘current_width’
awn-bar.c: In function ‘awn_bar_new’:
awn-bar.c:79: warning: passing argument 1 of ‘_position_window’ from incompatible pointer type
awn-bar.c: In function ‘_on_expose’:
awn-bar.c:259: warning: type defaults to ‘int’ in declaration of ‘oWidth’
awn-bar.c:260: warning: type defaults to ‘int’ in declaration of ‘oHeight’
awn-bar.c:260: warning: unused variable ‘oHeight’
awn-bar.c:259: warning: unused variable ‘oWidth’
awn-bar.c: In function ‘do_shape_combine_mask’:
awn-bar.c:310: error: ‘Pixmap’ undeclared (first use in this function)
awn-bar.c:310: error: (Each undeclared identifier is reported only once
awn-bar.c:310: error: for each function it appears in.)
awn-bar.c:310: error: syntax error before ‘pixmap’
awn-bar.c:315: warning: implicit declaration of function ‘XShapeQueryExtension’
awn-bar.c:315: warning: implicit declaration of function ‘GDK_WINDOW_XDISPLAY’
awn-bar.c:318: warning: implicit declaration of function ‘XShapeQueryVersion’
awn-bar.c:326: error: ‘pixmap’ undeclared (first use in this function)
awn-bar.c:326: warning: implicit declaration of function ‘GDK_DRAWABLE_XID’
awn-bar.c:331: error: ‘None’ undeclared (first use in this function)
awn-bar.c:334: warning: implicit declaration of function ‘XShapeCombineMask’
awn-bar.c:336: error: ‘ShapeInput’ undeclared (first use in this function)
awn-bar.c:340: error: ‘ShapeSet’ undeclared (first use in this function)
awn-bar.c: In function ‘awn_bar_resize’:
awn-bar.c:467: warning: ISO C forbids conversion of function pointer to object pointer type
awn-bar.c:467: warning: passing argument 2 of ‘g_timeout_add’ from incompatible pointer type
make[1]: *** [awn-bar.o] Error 1
make[1]: Leaving directory `/home/chaos/avant-window-navigator-0.1.1/src'
make: *** [install-recursive] Error 1
chaos@chaos-laptop:~/avant-window-navigator-0.1.1$

---

### Post by Hobbes on 2007-02-03
I get same as mhourahine; missing gnome-desktop-2.0 libgnome-2.0 and gnome-vfs-2.0, tried a couple guesses on the vfs to try to get it working but still no go.

Ahh the joys of compiling/running the newest docks.... its been a while.... :)

---

### Post by alecto on 2007-02-03
> **Hobbes said:**
> I get same as mhourahine; missing gnome-desktop-2.0 libgnome-2.0 and gnome-vfs-2.0, tried a couple guesses on the vfs to try to get it working but still no go.

Ahh the joys of compiling/running the newest docks.... its been a while.... :)

Same error here... Any ideas? :(

---

### Post by molgar on 2007-02-03
It's already on Treviño's repository for Edgy: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)

---

### Post by gansinho on 2007-02-03
here I installed it just fine, but still having some problems:
a) can't add launchers
b) the window I'm currently using doesn't show in the dock (just the ohers)

the output after switching some windows is this
```
gansinho@R2-D2:~$ avant-window-navigator

(process:21392): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
/home/gansinho/.themes/MurrinaNeoGraphite/gtk-2.0/gtkrc:55: Murrine configuration option "squaredstyle" is not supported and will be ignored.

(avant-window-navigator:21392): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed


You have chosen to use the old window manger code, start avant-window-navigator with '-x' to experience the new features

**AWN-X** : Getting icon from X failed for avant-window-navigator
**AWN-X** : Getting icon from X failed for avant-window-navigator
**AWN-X** : Getting icon from X failed for avant-window-navigator
**AWN-X** : Getting icon from X failed for untitled window

(avant-window-navigator:21392): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest != NULL' failed

(avant-window-navigator:21392): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(avant-window-navigator:21392): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest != NULL' failed

(avant-window-navigator:21392): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

```
thanks!

---

### Post by gansinho on 2007-02-03
> **Hobbes said:**
> I get same as mhourahine; missing gnome-desktop-2.0 libgnome-2.0 and gnome-vfs-2.0, tried a couple guesses on the vfs to try to get it working but still no go.

Ahh the joys of compiling/running the newest docks.... its been a while.... :)

just install the dev packages of them! here I did and autogen worked well

---

### Post by fantan on 2007-02-03
Hi for all,

My system is Dapper Drake 6.06 LTS

After setting preferences I tried to start the avant-window-navigator, but all the time I get the following error message:

"root@ubuntu:/usr/local/bin# ./avant-window-navigator
(process:26513): GLib-GObject-CRITICAL **: gtype.c:2215: initialization assertion failed, use IA__g_type_init() prior to this function
(process:26513): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
(process:26513): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
root@ubuntu:/usr/local/bin# "
I tried start as an ordinary user too, but I got the same error message! 
Of course I'm under beryl.
I tried all suggestions from all of you, but no success at all!

Can anybody suggest what to do yet?

Thanks a lot,

fantan

---

### Post by tdatu on 2007-02-03
I got this message error:

Checking for required M4 macros...
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?

---

### Post by Mithrandir.oo00 on 2007-02-04
I'm encountering the following error after following method 2:
```
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto) were not met:

No package 'gnome-desktop-2.0' found
No package 'libgnome-2.0' found
No package 'gnome-vfs-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

rob@arthur:~/avant-window-navigator$ make
make: *** No targets specified and no makefile found.  Stop.
rob@arthur:~/avant-window-navigator$ ls
aclocal.m4         ChangeLog     configure     INSTALL              libtool      mkinstalldirs         src
AUTHORS            config.guess  configure.in  install-sh           ltmain.sh    NEWS
autogen.sh         config.h.in   COPYING       intltool-extract.in  Makefile.am  po
autom4te.cache     config.log    data          intltool-merge.in    Makefile.in  prepare-ChangeLog.pl
avant-preferences  config.sub    depcomp       intltool-update.in   missing      README
```

I tried 
```
sudo apt-get install build-essential
```
which added a bunch of files, but didn't help. Then I tried
```
sudo gedit /etc/apt/sources.list
```
and uncommented all the extra repositories, which also didn't help.

I'm running a fairly clean install of ubuntu edgy, with Beryl running nicely.

---

### Post by searayman on 2007-02-04
there is an update in the svn version how do i update it on my computer to get the latest version? I am a newbie?

---

### Post by searayman on 2007-02-04
this is how i tried updatign but it didnt work:  

[http://code.google.com/p/avant-window-navigator/issues/detail?id=25&can=2&q=](http://code.google.com/p/avant-window-navigator/issues/detail?id=25&can=2&q=)

---

### Post by DjBeck on 2007-02-04
Cool dock, but really annoying that the active windows icon is replaced by a transparent box .. anyone know of a fix ?

---

### Post by iGama on 2007-02-05
Portuguese Translation : 

[Avant Window Navigator no Ubuntu  @ GuiaUbuntuPT.org](http://www.guiaubuntupt.org/wiki/index.php?title=Avant_Window_Navigator_no_Ubuntu) 

:D

---

### Post by edwyn on 2007-02-05
I installed the deb file but i can;t run the program after installed.

this is the error message i get

~$ avant-window-navigator

(process:11484): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
Segmentation fault (core dumped)

and...

~$ avant-preferences
/usr/share/avant-window-navigator/window.glade
Traceback (most recent call last):
  File "/usr/bin/avant-preferences", line 250, in ?
    app = main()
  File "/usr/bin/avant-preferences", line 143, in __init__
    self.setup_chooser(APP_ACTIVE_PNG, self.wTree.get_widget("activefilechooser"))
  File "/usr/bin/avant-preferences", line 221, in setup_chooser
    chooser.set_filename(self.client.get_string(key))
TypeError: GtkFileChooser.set_filename() argument 1 must be string, not None


anyone can help me with this ?

---

### Post by Scotty562 on 2007-02-06
Did anyone find a way to get the Beryl preview window to work with this wonderful gem?

---

### Post by pormogo on 2007-02-06
How would one go about changing the icons in this doc? The doc itself is nice however when launching some applications (such as firefox or VLC) the icon appears pixelated and blury, Poor old xterm doesn't even have an icon :( how would I go about changing the icons that appear in the doc?

---

### Post by stiankarlsen on 2007-02-06
When using autogen.sh, I get:

> 
..
..
..
Checking for required M4 macros...
  libtool.m4 not found
  glib-gettext.m4 not found
  intltool.m4 not found
  pkg.m4 not found
Checking for forbidden M4 macros...
***Error***: some autoconf macros required to build avant-panel-menu
  were not found in your aclocal path, or some forbidden
  macros were found.  Perhaps you need to adjust your
  ACLOCAL_FLAGS?


Ideas?

---

### Post by searayman on 2007-02-06
> **Scotty562 said:**
> Did anyone find a way to get the Beryl preview window to work with this wonderful gem?

no, mine didnt work

ubuntu edgy with beryl is what i tried on, with latest beryl svn

---

### Post by KungfooChris on 2007-02-07
This bar installed and is working perfectly from the SVN for me.  The only problem I have is that I can not move it around. I am running a nVidia card with two monitors using twinview.  So the bar displays in the middle of the desktop, or in my case partly on my left monitor's right side and partly on my right monitors left side.  Anyone have any ideas on how to solve this?

Thanks,

-- Chris

---

### Post by wingchun on 2007-02-07
> **gansinho said:**
> just install the dev packages of them! here I did and autogen worked well

hi

can explain how to do what you daid ?

thanks

---

### Post by Cheizzz on 2007-02-07
Pormogo: it seems that in the latest SVN version avant draws the background OVER your icons. and since the background's transparant, you get that blurry effect, i think. 
try enabling the patern engine, and report back if it draws the pattern over your icons.

Wingchun: he means: install the development packages for the listed packages. in this case just install : libgnome-desktop-dev
That will also take care of the other dependancies.
after installing those packages, i could "make" the file.

hope my comments are helpfull

---

### Post by wingchun on 2007-02-07
cheizzz

"Wingchun: he means: install the development packages for the listed packages. in this case just install : libgnome-desktop-dev
That will also take care of the other dependancies.
after installing those packages, i could "make" the file."

thanks a lot

regards

---

### Post by wingchun on 2007-02-07
hi all

it's me again. I hope you will understand i'm a neewbie and i always search before asking but i can't stay several hours each day to find an answer and a lot of time i don't find without asking, so ...

my problem is :
when i launch awn in a terminal i have this 

(process:28980): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

and

**AWN-X** : Getting icon from X failed for avant-window-navigator
**AWN-X** : Getting icon from X failed for avant-window-navigator
**AWN-X** : Getting icon from X failed for avant-window-navigator

but awn seems to work fine .... ???

and the last one is when i launch avant-preferences :

(avant-preferences:28849): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 250, in ?
    app = main()
  File "/usr/local/bin/avant-preferences", line 125, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=APP) 
RuntimeError: could not create GladeXML object


i really don't know what i have to do to correct this so if someone can help me again, it would be great. i've already look on the developper site but find nothing


regards

---

### Post by searayman on 2007-02-07
> **KungfooChris said:**
> This bar installed and is working perfectly from the SVN for me.  The only problem I have is that I can not move it around. I am running a nVidia card with two monitors using twinview.  So the bar displays in the middle of the desktop, or in my case partly on my left monitor's right side and partly on my right monitors left side.  Anyone have any ideas on how to solve this?

Thanks,

-- Chris

at the moment i dont think you can move the bar around, but i think it is a feature he is workign on. ALso i think he is also tryign to fix soemthign for dual monitor displays.

---

### Post by reacocard on 2007-02-07
I just installed this (SVN), and it completely rocks. 

:guitar: 

A few rough edges, but it's remarkable how good it is for an 0.1+svn release.

If anyone's interested, I'll try to build a deb from svn for those too lazy to compile. :p

---

### Post by searayman on 2007-02-07
we need this in a ubuntu repository so our update managers will let us know when new version are out, and then it will update them.

---

### Post by reacocard on 2007-02-07
> **searayman said:**
> we need this in a ubuntu repository so our update managers will let us know when new version are out, and then it will update them.

I can provide a repository.

EDIT: Repository up, using deb from the front page. Add the following to your /etc/apt/sources.list:

```
deb http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
```

Save, then do the following in a terminal:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install avant-window-navigator
```

SVN debs coming soon. Edit: SVN available, use sudo apt-get install avant-window-navigator-svn instead.

---

### Post by searayman on 2007-02-07
> **reacocard said:**
> I can provide a repository.

does that mean you will put it in the repository too? And can u tell us it when you have done it?

---

### Post by reacocard on 2007-02-07
> **searayman said:**
> does that mean you will put it in the repository too? And can u tell us it when you have done it?

Already done.  (see above^)

---

### Post by searayman on 2007-02-07
> **reacocard said:**
> Already done.  (see above^)

ok cool, but i want svn, so i guesse i need to wait. PLease tell us when that id done.

---

### Post by sxturbo on 2007-02-07
This is the error I am getting after running autogen.sh.

Any ideas? Im a n00b too :(

```

/usr/bin/gnome-autogen.sh

checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.60

checking for automake >= 1.9...

  testing automake-1.9... 
found 1.9.6

checking for libtool >= 1.5...

  testing libtoolize... 
found 1.5.22

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.12.4

checking for intltool >= 0.30...

  testing intltoolize... 
found 0.35.0

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.20

Checking for required M4 macros...


Checking for forbidden M4 macros...

**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.


Processing ./configure.in


Running libtoolize...

You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.
Putting files in AC_CONFIG_AUX_DIR, `..'.

Running glib-gettextize... Ignore non-fatal messages.

Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running intltoolize...

intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite

```

---

### Post by reacocard on 2007-02-07
> **searayman said:**
> ok cool, but i want svn, so i guesse i need to wait. PLease tell us when that id done.

Done. Add this to your sources.list:
```
deb http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
```

then do this in terminal:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install avant-window-navigator-svn
```

Also, the stable package didn't work in the repo. Borked my apt when I used it (**** checkinstall), so it's not available right now. I'll rebuild it later.

EDIT: updated command sequence to remove schema install, as it is no longer necessary. Also, stable packages are available, just remove the -svn from the last command above.

---

### Post by searayman on 2007-02-07
> **reacocard said:**
> Done. Add this to your sources.list:
```
deb http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
```

then do this in terminal:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install avant-window-navigator-svn
wget http://download.tuxfamily.org/syzygy42/misc/avant-window-navigator.schemas
gconftool-2 --install-schema-file=avant-window-navigator.schemas
rm avant-window-navigator.schemas
```

Also, the stable package didn't work in the repo. Borked my apt when I used it, so it's not available right now. I'll rebuild it later.

shoudl i uninstall mine first?

and will you keep this updated with the latest svn?

---

### Post by reacocard on 2007-02-07
> **searayman said:**
> shoudl i uninstall mine first?

and will you keep this updated with the latest svn?

Yes, uninstall first.

I'll keep it updated. I already maintain svn builds of Exaile, so I'll just adapt the script I use for that to do this as well.

---

### Post by searayman on 2007-02-07
> **reacocard said:**
> Yes, uninstall first.

I'll keep it updated. I already maintain svn builds of Exaile, so I'll just adapt the script I use for that to do this as well.

ok cool did it, so now when he updates that svn my update manager in ubuntu will notify me and it will download and update it for me when i click update?

---

### Post by iamhugeinjapan on 2007-02-07
If I intepret the blog correctly, I believe you don't need to do the following gconf command with the svn code now:

```

gconftool-2 --install-schema-file=avant-window-navigator.schemas

```

---

### Post by reacocard on 2007-02-07
> **searayman said:**
> ok cool did it, so now when he updates that svn my update manager in ubuntu will notify me and it will download and update it for me when i click update?

Not quite. I still have to run the update script on my end after every svn update, but I'll run it every day or two, so it'll always be up-to-date.

---

### Post by reacocard on 2007-02-07
> **iamhugeinjapan said:**
> If I intepret the blog correctly, I believe you don't need to do the following gconf command with the svn code now:

```

gconftool-2 --install-schema-file=avant-window-navigator.schemas

```

Excellent. Can someone test this please? Just install the package from my repo as above, but skip the commands after 'sudo apt-get install avant-window-navigator-svn'.  Make sure you don't already have the schemas installed.

---

### Post by iamhugeinjapan on 2007-02-07
I haven't used your repo but yesterday I installed it via svn and didnt do that line since I read it had been fixed. Worked fine. But other people may get different results, as evidence from the posts for help in this thread! :)

edit: Here's the blog part I refer to, from the 6th of Feb

> 
I have changed the gconf code , so you should not be getting anymore segfaults after the make install.


[http://njpatel.blogspot.com/2007/02/some-updates.html](http://njpatel.blogspot.com/2007/02/some-updates.html)

---

### Post by molgar on 2007-02-08
> **searayman said:**
> we need this in a ubuntu repository so our update managers will let us know when new version are out, and then it will update them.

As I said before, Avant Window Manager is on Treviño's repository for Edgy: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)

SVN version only, updated daily.

---

### Post by stiankarlsen on 2007-02-08
what about dapper repos?

---

### Post by reacocard on 2007-02-08
> **molgar said:**
> As I said before, Avant Window Manager is on Treviño's repository for Edgy: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org)

SVN version only, updated daily.

Yeah, well, Trevino's repo also includes a bunch of other packages, some of which override the Ubuntu packages. I prefer not to override Ubuntu's packages unless necessary, so I'll maintain my AWN-only repo as well, and I'll also try to have packages of stable versions.

---

### Post by reacocard on 2007-02-08
> **stiankarlsen said:**
> what about dapper repos?

I don't run Dapper so I can't build debs for it, but if someone else builds the debs ([_[COLOR="Sienna"]properly[/COLOR]_]("http://www.ubuntuforums.org/showthread.php?t=51003")! no checkinstall.) and sends them to me, I'll put them up in my repo.

---

### Post by P_Badger on 2007-02-08
It's been asked a few times, but I couldn't find an answer to it, so, how can one make the *active * icon visible? It seems that the background square likes to cover it, and there isn't a whole lot I can do to make it appear.

Thanks for any help.

Edit: Well, I grabbed the svn from Reacocard's repository just now, installed it, and AWN works properly. : O

---

### Post by wingchun on 2007-02-08
hi all

i tried a lot of time to install and unsinstall Awn with deb and compile and now i wish to clean all things about awn to make a fresh and clean install. So what is the way to unsinstall all things about awn ?

thanks

---

### Post by searayman on 2007-02-09
I helped the avant creator and created a wiki that we are buildign for it. Its a place for suggestions and how too's:

[http://awn.wetpaint.com/]("http://awn.wetpaint.com/")

i took the installation process from you post here if you don't mind; I gave you credit though.

---

### Post by reacocard on 2007-02-09
> **searayman said:**
> I helped the avant creator and created a wiki that we are buildign for it. Its a place for suggestions and how too's:

[http://awn.wetpaint.com/]("http://awn.wetpaint.com/")

i took the installation process from you post here if you don't mind; I gave you credit though.

Nice. I've added instructions for my repository.

---

### Post by searayman on 2007-02-09
> **reacocard said:**
> Nice. I've added instructions for my repository.

nice to here u liked the wiki, thanks for adding your repo instructions to it.

---

### Post by sog on 2007-02-10
i'll ask the dumb question here. after installing from the repo here ([http://download.tuxfamily.org/syzygy42/)](http://download.tuxfamily.org/syzygy42/)), as recommended here ([http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository)](http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository)), how do you start awn? 

i've tried avant-window-navigator, avant-window-navigator-svn, and awn. none worked ('command not found').

i'm sure i'm missing something obvious, but help's appreciated.

---

### Post by gansinho on 2007-02-10
to install from repositories it is recomended that I uninstall the svn compiled version right? ok, how do I do that?

---

### Post by kenkun on 2007-02-10
> **reacocard said:**
> Done. Add this to your sources.list:
```
deb http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
```

then do this in terminal:
```
wget http://download.tuxfamily.org/syzygy42/8434D43A.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install avant-window-navigator-svn
wget http://download.tuxfamily.org/syzygy42/misc/avant-window-navigator.schemas
gconftool-2 --install-schema-file=avant-window-navigator.schemas
rm avant-window-navigator.schemas
```

Also, the stable package didn't work in the repo. Borked my apt when I used it (**** checkinstall), so it's not available right now. I'll rebuild it later.

gettin a 404 not found when i do
wget [http://download.tuxfamily.org/syzygy42/misc/avant-window-navigator.schemas](http://download.tuxfamily.org/syzygy42/misc/avant-window-navigator.schemas)
has that file been removed?

---

### Post by kenkun on 2007-02-10
> **gansinho said:**
> to install from repositories it is recomended that I uninstall the svn compiled version right? ok, how do I do that?

i did
```
sudo apt-get autoremove avant-window-navigator
```

if that doesn't work, do 
```
sudo apt-get remove avant-window-navigator
```

someone please check me on this.. =]

---

### Post by searayman on 2007-02-10
> **sog said:**
> i'll ask the dumb question here. after installing from the repo here ([http://download.tuxfamily.org/syzygy42/)](http://download.tuxfamily.org/syzygy42/)), as recommended here ([http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository)](http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository)), how do you start awn? 

i've tried avant-window-navigator, avant-window-navigator-svn, and awn. none worked ('command not found').

i'm sure i'm missing something obvious, but help's appreciated.

i woudl think it would be avant-window-navigator but check in applications>accessories>Avant Windows Navigator.

but i really am not sure, i didnt build the repo. If it dotn work i would follow the svn way on that wiki, its simple enough

---

### Post by searayman on 2007-02-10
> **reacocard said:**
> Nice. I've added instructions for my repository.

people are having trouble with your repo it dont seem to be working: Check out the comments here:

[http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository](http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository)

---

### Post by reacocard on 2007-02-10
Sorry about the problems, my svn update script wasn't working right. Should be fixed now.

@kenkun - Yes, it has been removed as it is no longer necessary.

---

### Post by luopio on 2007-02-11
> **stiankarlsen said:**
> When using autogen.sh, I get:

Ideas?

For those of you who are still fighting with this issue I recommend installing **automake1.9** and removing whatever older version you have. This fixed things for me.

---

### Post by chalewa on 2007-02-11
Seems like I get an error at just about every point....

Running autoconf...
configure.in:55: error: possibly undefined macro: AM_GCONF_SOURCE_2
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.


any ideas?

---

### Post by FunnyLookinHat on 2007-02-13
Looks like you need to install the libgconf2-dev package?

sudo apt-get install libgconf2-dev

---

### Post by searayman on 2007-02-13
any one want to make a Installing FAQ at the awn wiki? you coudl take common questions from this thread and put there answers there?

---

### Post by iamhugeinjapan on 2007-02-14
The latest version of this is really good, thanks for updating the repo. I like being able to swap the use of arrows to open tasks.

I found that I was having trouble with some windows not gaining focus when I wanted them. This seems to have been fixed by changing a Beryl setting. In General Options there is a' Level of Focus Stealing Prevention' option which was set to Low. I set it to Off and have had no further troubles.

---

### Post by linkrjr on 2007-02-15
I am having some problems to install some of the needed libraries.
For instance, libgnome-desktop-dev and libgtk2.0-dev.
I am using ubuntu dapper.

Is it possible to install avant on dapper?
Does anyone have any clue?

I would appreciate.

Cheers

---

### Post by souteneur3190 on 2007-02-15
(avant-window-navigator:12302): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

(avant-window-navigator:12302): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

i cant open any programs

---

### Post by mmacintyre on 2007-02-15
Hi not sure if anyone is still following this post.  I am brand new to Linux and trying to get my first thing working.  I have been able to follow all the steps from Opition 1 on the first page of this thread, however when I get to the step "make" it gives me this error

make: *** No targets specified and no makefile found.  Stop.

I seem to be in the correct directory.
What to I need to do to get around this, I seem to be very close to finishing there is only one step left

thanks for the help,

Mike

---

### Post by reacocard on 2007-02-15
> **linkrjr said:**
> I am having some problems to install some of the needed libraries.
For instance, libgnome-desktop-dev and libgtk2.0-dev.
I am using ubuntu dapper.

Is it possible to install avant on dapper?
Does anyone have any clue?

I would appreciate.

Cheers

It should be possible, if all the dependencies are available. What error are you getting, exactly?

---

### Post by reacocard on 2007-02-15
> **souteneur3190 said:**
> (avant-window-navigator:12302): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

(avant-window-navigator:12302): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

i cant open any programs

Are you using stable or SVN? Did you compile from source or use the repo?

---

### Post by reacocard on 2007-02-15
> **mmacintyre said:**
> Hi not sure if anyone is still following this post.  I am brand new to Linux and trying to get my first thing working.  I have been able to follow all the steps from Opition 1 on the first page of this thread, however when I get to the step "make" it gives me this error

make: *** No targets specified and no makefile found.  Stop.

I seem to be in the correct directory.
What to I need to do to get around this, I seem to be very close to finishing there is only one step left

thanks for the help,

Mike

You are probably in the wrong directory, or ./configure failed to work properly. Could you try following the guide again, just to make sure you didn't accidentally skip a step?

---

### Post by souteneur3190 on 2007-02-16
i have a problem with beryl, with out beryl when i run awn i get and ugly  black thing around it (i kno i need to run beryl) but in this ugly form i can click on an icon on the bottom and open windows that are minimized.  When i run beryl it looks much nicer (i kno this is how its supposed to work) but i can not open minimized windows...is something wrong with my settings?  Can sum1 post me there beryl settings that work with awn?

---

### Post by reacocard on 2007-02-16
> **souteneur3190 said:**
> i have a problem with beryl, with out beryl when i run awn i get and ugly  black thing around it (i kno i need to run beryl) but in this ugly form i can click on an icon on the bottom and open windows that are minimized.  When i run beryl it looks much nicer (i kno this is how its supposed to work) but i can not open minimized windows...is something wrong with my settings?  Can sum1 post me there beryl settings that work with awn?

Sure. Mine are attached, just use beryl's import option on them.

---

### Post by mmacintyre on 2007-02-17
Hi, ok so i have just done a fresh install of 6.10 and I am now trying to install AWN, I am following option 2 from the first page.  I get all the way to the "./autogen.sh and the output is below.  I move onto the next step "make" and I get this error "bash: make: command not found"  Does anyone know how to get around this or what I need to do, 

thanks,  Mike

```
checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
found 2.60

checking for automake >= 1.9...

  testing automake-1.9... 
found 1.9.6

checking for libtool >= 1.5...

  testing libtoolize... 
found 1.5.22

checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.12.4

checking for intltool >= 0.30...

  testing intltoolize... 
found 0.35.0

checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.20

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
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.


Running intltoolize...


Running aclocal-1.9...


Running autoconf...


Running autoheader...


Running automake-1.9...

configure.in: installing `./install-sh'
configure.in: installing `./missing'
src/Makefile.am: installing `./depcomp'

Running ./configure --enable-maintainer-mode ...

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking how to create a ustar tar archive... gnutar
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for style of include used by make... none
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl.exe... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for f95... no
checking for fort... no
checking for xlf95... no
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
appending configuration tag "F77" to libtool
checking for intltool >= 0.34... 0.35.0 found
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
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  en_GB
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.8.0... yes (version 2.12.4)
checking pkg-config is at least version 0.9.0... yes
checking for AWN... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
configure: creating ./config.status
config.status: creating Makefile
config.status: creating avant-preferences/Makefile
config.status: creating src/Makefile
config.status: creating data/Makefile
config.status: creating data/active/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands
Now type `make' to compile avant-panel-menu

```

---

### Post by reacocard on 2007-02-17
> **mmacintyre said:**
> Hi, ok so i have just done a fresh install of 6.10 and I am now trying to install AWN, I am following option 2 from the first page.  I get all the way to the "./autogen.sh and the output is below.  I move onto the next step "make" and I get this error "bash: make: command not found"  Does anyone know how to get around this or what I need to do, 

thanks,  Mike

try
```
sudo apt-get install make build-essential
```

---

### Post by mmacintyre on 2007-02-17
Thanks that totally worked and got me through to the next step.  Now when I get here, obviously I can change to the data directory but when I try to run the next command "gconftool-2--....... I get this error below


IMPORTANT!
There is one last step which many people will miss! In order to avoid a seg-fault do the following:
Quote:
cd data
gconftool-2 --install-schema-file=avant-window-navigator.schemas


```

IMPORTANT!
I/O warning : failed to load external entity "avant-window-navigator.schemas"
Failed to open `avant-window-navigator.schemas': No such file or directory

```

I am sorry but I have dug around on all the threads and can't find anything.  Any ideas on how to get around it?

---

### Post by reacocard on 2007-02-17
If you're installing from SVN, the schemas aren't necessary anymore, which is why that file isn't there. You should just be able to launch AWN now.

---

### Post by mmacintyre on 2007-02-17
OK, thanks you have been a great help!

---

### Post by Treviño on 2007-02-20
I don't know if this "news" has just been shared, but I package from svn since the beginning of this project and you can find my packages always updated at [http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/](http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/)

Latest one includes also the patches I wrote and that now have been included on svn too:
- [http://code.google.com/p/avant-window-navigator/issues/detail?id=92](http://code.google.com/p/avant-window-navigator/issues/detail?id=92)
- [http://code.google.com/p/avant-window-navigator/issues/detail?id=99](http://code.google.com/p/avant-window-navigator/issues/detail?id=99)
- [http://code.google.com/p/avant-window-navigator/issues/detail?id=100](http://code.google.com/p/avant-window-navigator/issues/detail?id=100)
- [http://code.google.com/p/avant-window-navigator/issues/detail?id=102](http://code.google.com/p/avant-window-navigator/issues/detail?id=102)


:)

---

### Post by reacocard on 2007-02-20
> **Treviño said:**
> I don't know if this "news" has just been shared, but I package from svn since the beginning of this project and you can find my packages always updated at [http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/](http://3v1n0.tuxfamily.org/dists/edgy/3v1n0/)

Latest one includes also the patches I wrote and that now have been included on svn too:
- [http://code.google.com/p/avant-window-navigator/issues/detail?id=92](http://code.google.com/p/avant-window-navigator/issues/detail?id=92)
- [http://code.google.com/p/avant-window-navigator/issues/detail?id=99](http://code.google.com/p/avant-window-navigator/issues/detail?id=99)
- [http://code.google.com/p/avant-window-navigator/issues/detail?id=100](http://code.google.com/p/avant-window-navigator/issues/detail?id=100)
- [http://code.google.com/p/avant-window-navigator/issues/detail?id=102](http://code.google.com/p/avant-window-navigator/issues/detail?id=102)


:)

Yes, but it's mixed into your repo with all that other stuff. What if people don't want that other stuff, some of which overrides Ubuntu's packages? My repo has a section exclusively for AWN, eliminating that problem. Also, I have both svn and stable versions.

My AWN repo is here, for those too lazy to search the thread: [http://syzygy42.tuxfamily.org/dists/edgy/avant-window-navigator/](http://syzygy42.tuxfamily.org/dists/edgy/avant-window-navigator/)

---

### Post by gansinho on 2007-02-21
hello, awn is working pretty well here... I just hahve one annoying problem:
I installed AWN while in gnome, latter on I migrated to KDE using (sudo aptitude install kubuntu-desktop) and I'm loading KDE in the login screen since then...
the problem is: the icons in my dock doesn't change when I change the iconset and as far as I remember they use to do that in gnome...
I'm using the SVN version (updating the svn manually) and I don't know if this is a bug or just a misconfigured thing...

---

### Post by Treviño on 2007-02-21
> **reacocard said:**
> Yes, but it's mixed into your repo with all that other stuff. What if people don't want that other stuff, some of which overrides Ubuntu's packages? My repo has a section exclusively for AWN, eliminating that problem. Also, I have both svn and stable versions.

My AWN repo is here, for those too lazy to search the thread: [http://syzygy42.tuxfamily.org/dists/edgy/avant-window-navigator/](http://syzygy42.tuxfamily.org/dists/edgy/avant-window-navigator/)Oh I didn't know there was just a repo, so it's ok... ;)

---

### Post by searayman on 2007-02-22
the awn wiki now has a neat ajax based forum. So you can discuss or ask/answer awn questiosn there. below is a link:

[http://www.planetblur.org/hosted/awnforum/index.php?shard=forum]("http://www.planetblur.org/hosted/awnforum/index.php?shard=forum")

---

### Post by Boni2k on 2007-02-22
I get this view with the errors:
[[IMG]http://img521.imageshack.us/img521/5819/bildschirmfoto1ro6.th.png[/IMG]](http://img521.imageshack.us/my.php?image=bildschirmfoto1ro6.png)
What am I doing wrong? :)

---

### Post by reacocard on 2007-02-22
> **gansinho said:**
> hello, awn is working pretty well here... I just hahve one annoying problem:
I installed AWN while in gnome, latter on I migrated to KDE using (sudo aptitude install kubuntu-desktop) and I'm loading KDE in the login screen since then...
the problem is: the icons in my dock doesn't change when I change the iconset and as far as I remember they use to do that in gnome...
I'm using the SVN version (updating the svn manually) and I don't know if this is a bug or just a misconfigured thing...

This is probably a bug. AWN is developed under Gnome, so it's unsurprising that it has bugs with KDE. You can file a bug report here: [http://code.google.com/p/avant-window-navigator/issues/list](http://code.google.com/p/avant-window-navigator/issues/list)

---

### Post by gansinho on 2007-02-23
reacocard do you know if awn will continue to be gnome "only" ?
I know that there are severall docks for gnome, but none are just like this...

---

### Post by Boni2k on 2007-02-23
Any ideas about my problem? Anyone?

---

### Post by reacocard on 2007-02-23
> **gansinho said:**
> reacocard do you know if awn will continue to be gnome "only" ?
I know that there are severall docks for gnome, but none are just like this...

I don't know. However, while AWN will probably continue to have gnome dependencies, it will undoubtedly get patched to work better under KDE. All we need are a few KDE-using testers who can file a bug report, or perhaps even patches for the problems.

---

### Post by reacocard on 2007-02-23
Boni2k, that black bar is caused by not running a compositor on your computer, which AWN needs to work. There are currently three compositors I know of: Beryl, Compiz and xcompmgr. I would recommend Beryl, but xcompmgr is good if you don't want to replace your existing window manager.  Search these forums for any of these three and you'll find all you need to install them.

---

### Post by Boni2k on 2007-02-23
Oh, I didn't knew that...
I don't want to use those Beryl stuff, my PC is kinda slow for such software. I might have a look at xcom...
Thanks for your help!

---

### Post by gansinho on 2007-02-23
reacocard I submitted an issue in the project home page, its the issue number 111 at [http://code.google.com/p/avant-window-navigator/issues/detail?id=111&can=2&q=]("http://code.google.com/p/avant-window-navigator/issues/detail?id=111&can=2&q=")
My English is pretty bad, so if you think that I was not able to report the issue porperly just let me know that I can try to rewrite it

---

### Post by reacocard on 2007-02-23
> **gansinho said:**
> reacocard I submitted an issue in the project home page, its the issue number 111 at [http://code.google.com/p/avant-window-navigator/issues/detail?id=111&can=2&q=]("http://code.google.com/p/avant-window-navigator/issues/detail?id=111&can=2&q=")
My English is pretty bad, so if you think that I was not able to report the issue porperly just let me know that I can try to rewrite it

Looks good to me.

---

### Post by kwiwiphotography on 2007-02-26
You need to install the gnome-common module and make
sure the gnome-autogen.sh script is in your $PATH.

What should i do there?

---

### Post by kwiwiphotography on 2007-02-26
Nevermind i missed a step that i thought i did
sry

---

### Post by jonah1980 on 2007-03-03
hi, i've installed avant-window-navigator, but i've decided not to use it as i prefer to use gdesklets as it doesn't need beryl etc to run. but how do i know uninstall it to tidy up my machine?

---

### Post by reacocard on 2007-03-03
> **jonah1980 said:**
> hi, i've installed avant-window-navigator, but i've decided not to use it as i prefer to use gdesklets as it doesn't need beryl etc to run. but how do i know uninstall it to tidy up my machine?

Well, that depends on how you installed it. If from the repo/packages, just use apt/synaptic to remove it. if from source, then 'sudo make uninstall' in the source dir should work.

---

### Post by jonah1980 on 2007-03-03
doesnt' seem to work, it still runs after uninstalling:

> 
jonah@jonah-desktop:~$ cd '/home/jonah/avant-window-navigator' 
jonah@jonah-desktop:~/avant-window-navigator$ sudo make uninstallMaking uninstall in src
make[1]: Entering directory `/home/jonah/avant-window-navigator/src'
 rm -f '/usr/bin/avant-window-navigator'
make[1]: Leaving directory `/home/jonah/avant-window-navigator/src'
Making uninstall in data
make[1]: Entering directory `/home/jonah/avant-window-navigator/data'
Making uninstall in active
make[2]: Entering directory `/home/jonah/avant-window-navigator/data/active'
 rm -f '/usr/share/avant-window-navigator/active/glow.png'
 rm -f '/usr/share/avant-window-navigator/active/glow2.png'
 rm -f '/usr/share/avant-window-navigator/active/glow3.png'
 rm -f '/usr/share/avant-window-navigator/active/glow4.png'
 rm -f '/usr/share/avant-window-navigator/active/glow5.png'
 rm -f '/usr/share/avant-window-navigator/active/glow6.png'
 rm -f '/usr/share/avant-window-navigator/active/glow7.png'
 rm -f '/usr/share/avant-window-navigator/active/glow8.png'
 rm -f '/usr/share/avant-window-navigator/active/glow9.png'
make[2]: Leaving directory `/home/jonah/avant-window-navigator/data/active'
make[2]: Entering directory `/home/jonah/avant-window-navigator/data'
 rm -f '/usr/share/applications/avant-window-navigator.desktop'
 rm -f '/usr/share/avant-window-navigator/avant-window-navigator.svg'
 rm -f '/usr/share/avant-window-navigator/avant-window-navigator-24.png'
 rm -f '/usr/share/avant-window-navigator/avant-window-navigator-48.png'
make[2]: Leaving directory `/home/jonah/avant-window-navigator/data'
make[1]: Leaving directory `/home/jonah/avant-window-navigator/data'
Making uninstall in po
make[1]: Entering directory `/home/jonah/avant-window-navigator/po'
linguas="en_GB "; \
        for lang in $linguas; do \
          rm -f /usr/share/locale/$lang/LC_MESSAGES/avant-window-navigator.mo; \
          rm -f /usr/share/locale/$lang/LC_MESSAGES/avant-window-navigator.mo.m; \
        done
make[1]: Leaving directory `/home/jonah/avant-window-navigator/po'
Making uninstall in avant-preferences
make[1]: Entering directory `/home/jonah/avant-window-navigator/avant-preferences'
 rm -f '/usr/share/applications/avant-preferences.desktop'
 rm -f '/usr/share/avant-window-navigator/window.glade'
make[1]: Leaving directory `/home/jonah/avant-window-navigator/avant-preferences'
make[1]: Entering directory `/home/jonah/avant-window-navigator'
make[1]: Nothing to be done for `uninstall-am'.
make[1]: Leaving directory `/home/jonah/avant-window-navigator'
jonah@jonah-desktop:~/avant-window-navigator$ 


---

### Post by reacocard on 2007-03-03
Weird, looks like it uninstalled. "rm -f '/usr/bin/avant-window-navigator'" should have trashed the main executable at least, prevent awn from restarting.

---

### Post by jonah1980 on 2007-03-04
yeah doesnt seem to have, it still starts up which is really odd

---

### Post by Quickdood on 2007-03-06
Is there a way to auto hide this bar or atleast make it so it goes in the background when a window goes over it in full screen?

---

### Post by reacocard on 2007-03-06
> **Quickdood said:**
> Is there a way to auto hide this bar or atleast make it so it goes in the background when a window goes over it in full screen?

Yes, but only in the SVN version. To enable it, go to Applications -> System -> Configuration Editor, then apps -> avant-window-navigator and check 'auto_hide'.

---

### Post by Quickdood on 2007-03-06
> **reacocard said:**
> Yes, but only in the SVN version. To enable it, go to Applications -> System -> Configuration Editor, then apps -> avant-window-navigator and check 'auto_hide'.
Is the link on the first post for the SVN version still up-to-date because that is the one I installed and when I go into preferences there is no auto hide option.  If the link on the main page is old how can I update to the new one, do I have to un-install the version I currently have?

---

### Post by reacocard on 2007-03-07
> **Quickdood said:**
> Is the link on the first post for the SVN version still up-to-date because that is the one I installed and when I go into preferences there is no auto hide option.  If the link on the main page is old how can I update to the new one, do I have to un-install the version I currently have?

To uninstall the current version, do 'sudo make uninstall' in the source directory.

For the latest SVN, I recommend using my Ubuntu repository. See [this wiki page]("http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository") for instructions.

---

### Post by Quickdood on 2007-03-07
> **reacocard said:**
> To uninstall the current version, do 'sudo make uninstall' in the source directory.

For the latest SVN, I recommend using my Ubuntu repository. See [this wiki page]("http://awn.wetpaint.com/page/Ubuntu+Edgy+Repository") for instructions.
Thank you! I am gonna try this as soon as I get home from work!

---

### Post by Quickdood on 2007-03-07
I just installed using the Ubuntu repository.  I am using the SVN version.  It works but I cant access the preferences.  When I try to do so in the console this is what I get:
> /usr/local/share/avant-window-navigator/window.glade

(avant-preferences:5831): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 264, in ?
    app = main()
  File "/usr/local/bin/avant-preferences", line 131, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=APP) 
RuntimeError: could not create GladeXML object

---

### Post by reacocard on 2007-03-07
> **Quickdood said:**
> I just installed using the Ubuntu repository.  I am using the SVN version.  It works but I cant access the preferences.  When I try to do so in the console this is what I get:

It sounds like your old compiled version didn't uninstall completely. do this in a terminal:
```
sudo rm -f /usr/local/bin/avant-window-navigator
sudo rm -f /usr/local/bin/avant-preferences
```

---

### Post by Quickdood on 2007-03-07
> **reacocard said:**
> It sounds like your old compiled version didn't uninstall completely. do this in a terminal:
```
sudo rm -f /usr/local/bin/avant-window-navigator
sudo rm -f /usr/local/bin/avant-preferences
```

Thank you for being so helpful, that did the trick.  I have the SVN installed from the repository but when i go into preferences for the life of me I cant find the auto hide function.  Did they take it out of the new version?  Which tab under preferences is it under?  I dont see it under general, task appearance, bar appearance, glass engine, or pattern engine.  Is there a way to edit preferences from a text based file maybe with more options?

---

### Post by reacocard on 2007-03-07
> **Quickdood said:**
> Thank you for being so helpful, that did the trick.  I have the SVN installed from the repository but when i go into preferences for the life of me I cant find the auto hide function.  Did they take it out of the new version?  Which tab under preferences is it under?  I dont see it under general, task appearance, bar appearance, glass engine, or pattern engine.  Is there a way to edit preferences from a text based file maybe with more options?

It's not in preferences, it's a hidden option in gconf. Open the Configuration Editor (Applications -> System), then navigate to apps -> avant-window-navigator and check the auto_hide option.

---

### Post by Quickdood on 2007-03-07
> **reacocard said:**
> It's not in preferences, it's a hidden option in gconf. Open the Configuration Editor (Applications -> System), then navigate to apps -> avant-window-navigator and check the auto_hide option.

Thanks that worked!

---

### Post by jonah1980 on 2007-03-08
does anyone know how i can remove avant from my system? thanks...

---

### Post by reacocard on 2007-03-08
> **jonah1980 said:**
> does anyone know how i can remove avant from my system? thanks...

as make uninstall didn't work, do it the hard way:
```
sudo rm -f /usr/bin/avant-window-navigator
sudo rm -f /usr/bin/avant-preferences
sudo rm -rf /usr/share/avant-window-navigator/
sudo rm -f usr/share/applications/avant-preferences.desktop
sudo rm -f usr/share/applications/avant-window-navigator.desktop
```
that should get rid of just about all of it.

---

### Post by jonah1980 on 2007-03-08
> **reacocard said:**
> as make uninstall didn't work, do it the hard way:
```
sudo rm -f /usr/bin/avant-window-navigator
sudo rm -f /usr/bin/avant-preferences
sudo rm -rf /usr/share/avant-window-navigator/
sudo rm -f usr/share/applications/avant-preferences.desktop
sudo rm -f usr/share/applications/avant-window-navigator.desktop
```
that should get rid of just about all of it.

none of the above seemed to work either. i still have it in main menu/accessories and it still loads up when clicking on it

---

### Post by reacocard on 2007-03-08
> **jonah1980 said:**
> none of the above seemed to work either. i still have it in main menu/accessories and it still loads up when clicking on it

Try this:
```
sudo rm -f /usr/share/applications/avant-preferences.desktop
sudo rm -f /usr/share/applications/avant-window-navigator.desktop
sudo rm -f /usr/local/bin/avant-window-navigator
sudo rm -f /usr/local/bin/avant-preferences
sudo rm -rf /usr/local/share/avant-window-navigator/
sudo rm -f /usr/local/share/applications/avant-preferences.desktop
sudo rm -f /usr/local/share/applications/avant-window-navigator.desktop
```

If that doesn't work, then post the output of 'which avant-window-navigator'

---

### Post by jonah1980 on 2007-03-08
> **reacocard said:**
> Try this:
```
sudo rm -f /usr/share/applications/avant-preferences.desktop
sudo rm -f /usr/share/applications/avant-window-navigator.desktop
sudo rm -f /usr/local/bin/avant-window-navigator
sudo rm -f /usr/local/bin/avant-preferences
sudo rm -rf /usr/local/share/avant-window-navigator/
sudo rm -f /usr/local/share/applications/avant-preferences.desktop
sudo rm -f /usr/local/share/applications/avant-window-navigator.desktop
```

If that doesn't work, then post the output of 'which avant-window-navigator'

jonah@jonah-desktop:~$ which avant-window-navigator
/usr/local/bin/avant-window-navigator
jonah@jonah-desktop:~$

---

### Post by reacocard on 2007-03-08
> **jonah1980 said:**
> jonah@jonah-desktop:~$ which avant-window-navigator
/usr/local/bin/avant-window-navigator
jonah@jonah-desktop:~$

I have no idea why it is still working, by all rights, it should have been flayed, drawn, quartered, and shot by that series of commands I gave you in my last post.

One last try:
```
sudo rm /usr/local/bin/avant-window-navigator
```
If that doesn't work, I'm throwing in the towel.

---

### Post by jonah1980 on 2007-03-09
that's stopped it executing at least thanks, so i've just removed the icon etc by hand. but hopefully there's no other messy files still lingering around...

---

### Post by lukew on 2007-03-13
FunnyLookinHat.

Thanks for the post; was not really happy with kiba but i think this is excellent. Great instructions worked a treat in litterally a minute or to.

Does anyone know how to get the ubuntu start menu on there? (The one icon added from  panel items and not the default 3 button one with words on it! )

Thanks

Luke

---

### Post by reacocard on 2007-03-13
> **lukew said:**
> FunnyLookinHat.

Thanks for the post; was not really happy with kiba but i think this is excellent. Great instructions worked a treat in litterally a minute or to.

Does anyone know how to get the ubuntu start menu on there? (The one icon added from  panel items and not the default 3 button one with words on it! )

Thanks

Luke

So far as I know, that is not possible yet. Embedded applets like that are a planned feature though, so if you stick around long enough it'll happen.

---

### Post by Pugwash on 2007-03-14
I get some errors when I try to "make", whats going wrong? Here's what I got when I ran "./config":

```
nasef@nasef-laptop:~/avant-window-navigator-0.1.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking how to create a ustar tar archive... gnutar
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
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
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
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
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
checking dynamic linker characteristics... GNU/Linux ld.so
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
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for intltool >= 0.34... 0.35.0 found
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
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for catalogs to be installed...  en_GB
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.7... yes
checking for GLIB - version >= 2.8.0... yes (version 2.10.3)
checking for AWN... yes
checking for gconftool-2... /usr/bin/gconftool-2
Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
Using $(sysconfdir)/gconf/schemas as install directory for schema files
configure: creating ./config.status
config.status: creating Makefile
config.status: creating avant-preferences/Makefile
config.status: creating src/Makefile
config.status: creating data/Makefile
config.status: creating data/active/Makefile
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

```

This from "make":

```
nasef@nasef-laptop:~/avant-window-navigator-0.1.1$ make
make  all-recursive
make[1]: Entering directory `/home/nasef/avant-window-navigator-0.1.1'
Making all in src
make[2]: Entering directory `/home/nasef/avant-window-navigator-0.1.1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/libwnck-1.0 -I/usr/include/gconf/2 -I/usr/include/orbit-2.0    -DDATADIR=\""/usr/local/share"\" -DGNOMELOCALEDIR=\""/usr/local/share/locale"\"   -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c; \
        then mv -f ".deps/main.Tpo" ".deps/main.Po"; else rm -f ".deps/main.Tpo"; exit 1; fi
main.c: In function &#8216;main&#8217;:
main.c:52: warning: unused variable &#8216;lab&#8217;
main.c: At top level:
awn-bar.h:51: warning: &#8216;parent_class&#8217; defined but not used
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/libwnck-1.0 -I/usr/include/gconf/2 -I/usr/include/orbit-2.0    -DDATADIR=\""/usr/local/share"\" -DGNOMELOCALEDIR=\""/usr/local/share/locale"\"   -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2 -MT awn-gconf.o -MD -MP -MF ".deps/awn-gconf.Tpo" -c -o awn-gconf.o awn-gconf.c; \
        then mv -f ".deps/awn-gconf.Tpo" ".deps/awn-gconf.Po"; else rm -f ".deps/awn-gconf.Tpo"; exit 1; fi
awn-gconf.c: In function &#8216;awn_notify_string&#8217;:
awn-gconf.c:136: warning: assignment discards qualifiers from pointer target type
awn-gconf.c: In function &#8216;awn_notify_color&#8217;:
awn-gconf.c:157: warning: passing argument 1 of &#8216;hex2float&#8217; discards qualifiers from pointer target type
awn-gconf.c: In function &#8216;awn_load_bool&#8217;:
awn-gconf.c:171: warning: passing argument 3 of &#8216;gconf_client_notify_add&#8217; from incompatible pointer type
awn-gconf.c: In function &#8216;awn_load_string&#8217;:
awn-gconf.c:179: warning: passing argument 3 of &#8216;gconf_client_notify_add&#8217; from incompatible pointer type
awn-gconf.c: In function &#8216;awn_load_float&#8217;:
awn-gconf.c:187: warning: passing argument 3 of &#8216;gconf_client_notify_add&#8217; from incompatible pointer type
awn-gconf.c: In function &#8216;awn_load_color&#8217;:
awn-gconf.c:202: warning: passing argument 3 of &#8216;gconf_client_notify_add&#8217; from incompatible pointer type
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DORBIT2=1 -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/libwnck-1.0 -I/usr/include/gconf/2 -I/usr/include/orbit-2.0    -DDATADIR=\""/usr/local/share"\" -DGNOMELOCALEDIR=\""/usr/local/share/locale"\"   -g -O2 -Wall -pedantic -std=c99 -fno-strict-aliasing -fmessage-length=0 -D_FORTIFY_SOURCE=2 -MT awn-bar.o -MD -MP -MF ".deps/awn-bar.Tpo" -c -o awn-bar.o awn-bar.c; \
        then mv -f ".deps/awn-bar.Tpo" ".deps/awn-bar.Po"; else rm -f ".deps/awn-bar.Tpo"; exit 1; fi
awn-bar.c:35: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;current_width&#8217;
awn-bar.c: In function &#8216;awn_bar_new&#8217;:
awn-bar.c:79: warning: passing argument 1 of &#8216;_position_window&#8217; from incompatible pointer type
awn-bar.c: In function &#8216;_on_expose&#8217;:
awn-bar.c:259: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;oWidth&#8217;
awn-bar.c:260: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;oHeight&#8217;
awn-bar.c:260: warning: unused variable &#8216;oHeight&#8217;
awn-bar.c:259: warning: unused variable &#8216;oWidth&#8217;
awn-bar.c: In function &#8216;do_shape_combine_mask&#8217;:
awn-bar.c:310: error: &#8216;Pixmap&#8217; undeclared (first use in this function)
awn-bar.c:310: error: (Each undeclared identifier is reported only once
awn-bar.c:310: error: for each function it appears in.)
awn-bar.c:310: error: syntax error before &#8216;pixmap&#8217;
awn-bar.c:315: warning: implicit declaration of function &#8216;XShapeQueryExtension&#8217;
awn-bar.c:315: warning: implicit declaration of function &#8216;GDK_WINDOW_XDISPLAY&#8217;
awn-bar.c:318: warning: implicit declaration of function &#8216;XShapeQueryVersion&#8217;
awn-bar.c:326: error: &#8216;pixmap&#8217; undeclared (first use in this function)
awn-bar.c:326: warning: implicit declaration of function &#8216;GDK_DRAWABLE_XID&#8217;
awn-bar.c:331: error: &#8216;None&#8217; undeclared (first use in this function)
awn-bar.c:334: warning: implicit declaration of function &#8216;XShapeCombineMask&#8217;
awn-bar.c:336: error: &#8216;ShapeInput&#8217; undeclared (first use in this function)
awn-bar.c:340: error: &#8216;ShapeSet&#8217; undeclared (first use in this function)
awn-bar.c: In function &#8216;awn_bar_resize&#8217;:
awn-bar.c:467: warning: ISO C forbids conversion of function pointer to object pointer type
awn-bar.c:467: warning: passing argument 2 of &#8216;g_timeout_add&#8217; from incompatible pointer type
make[2]: *** [awn-bar.o] Error 1
make[2]: Leaving directory `/home/nasef/avant-window-navigator-0.1.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nasef/avant-window-navigator-0.1.1'
make: *** [all] Error 2

```

---

### Post by Gorbachev on 2007-03-14
I got to:

gconftool-2 --install-schema-file=avant-window-navigator.schemas

and entered it after cd data, and... it didn't work. (failed to load external entity)

i tried it a few times, then decided to go ahead and launch avant, and it launched fine.. :confused: 

Well, it works. And it's not even that great. I guess I just like a nice wide bar at the bottom and top, so when firefox is maximized there is no background picture visible. Weird obsessive compulsive thing I have.

---

### Post by lukew on 2007-03-14
> **reacocard said:**
> So far as I know, that is not possible yet. Embedded applets like that are a planned feature though, so if you stick around long enough it'll happen.


Thanks reacocard for the information.

At the moment I have the AWT dock and then a very small unextended gnome panel which has the ubuntu start icon, clock and weather applet which kinda let the side down... ;)

Thanks again for your information. I will keep an eye out for future works.

Luke

---

### Post by reacocard on 2007-03-14
> **Pugwash said:**
> I get some errors when I try to "make", whats going wrong? Here's what I got when I ran "./config":

<snip>

Pugwash, don't use the 'stable' version, it's actually buggier than SVN. 

> **Gorbachev said:**
> I got to:

gconftool-2 --install-schema-file=avant-window-navigator.schemas

and entered it after cd data, and... it didn't work. (failed to load external entity)

i tried it a few times, then decided to go ahead and launch avant, and it launched fine.. :confused: 

Well, it works. And it's not even that great. I guess I just like a nice wide bar at the bottom and top, so when firefox is maximized there is no background picture visible. Weird obsessive compulsive thing I have.

If you're using SVN, the part about schemas is no longer necessary.


Maybe I need to start a new thread, I'm getting tired of answering these same questions over and over because I can't update the first post.

---

### Post by Gorbachev on 2007-03-14
Ok thanks, I just don't pay attention to instructions very well.

---

### Post by FuturePilot on 2007-03-14
When I tried to run it I got a segmentation fault and then it failed to start. I'm trying this on Dapper and I used the .deb Any ideas?

---

### Post by Gorbachev on 2007-03-14
If you used option one, did you forget the following step?

cd data
gconftool-2 --install-schema-file=avant-window-navigator.schemas

---

### Post by FuturePilot on 2007-03-14
No I used the .deb

---

### Post by reacocard on 2007-03-14
> **FuturePilot said:**
> No I used the .deb

The deb is edgy-only. You'll have to compile from SVN for dapper.

---

### Post by FuturePilot on 2007-03-15
Ah, I see. When I tried to compile it, it said there were dependencies missing, but I checked in Synaptic and they were there. Were they not the right version?

---

### Post by reacocard on 2007-03-15
> **FuturePilot said:**
> Ah, I see. When I tried to compile it, it said there were dependencies missing, but I checked in Synaptic and they were there. Were they not the right version?

You need the -dev packages for some of them. Just look them up again, and if there is a package of that name but with -dev on the end, install it. then try again.

---

### Post by banditti on 2007-03-15
is there something wrong with svn?

> # svn checkout [http://avant-window-navigator.googlecode.com/svn/trunk/](http://avant-window-navigator.googlecode.com/svn/trunk/) avant-window-navigator
svn: REPORT request failed on '/svn/!svn/vcc/default'
svn: REPORT of '/svn/!svn/vcc/default': 400 Bad Request ([http://avant-window-navigator.googlecode.com](http://avant-window-navigator.googlecode.com))


---

### Post by kaffekopp on 2007-03-15
Avant compiled just fine for me on edgy and worked perfectly from the start. (installed it on March 15th). However, after playing around a little with it, I can't get the text bubbles up any more... I've checked that the settings for text and background colors are set properly (ie. that they're not totally transparent). Anyone else have this problem?

---

### Post by Pugwash on 2007-03-16
> **reacocard said:**
> Pugwash, don't use the 'stable' version, it's actually buggier than SVN. 



If you're using SVN, the part about schemas is no longer necessary.


Maybe I need to start a new thread, I'm getting tired of answering these same questions over and over because I can't update the first post.


Thanks for the info, sorry if you've answered this before.

---

### Post by reacocard on 2007-03-16
> **Pugwash said:**
> Thanks for the info, sorry if you've answered this before.

I have, but it's ok. I think I'll start a new thread and cover affinity too, since that came out yesterday.

(If you have no idea what I'm talking about, go[ here]("http://code.google.com/p/affinity-search/").)

---

### Post by reacocard on 2007-03-16
[**[SIZE="3"]New Thread[/SIZE]**]("http://ubuntuforums.org/showthread.php?p=2307772#post2307772")

Please continue discussion there, I'll keep the first post updated so that questions don't have to be answered repeatedly. The new thread also covers affinity.

---

### Post by banditti on 2007-03-23
I could use help.

1.  I am using Treviño's avant-window-navigator in my sources.list
2.  When I run the program, I get the following:

```
root@todd-laptop:~# avant-window-navigator
Segmentation fault (core dumped)

```

Thoughts?

---

### Post by banditti on 2007-03-23
Also, sometimes I get:

```
root@todd-laptop:~# avant-window-navigator 

(process:8172): GLib-GObject-CRITICAL **: gtype.c:2240: initialization assertion failed, use IA__g_type_init() prior to this function

(process:8172): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

(process:8172): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault (core dumped)

```

Also, I originally tried to install from SVN and got basically the same.

---

### Post by What_the_deuce on 2007-04-06
Successful install of avant, thanks for the HOWTO, but, it is not quite working, for example, when i click on an item in the dock, nothing happens, it just bounces up and down.

also, it remains on top of all windows, and i can't seem to alter that. any help appreciated.

thanks.

---

### Post by reacocard on 2007-04-06
> **What_the_deuce said:**
> Successful install of avant, thanks for the HOWTO, but, it is not quite working, for example, when i click on an item in the dock, nothing happens, it just bounces up and down.

Turn off beryl's focus stealing prevention.

> also, it remains on top of all windows, and i can't seem to alter that. any help appreciated.

It always stays on top, that's not configurable. You can have it auto-hide though. Open your configuration editor (Apps - > System -> Configuration Editor), navigate to apps -> avant-window-navigator and check the 'auto_hide' option.

Also, *please* continue discussion in the new thread (see my post a few back), this thread is depreciated. I should ask a mod to close it.

---

### Post by bugz0r on 2007-04-12
I installed the svn version from the repo in the first post and it works fine, but when I right click to chnage preferences nothing happens. Also, When I click on an icon and select preferences a window saying change icon shows up, I click it but nothing happens. In gconf-editor under AWN for each option it says "this key has no schema" what does this mean? How can I add launchers to the bar?

---

### Post by reacocard on 2007-04-12
> **bugz0r said:**
> I installed the svn version from the repo in the first post and it works fine, but when I right click to chnage preferences nothing happens. Also, When I click on an icon and select preferences a window saying change icon shows up, I click it but nothing happens. In gconf-editor under AWN for each option it says "this key has no schema" what does this mean? How can I add launchers to the bar?

Please try the instructions in this thread: [http://ubuntuforums.org/showthread.php?p=2307772#post2307772](http://ubuntuforums.org/showthread.php?p=2307772#post2307772)
If you still have problems, please post them there.

---

### Post by dlaw on 2007-04-13
hey!

Thanks for the HOWTO.  I'm very new to Ubuntu (started using it this week).  Have got Beryl going.  I've had trouble getting kiba-dock and kooldock working. 

BUT

I just used your SVN install and it is AWESOME.  Directions worked perfectly

Thanks Again!

---

### Post by bugz0r on 2007-04-13
AWN is always on top, how do I make it stay underneath.

---

### Post by wulfhound on 2007-04-17
If you get a shift error try installing automake1.9. It is needed if you don't have it.

---

### Post by diskotek on 2007-04-22
> *** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gconf-2.0) were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AWN_CFLAGS
and AWN_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

what should i do next? i tried to install 
> 
diskotek@diskotek-desktop:~/Desktop/avant-window-navigator-0.1.1$ sudo apt-get install libwnck=2.16.1-0ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: libwnck paketi bulunam&#305;yor (can not find) 

anyway: if i would remove files which i installed with this command, would cause any problem?

> sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev libgnome2-dev libgnome-desktop-2 libgnome-desktop-dev

hehe so by which command i can remove these? apt-get remove?

---

### Post by reacocard on 2007-04-22
> **diskotek said:**
> hehe so by which command i can remove these? apt-get remove?

Yep. sudo apt-get remove will do it.

If you still want to give AWN a shot, the new thread here is much more detailed: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

---

### Post by diskotek on 2007-04-23
thank you for helping... i'll check the other instructions...

---

### Post by hihihi on 2007-04-27
hello!  
(ubuntu7.04)
It's like that: I got awn to work. and i can even drag a launch-icon into it, and it launches the program! gooood. BUT unfortunately i cannot configure anything useful, like described in the main-page of awn. so my preferences-window has no auto-hide and lots of other important stuff... this is what appears on the preferences-window: "general" "task appearance" "bar appearance" "glass engine" "pattern engine". 
i'm missing "window manager"....what is wrong? it seems not to be connected to gconf... but all the packages mentioned here are already installed... did i miss something?[/I][/I][/I][/I][/I]
i got it through svn and compiled myself. btw: nice thing.
thanks

---

### Post by reacocard on 2007-04-27
> **hihihi said:**
> hello!  
(ubuntu7.04)
It's like that: I got awn to work. and i can even drag a launch-icon into it, and it launches the program! gooood. BUT unfortunately i cannot configure anything useful, like described in the main-page of awn. so my preferences-window has no auto-hide and lots of other important stuff... this is what appears on the preferences-window: "general" "task appearance" "bar appearance" "glass engine" "pattern engine". 
i'm missing "window manager"....what is wrong? it seems not to be connected to gconf... but all the packages mentioned here are already installed... did i miss something?[/I][/I][/I][/I][/I]
i got it through svn and compiled myself.
thanks

All the extra settings can be found in gconf-editor, under apps -> avant-window-navigator.

---

### Post by XTREEM|RAGE on 2007-05-02
> **reacocard said:**
> Yep. sudo apt-get remove will do it.

If you still want to give AWN a shot, the new thread here is much more detailed: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

I'm very new to ubuntu, got it installed (not the svn version :( ). But it dont work the way i like, so i want to uninstall it. And this code should work?

sudo apt-get remove avant-window-navigator
or just
sudo apt-get remove

??? :)

plz help this ubuntu noobie out ;D :lolflag:

p.s. cant test it, because i'm at work ;)

---

### Post by reacocard on 2007-05-02
> **XTREEM|RAGE said:**
> I'm very new to ubuntu, got it installed (not the svn version :( ). But it dont work the way i like, so i want to uninstall it. And this code should work?

sudo apt-get remove avant-window-navigator
or just
sudo apt-get remove

??? :)

plz help this ubuntu noobie out ;D :lolflag:

p.s. cant test it, because i'm at work ;)

If you installed from my repo, then 'sudo apt-get remove avant-window-navigator' will work, if you installed form source, doing 'sudo make uninstall' from the source directory will work.

---

### Post by XTREEM|RAGE on 2007-05-02
i'm sorry to be such a noob but!!
i did this tutorial and not yours + i did the stable version not the svn version. But i want to do you tutorial + the svn version. And how do you mean from the source directory? In th tutorials it said i needed to ut it in the home directory and those files are extracted build etc all there not? do you mean from that folder(the extracted one)?

tnx :)

---

### Post by reacocard on 2007-05-02
> **XTREEM|RAGE said:**
> i'm sorry to be such a noob but!!
i did this tutorial and not yours + i did the stable version not the svn version. But i want to do you tutorial + the svn version. And how do you mean from the source directory? In th tutorials it said i needed to ut it in the home directory and those files are extracted build etc all there not? do you mean from that folder(the extracted one)?

tnx :)

Yep, that's the one. It should have a file called Makefile in it.

---

### Post by XTREEM|RAGE on 2007-05-03
tnx, gonna try yours! :D

---

### Post by jargoman on 2007-05-05
For those like me who are having problems with the first method and want to try the second or are having trouble just uninstalling

first go into the extracted source just as you did to compile it before
then 

$ ./configure
$ sudo make uninstall

make uninstall alone did not work for me and for a split second I was shocked!

---

### Post by jargoman on 2007-05-05
I can confirm that uninstalling option 1 and going with option 2 fixed the bug where the icons were   blocked by the glow. Also missing prefrences options are there. still no auto hide though

---

### Post by Trynemjoel on 2007-05-07
I just uninstalled the program after I followed option 1 and got the glow in front of the icon. I tryed option 2 because jargoman said it fixed that bug. It sadly did not and so I'm back to square one on that issue. Any other suggestions on how to solve this bug?

EDIT:
I got:
> Running intltoolize...

intltoolize: 'po/Makefile.in.in' is out of date: use '--force' to overwrite

during autogen.sh

---

### Post by reacocard on 2007-05-07
> **Trynemjoel said:**
> I just uninstalled the program after I followed option 1 and got the glow in front of the icon. I tryed option 2 because jargoman said it fixed that bug. It sadly did not and so I'm back to square one on that issue. Any other suggestions on how to solve this bug?

EDIT:
I got:

during autogen.sh

Could you please try again with my guide: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

This thread's guide is out-of-date. Post any more questions on the new thread.

---

### Post by ethanphoto on 2007-05-16
Hello I installed Avant and had to reinstall Ubuntu... I have once again installed Avant and it works seamlessly except i do not have the ability to drop new icons onto it... it has no icons on it as of yet so i assume that the left part of it (where your icons usually sit) has disappeared because its not used. im wondering how i can get icons on there other than it showing the open windows.


Thanks,

Ethan

---

### Post by jargoman on 2007-05-24
As far as my knowlge goes you can't put icon on avant. It displays only active windows.

I moved all the items form the bottom panel to the top and removed the bottom completely. there's still plenty of room for icons on the top panel.

---

### Post by tact on 2007-05-24
> **jargoman said:**
> As far as my knowlge goes you can't put icon on avant. It displays only active windows.

I moved all the items form the bottom panel to the top and removed the bottom completely. there's still plenty of room for icons on the top panel.

Sorry - Wrong.

You can drag and drop items from menus etc to AWN and use it as a launcher etc... as well as displaying open windows.

Its clever/cool too - eg. if you have your "Terminal" launcher there on AWN and click it...  it launches your command line terminal window.  As you would expect.  :)

It does NOT then place another icon on the right side showing it (twice)..  once as launcher and once as "open window".   (i.e. It is displayed only ONCE).  While the terminal window is open clicking it again does NOT launch a second terminal.  It just makes the already open terminal window visible again.   You CAN open a second (or third) terminal by CENTRE clicking on the terminal launcher icon

---

### Post by anandanbu on 2007-06-03
The problem that i face after successfully installing the avant-window Navigator is when i run it in the terminal i get the following error

phoenix@firebird:~$ avant-window-navigator

(avant-window-navigator:13611): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

(avant-window-navigator:13611): GdkPixbuf-CRITICAL **: gdk_pixbuf_composite: assertion `dest_x >= 0 && dest_x + dest_width <= dest->width' failed

---

### Post by Alex&amp;Linux on 2007-06-10
hmmm, I had used this before, but Ive just reinstalled with 64-bit feisty.
It was clearly stated that this was the best path to take if using 32-bit, any reason to suspect it shouldnt work with 64?
I

---

### Post by equinox_child on 2007-06-16
I tried to use the SVN method but when i try autogen, it runs for a while before saying:

```
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto dbus-glib-1) were not met:

No package 'dbus-glib-1' found
```

Does anyone know what I can do or what I should try?

I did the previous step of installing the other packages and that worked so i don't see why this should happen. Also, I tried to find dbus-glib-1 but i couldn't find it in the repos so i don't know what it is.

I also tried using the .deb package but after it installed I have no idea what to do...i tried to call avant-window-navigator from the terminal but it says it can't find such a command.

Any help would be really appreciated... i really want that dock :p
thanx

EDIT: I'm using Feisty with compiz btw, if that helps.

---

### Post by reacocard on 2007-06-16
> **equinox_child said:**
> I tried to use the SVN method but when i try autogen, it runs for a while before saying:

```
checking for AWN... configure: error: Package requirements ( glib-2.0 gobject-2.0 gtk+-2.0 gdk-2.0 libwnck-1.0 gnome-desktop-2.0 libgnome-2.0 gnome-vfs-2.0 gconf-2.0 x11 xproto dbus-glib-1) were not met:

No package 'dbus-glib-1' found
```

Does anyone know what I can do or what I should try?

I did the previous step of installing the other packages and that worked so i don't see why this should happen. Also, I tried to find dbus-glib-1 but i couldn't find it in the repos so i don't know what it is.

I also tried using the .deb package but after it installed I have no idea what to do...i tried to call avant-window-navigator from the terminal but it says it can't find such a command.

Any help would be really appreciated... i really want that dock :p
thanx

EDIT: I'm using Feisty with compiz btw, if that helps.

Please try again with the new guide, it's much more up-to-date and should fix your problem. Link: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

Mods, if anyone sees this, please close this thread, it's not updated anymore, only the new one is relevant anymore.

---

### Post by dannymichel on 2007-06-16
For some reason I can't drang ANYTHING on to it.
It's as if it's not there, but I can see it.
Any ideas?

---

### Post by chocbizkit on 2007-06-21
i get this error when i try to use ./autogen.sh

"shift: 364: can't shift that many"

what must i do?

---

### Post by a12ctic on 2007-06-28
I get a segmentation fault, any ideas?

---

### Post by FunnyLookinHat on 2007-06-28
[B]************************************************** ****************************
************************************************** ****************************
ATTENTION!! This post is no longer being updated, please see the following post instead:
[http://ubuntuforums.org/showthread.php?p=2307772](http://ubuntuforums.org/showthread.php?p=2307772)
************************************************** ****************************
************************************************** ****************************[/B]

---

