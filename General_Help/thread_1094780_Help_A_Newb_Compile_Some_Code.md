---
title: "Help A Newb Compile Some Code?"
date: 2009-03-12
forum: General Help
---

### Post by CCraw on 2009-03-12
Hello all

I'm hoping somebody would be kind enough to hold my hand and walk me through the process of compiling and installing a piece of software. It's a program called 'boomsim' and the code is available here: [http://www.hennigbuam.de/georg/boomerang_download.html](http://www.hennigbuam.de/georg/boomerang_download.html). Keeping in mind I really have no idea why I'm doing anything I'm doing, I tried getting it running using ./configure, make, make install. When I ran ./configure, it returned a message that said it seemed to work fine. Things went wrong at "make" and since I have no clue what I'm actually doing, I got stuck instantly. 

I'd like to start from scratch (unpacked archive in a directory) and walk through the process of (hopefully) getting this program running. If someone is willing to help a total linux newb I would really appreciate it. 

Thanks, 
Chris

---

### Post by Locutus_of_Borg on 2009-03-13
the source needs to be edited quite a bit to get it to compile on linux

try the windows executable in wine

---

### Post by Bapabooiee on 2009-03-13
Could you help clarify this by telling us what the error messages would be?

The usual process for compiling code is this:

You download the package, and check the website (or documentation) for any dependencies the code may need. For example, say you want to compile a game. The game may have a dependency on SDL--which, to put it simply, is a "library" that the code needs. It will not compile without it.

Run ./configure to, well, configure the build. Generally, that's all you have to do, but you can sometimes give it extra parameters. An example would be "./configure --use-opengl", which will configure the build to... well (isn't it obvious) enable support for OpenGL. It also does misc. care-taking.

Run "make", which is a program that reads-in "Makefiles". A simple way to think of Makefiles is a file that contains the commands used to compile the source code for you. Without it, you'd have to compile every source file manually, and create the executables manually as well - which would be a pain.

Anyway, the make file then uses the Makefiles to compile all the source code files (which is also affected by any configurations you did with the configure script), and build an executable for you.

What "make install" does is specify to make "ok. The source is all compiled. Copy the executable(s) and other files to the appropriate directory".

--

Sometimes, though, trying to compile source code can sometimes just plain-out be impossible... too many things could go wrong.. and the code just won't wanna compile for whatever reason (which is where most people give up). So it may be a good idea to look for some other source code to compile, and see if that changes anything.

Most of the time, it's a really simply process, though. Just make sure you have met all the program's dependencies. Configure. Compile. Install. That's it.

I'd recommend possible checking-out some other source code to eliminate the chance of there just being something horribly wrong with the process - because this can be very daunting to someone who is new. And since the config script doesn't complain about anything, there's probably something else wrong - which isn't worth going after for these purposes.

Let's see if we can find you some nice source code that's easier to compile =]

---

### Post by ju2wheels on 2009-03-13
```

sudo apt-get install gcc make build-essential libwxgtk2.8-0 libwxgtk2.8-dev glutg3 libglut3 libglut3-dev glutg3-dev
wget "http://www.cip.physik.uni-muenchen.de/~georg.hennig/downloads/2003-06-14wxBumms-src.tar.gz"
tar xvfz 2003-06-14wxBumms-src.tar.gz
cd wxBumms-14-06-2003/
mv Makefile.unx MakeFile
make

```

Theres an error in the code in file GLWidget.h on line 40 so it doesnt compile for me (which is not related to missing libraries so its an actual error in the way the author wrote the code).

---

### Post by CCraw on 2009-03-13
Thank you all for the info so far. So right now, my understanding is that it needs to be heavily modified to compile under Linux (I thought it was ok under Linux, but I may have missed something) and that there's an error in the code that prevents it from compiling anyway. Good way to start. :D 

I did try the windows version with wine, but no luck. Screen flickers and nothing ever starts. Quite possibly my fault, but not sure. 

Just in case, here's what happens for me when I try to compile it:

I've just downloaded and unpacked boomsim-0.0_2005-10-16.tar.gz into a directory in my home folder called *boomsim-0.0_2005-10-16*.

I've opened a terminal window and I'm sitting in the *boomsim...* directory.

```
 ./configure

checking whether to enable debugging... no
checking whether to enable check for canonical system... checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
=========================================
Setting up build environment for Linux...
=========================================
checking for rm... /bin/rm
checking for del... (cached) /bin/rm
checking for rmdir... /bin/rmdir
checking for deltree... (cached) /bin/rmdir
checking for make... /usr/bin/make
configure: cleaning previous installation
checking whether build environment is sane... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for ranlib... ranlib
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for Qt... no
checking for the pthreads library -lpthreads... no
checking whether pthreads work without any flags... no
checking whether pthreads work with -Kthread... no
checking whether pthreads work with -kthread... no
checking for the pthreads library -llthread... no
checking whether pthreads work with -pthread... yes
checking for joinable pthread attribute... PTHREAD_CREATE_JOINABLE
checking if more special flags are required for pthreads... no
checking for cc_r... gcc
checking whether to enable opengl (recommended)... yes
checking whether to prefer glut to glx/win32-opengl if available... no
checking for egrep... grep -E
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
checking whether we are using the Microsoft C compiler... no
checking windows.h usability... no
checking windows.h presence... no
checking for windows.h... no
checking for OpenGL library... no
checking for OpenGL Utility library... no
WARNING: No opengl implementation found. You won't be able to plot boomsim results directly.
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
configure: creating ./config.status
config.status: creating Makefile


**************************************************
* Configure seems to have finished successfully...
* Using the following settings:
*
* Binaries directory: "/usr/local/bin"
* Data directory:     "/usr/local/share/boomsim"
*
* Using QT:
*     QT_CXXFLAGS=
*     QT_DIR=
*     QT_LIBS=
*     QT_UIC=
*     QT_MOC=
*
* Using GLX OpenGL window.
*
* AR=ar
* CXX=g++
* CXXFLAGS= -O3 -ffast-math -s -pthread   -D__QT__ -D__USE_PTHREAD__ -D__WORKING_DIR__="\"/usr/local/share/boomsim\"" -I. -Ilib
* LIBS=
* OPENGL_LIBS=
*
* Run "make" to compile and "make install" (as root) to
*   install boomsim.
**************************************************

```

I've just noticed that it says "checking for xxx... no" numerous times. I assume that this isn't helping the situation. Not sure how I missed that the first time. Anyway...

```
 make

g++ -c lib/motion/boomsim_motion.cpp -o lib/motion/boomsim_motion.o -O3 -ffast-math -s -pthread   -D__QT__ -D__USE_PTHREAD__ -D__WORKING_DIR__="\"/usr/local/share/boomsim\"" -I. -Ilib 
g++ -c lib/motion/forces_and_torques.cpp -o lib/motion/forces_and_torques.o -O3 -ffast-math -s -pthread   -D__QT__ -D__USE_PTHREAD__ -D__WORKING_DIR__="\"/usr/local/share/boomsim\"" -I. -Ilib 
lib/motion/forces_and_torques.cpp: In member function ‘bool forces_and_torques::read(std::string, std::string&, std::string&, std::string&, std::string&, double&, double&, double&)’:
lib/motion/forces_and_torques.cpp:97: error: ‘strtod’ was not declared in this scope
lib/motion/forces_and_torques.cpp:111: error: ‘strtod’ was not declared in this scope
lib/motion/forces_and_torques.cpp:125: error: ‘strtod’ was not declared in this scope
lib/motion/forces_and_torques.cpp:139: error: ‘strtod’ was not declared in this scope
lib/motion/forces_and_torques.cpp:153: error: ‘strtod’ was not declared in this scope
lib/motion/forces_and_torques.cpp:167: error: ‘strtod’ was not declared in this scope
lib/motion/forces_and_torques.cpp:209: error: ‘atoi’ was not declared in this scope
lib/motion/forces_and_torques.cpp:217: error: ‘atoi’ was not declared in this scope
lib/motion/forces_and_torques.cpp:225: error: ‘atoi’ was not declared in this scope
make: *** [lib/motion/forces_and_torques.o] Error 1

```

So that's where it stands right now. Am I totally out of luck? Whatever the outcome, I do appreciate the help. I'm learning something regardless.

-Chris

---

### Post by ju2wheels on 2009-03-13
Looks like you dont have the standard C libraries included to me.

```

wget "http://www.cip.physik.uni-muenchen.de/~georg.hennig/downloads/boomsim-0.0_2005-10-16.tar.gz"
tar xvfz boomsim-0.0_2005-10-16.tar.gz
cd boomsim-0.0_2005-10-16/
./configure

```

Edit file lib/motion/forces_and_torques.cpp, add #include <cstdlib> to the top and replace all occurrences of strtod and atoi with std::strtod and std::atoi.
Edit file lib/aerodynamics/import_obj_io.cpp and do the same as above.
Edit file ui/motion/glut_motion_window.cpp add #include <cstring> to the top and replace all occurrences of strlen with std::strlen.

```

make
sudo make install

```

Compiles perfectly for me (although I did not install or test run).

---

### Post by ju2wheels on 2009-03-13
Corrected my above post with proper instructions for compiling.

---

### Post by CCraw on 2009-03-13
Wow! Thanks for taking all the effort to try to track down the problems I'm having. 

I carefully went through the steps you provided and I'm pretty confident I didn't miss anything. Still no luck, unfortunately. The fact that someone else *can* compile it gives me some hope.

```
 make
g++ -c lib/motion/boomsim_motion.cpp -o lib/motion/boomsim_motion.o -O3 -ffast-math -s -pthread   -D__QT__ -D__USE_PTHREAD__ -D__WORKING_DIR__="\"/usr/local/share/boomsim\"" -I. -Ilib 
g++ -c lib/motion/forces_and_torques.cpp -o lib/motion/forces_and_torques.o -O3 -ffast-math -s -pthread   -D__QT__ -D__USE_PTHREAD__ -D__WORKING_DIR__="\"/usr/local/share/boomsim\"" -I. -Ilib 
g++ -c lib/motion/integration.cpp -o lib/motion/integration.o -O3 -ffast-math -s -pthread   -D__QT__ -D__USE_PTHREAD__ -D__WORKING_DIR__="\"/usr/local/share/boomsim\"" -I. -Ilib 
g++ -c lib/reporter.cpp -o lib/reporter.o -O3 -ffast-math -s -pthread   -D__QT__ -D__USE_PTHREAD__ -D__WORKING_DIR__="\"/usr/local/share/boomsim\"" -I. -Ilib 
g++ -c ui/qt_reporter.cpp -o ui/qt_reporter.o -O3 -ffast-math -s -pthread   -D__QT__ -D__USE_PTHREAD__ -D__WORKING_DIR__="\"/usr/local/share/boomsim\"" -I. -Ilib 
ui/qt_reporter.cpp:34:23: error: qdatetime.h: No such file or directory
ui/qt_reporter.cpp:35:19: error: qfile.h: No such file or directory
ui/qt_reporter.cpp:36:20: error: qlabel.h: No such file or directory
ui/qt_reporter.cpp:37:25: error: qmessagebox.h: No such file or directory
ui/qt_reporter.cpp:38:26: error: qprogressbar.h: No such file or directory
ui/qt_reporter.cpp:39:23: error: qtextedit.h: No such file or directory
ui/qt_reporter.cpp: In member function ‘void qt_reporter::log(std::string)’:
ui/qt_reporter.cpp:67: error: invalid use of incomplete type ‘struct QTextEdit’
ui/qt_reporter.h:37: error: forward declaration of ‘struct QTextEdit’
ui/qt_reporter.cpp:67: error: ‘QDateTime’ has not been declared
ui/qt_reporter.cpp:71: error: ‘QTextStream’ was not declared in this scope
ui/qt_reporter.cpp:71: error: expected `;' before ‘log_stream’
ui/qt_reporter.cpp:72: error: ‘log_stream’ was not declared in this scope
ui/qt_reporter.cpp:72: error: ‘QDateTime’ has not been declared
ui/qt_reporter.cpp:72: error: ‘endl’ was not declared in this scope
ui/qt_reporter.cpp:73: error: invalid use of incomplete type ‘struct QFile’
ui/qt_reporter.h:35: error: forward declaration of ‘struct QFile’
ui/qt_reporter.cpp: In member function ‘void qt_reporter::inform(std::string)’:
ui/qt_reporter.cpp:87: error: ‘QMessageBox’ has not been declared
ui/qt_reporter.cpp: In member function ‘void qt_reporter::warn(std::string)’:
ui/qt_reporter.cpp:93: error: ‘QMessageBox’ has not been declared
ui/qt_reporter.cpp: In member function ‘void qt_reporter::error(std::string)’:
ui/qt_reporter.cpp:99: error: ‘QMessageBox’ has not been declared
ui/qt_reporter.cpp: In member function ‘void qt_reporter::run(std::string)’:
ui/qt_reporter.cpp:106: error: invalid use of incomplete type ‘struct QProgressBar’
ui/qt_reporter.h:38: error: forward declaration of ‘struct QProgressBar’
ui/qt_reporter.cpp:107: error: invalid use of incomplete type ‘struct QLabel’
ui/qt_reporter.h:36: error: forward declaration of ‘struct QLabel’
ui/qt_reporter.cpp: In member function ‘void qt_reporter::done(std::string)’:
ui/qt_reporter.cpp:114: error: invalid use of incomplete type ‘struct QLabel’
ui/qt_reporter.h:36: error: forward declaration of ‘struct QLabel’
ui/qt_reporter.cpp:115: error: invalid use of incomplete type ‘struct QProgressBar’
ui/qt_reporter.h:38: error: forward declaration of ‘struct QProgressBar’
ui/qt_reporter.cpp: In member function ‘void qt_reporter::percent(short unsigned int)’:
ui/qt_reporter.cpp:126: error: invalid use of incomplete type ‘struct QProgressBar’
ui/qt_reporter.h:38: error: forward declaration of ‘struct QProgressBar’
ui/qt_reporter.cpp:127: error: invalid use of incomplete type ‘struct QProgressBar’
ui/qt_reporter.h:38: error: forward declaration of ‘struct QProgressBar’
ui/qt_reporter.cpp: In member function ‘void qt_reporter::del()’:
ui/qt_reporter.cpp:133: error: invalid use of incomplete type ‘struct QFile’
ui/qt_reporter.h:35: error: forward declaration of ‘struct QFile’
ui/qt_reporter.cpp:134: error: incomplete type ‘QFile’ used in nested name specifier
ui/qt_reporter.cpp:134: error: invalid use of incomplete type ‘struct QFile’
ui/qt_reporter.h:35: error: forward declaration of ‘struct QFile’
ui/qt_reporter.cpp:135: warning: possible problem detected in invocation of delete operator:
ui/qt_reporter.cpp:135: warning: invalid use of incomplete type ‘struct QFile’
ui/qt_reporter.h:35: warning: forward declaration of ‘struct QFile’
ui/qt_reporter.cpp:135: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
ui/qt_reporter.cpp: In member function ‘void qt_reporter::setFile(QFile*)’:
ui/qt_reporter.cpp:148: warning: possible problem detected in invocation of delete operator:
ui/qt_reporter.cpp:148: warning: invalid use of incomplete type ‘struct QFile’
ui/qt_reporter.h:35: warning: forward declaration of ‘struct QFile’
ui/qt_reporter.cpp:148: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
ui/qt_reporter.cpp: In member function ‘void qt_reporter::setLabel(QLabel*)’:
ui/qt_reporter.cpp:159: warning: possible problem detected in invocation of delete operator:
ui/qt_reporter.cpp:159: warning: invalid use of incomplete type ‘struct QLabel’
ui/qt_reporter.h:36: warning: forward declaration of ‘struct QLabel’
ui/qt_reporter.cpp:159: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
ui/qt_reporter.cpp: In member function ‘void qt_reporter::setTextEdit(QTextEdit*)’:
ui/qt_reporter.cpp:170: warning: possible problem detected in invocation of delete operator:
ui/qt_reporter.cpp:170: warning: invalid use of incomplete type ‘struct QTextEdit’
ui/qt_reporter.h:37: warning: forward declaration of ‘struct QTextEdit’
ui/qt_reporter.cpp:170: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
ui/qt_reporter.cpp: In member function ‘void qt_reporter::setProgressBar(QProgressBar*)’:
ui/qt_reporter.cpp:181: warning: possible problem detected in invocation of delete operator:
ui/qt_reporter.cpp:181: warning: invalid use of incomplete type ‘struct QProgressBar’
ui/qt_reporter.h:38: warning: forward declaration of ‘struct QProgressBar’
ui/qt_reporter.cpp:181: note: neither the destructor nor the class-specific operator delete will be called, even if they are declared when the class is defined.
make: *** [ui/qt_reporter.o] Error 1

```

Am I missing a bunch of necessary libraries perhaps? I'm not sure how to decipher this flood of errors.

-Chris

---

### Post by ju2wheels on 2009-03-13
You are missing some QT libraries.

I installed a couple so I dont know which ones did the trick but try the following:

```

sudo apt-get install libqtgui4 qt4-dev-tools libqt4-dev libqt4-gui libqtuitools2.2-cil

```

Hopefully one of those should do the trick.

---

### Post by CCraw on 2009-03-16
Hello

Sorry about the delay in replying. 
I tried the above commands and got the following output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqtgui4 is already the newest version.
libqtgui4 set to manually installed.
libqt4-dev is already the newest version.
libqt4-gui is already the newest version.
libqt4-gui set to manually installed.
E: Couldn't find package libqtuitools2.2-cil

```

So it looked like I had everything except, possibly, libqtuitools. I did a quick search and it looked like libqtuitools is part of the kdebindings package, so I installed that as well (am I wrong?).

Anyway, I ran ./configure, went through the editing process with the 3 boomsim files, and ended up with the same list of errors as before from the make command. Bummer. Upside is that I had a reason to try the diff command to compare my error lists. ;)

Totally fair call it if you want to bail on this problem, but I've sure appreciated the patience and help so far.

Thanks,
-Chris

---

### Post by ju2wheels on 2009-03-16
I honestly dont know which package had the right libs but I just installed a load of qt packages that I though were relevant and it ended up working. These are what I have installed:

```

libqt3-compat-headers libqt3-headers libqt3-mt libqt3-mt-dev libqt4-core libqt4-dbus libqt4-designer libqt4-dev libqt4-gui libqt4-network libqt4-opengl libqt4-opengl-dev libqt4-qt3support libqt4-script libqt4-webkit libqtcore4 libqtgui4 libqtuitools2.2-cil qt3-dev-tools qt3-assistant qt4-designer qt4-dev-tools 

```

---

### Post by CCraw on 2009-03-17
Yes! Success! That list of libs is just what I needed. I went through the it and found I was missing a single library. Apparently it was the magic one. I haven't got the graphical side of the motion simulation software working yet, but piping the output to gnuplot works beautifully so it's not too important.

Thanks so much for all the help!

-Chris

---

