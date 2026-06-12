---
title: "Problem compiling QtiPlot 0.9.8 with xls import"
date: 2010-07-01
forum: Education &amp; Science
---

### Post by bailli on 2010-07-01
Hi everybody,
I am having problems compiling the latest release of QtiPlot with .xls import.
Starting from v0.9.8 the library ExcelFormat ([http://www.codeproject.com/KB/office/ExcelFormat.aspx](http://www.codeproject.com/KB/office/ExcelFormat.aspx)) is used instead of libxls.

Since I solved (more or less cleanly) I want to give a quick outline how to compile QtiPlot 0.9.8:

You need the following packages (if I remember correctly):
```
sudo apt-get install build-essential g++ libboost-all-dev libpng12-dev libqt4-dev libgsl0-dev python2.6-dev python-qt4-dev python-sip4-dev
```
Additionally QtiPlot depends on muParser. The version in the Lucid Repos is too old so you have to compile the library yourself. Get the v1.32 source from [http://muparser.sourceforge.net/](http://muparser.sourceforge.net/). If you want ODF and XLS import you need the QuaZIP library from [http://quazip.sourceforge.net/](http://quazip.sourceforge.net/) (v0.2.3) and the ExcelFormat library from [http://www.codeproject.com/KB/office/ExcelFormat.aspx](http://www.codeproject.com/KB/office/ExcelFormat.aspx) or better from SVN [http://shell.franken.de/svn/sky/excel/trunk/ExcelFormat/](http://shell.franken.de/svn/sky/excel/trunk/ExcelFormat/) (only BasicExcel.hpp/.cpp and ExcelFormat.cpp/.h are needed)

Open a console, navigate to your usual compile directory and do the following:
```
tar xvjf /home/yourhome/Downloads/qtiplot-0.9.8.tar.bz2
cd qtiplot-0.9.8/3rdparty

tar xvzf /home/yourhome/Downloads/muparser_v132.tar.gz
cd muparser_v132
./configure
make
sudo make install
sudo ldconfig
cd ..
```

If you want ODF import:
```
tar xvzf quazip-0.2.3.tar.gz
cd quazip.0.2.3/quazip
qmake PREFIX=/usr
make
sudo make install
cd ..
```

You have some more work getting xls import going. 

If you are running an **amd64** system you should give my attached edited version of ExcelFormat library a try because I got segfaults using the original version. Just extract the contents:
```
tar xvzf ExcelFormat.tar.gz
```

If you have **x86** system, put the 4 files from SVN (BasicExcel.cpp/.hpp and ExcelFormat.cpp/.h) together with the attached (very basic) Makefile in a directory (i.e. 3rdparty/ExcelFormat).
Add these 3 lines to BasicExcel.hpp after line 110 (#include <string> //MF)
```
#ifdef __GNUC__
#include <string.h>
#endif
```

**amd64 and x86**:
```
cd ExcelFormat
make
sudo make install
cd ..
```

Okay now we have almost everything set up. You only need a build.conf in your qtiplot-0.9.8 directory:
```
isEmpty( QTI_ROOT ) {
  message( "each file including this config needs to set QTI_ROOT to the dir containing this file!" )
}

SYS_INCLUDEPATH = /opt/local/include
SYS_LIBS = -L/opt/local/lib

# muParser lib
MUPARSER_INCLUDEPATH = 
MUPARSER_LIBS = -lmuparser

# GSL lib
GSL_INCLUDEPATH =
GSL_LIBS = -lgsl -lgslcblas

# Boost lib
BOOST_INCLUDEPATH =
BOOST_LIBS = -lboost_date_time-mt -lboost_thread-mt


# QWT
QWT_INCLUDEPATH = $$QTI_ROOT/3rdparty/qwt/src
QWT_LIBS = $$QTI_ROOT/3rdparty/qwt/lib/libqwt.a

# QwtPlot3D
QWT3D_INCLUDEPATH = $$QTI_ROOT/3rdparty/qwtplot3d/include
QWT3D_LIBS = $$QTI_ROOT/3rdparty/qwtplot3d/lib/libqwtplot3d.a

# ExcelFormat - optional
# comment the next 2 lines to disable xls import
XLS_INCLUDEPATH =
XLS_LIBS = -lExcelFormat

# QuaZIP - optional
# comment the next 2 lines to disable xls import
QUAZIP_INCLUDEPATH =
QUAZIP_LIBS = -lquazip

# libpng
LIBPNG_INCLUDEPATH =
LIBPNG_LIBS = -lpng

PYTHON = python

# Qt tools - allows to use specific versions
LUPDATE = lupdate
LRELEASE = lrelease

#  Target specific configuration: configure Qtiplot itself
contains( TARGET, qtiplot ) {
  # building without muParser doesn't work yet
  SCRIPTING_LANGS += muParser
  SCRIPTING_LANGS += Python

  # a console displaying output of scripts; particularly useful on Windows
  # where running QtiPlot from a terminal is inconvenient
  DEFINES         += SCRIPTING_CONSOLE

  #DEFINES         += QTIPLOT_DEMO

  # Comment the following lines to disable donations start-up message.
  #DEFINES         += QTIPLOT_SUPPORT

  # Uncomment the following line if you want to perform a custom installation using the *.path variables defined in ./qtiplot.pro.
  #CONFIG          += CustomInstall

  # Uncomment the following line if you want to build QtiPlot as a browser plugin (not working on Internet Explorer).
  #CONFIG          += BrowserPlugin
  
  CONFIG          += release
  #CONFIG          += debug
}

```
and you need to edit qtiplot-0.9.8/src/core/ApplicationWindow.cpp to:
```
line  199: #include <quazip/quazip.h>
line  200: #include <quazip/quazipfile.h>

line 4221: if (!rows && !cols){
```

Finally the last commands (in the qtiplot-0.9.8 directory):
```
qmake
make
sudo make install
```
For me, the install command only installs the qtiplot plugins - I just started qtiplot directly from the qtiplot subdir - but I think you could also copy the executable to /usr/bin or somethin similiar.

---

### Post by bailli on 2010-07-09
Found a (ugly) solution myself.
I updated the first post to quick guide to compile QtiPlot. Maybe a mod could change the thread title?

---

### Post by barmaley on 2010-07-13
Thank you for the post.
I followed your instructions step by step, and still I have errors during the last compilation.
Here is the output: :~/soft/qtiplot-0.9.8$ make
cd fitPlugins/ && make -f Makefile 
make[1]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins'
cd explin/ && make -f Makefile 
make[2]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins/explin'
/usr/bin/qmake -unix -o Makefile explin.pro
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/explin'
make[2]: Entering directory `/../soft/qtiplot-0.9.8/fitPlugins/explin'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/explin'
cd exp_saturation/ && make -f Makefile 
make[2]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins/exp_saturation'
/usr/bin/qmake -unix -o Makefile exp_saturation.pro
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/exp_saturation'
make[2]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins/exp_saturation'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/exp_saturation'
cd fitRational0/ && make -f Makefile 
make[2]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins/fitRational0'
/usr/bin/qmake -unix -o Makefile fitRational0.pro
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/fitRational0'
make[2]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins/fitRational0'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/fitRational0'
cd fitRational1/ && make -f Makefile 
make[2]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins/fitRational1'
/usr/bin/qmake -unix -o Makefile fitRational1.pro
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/fitRational1'
make[2]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins/fitRational1'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/fitRational1'
cd planck_wavelength/ && make -f Makefile 
make[2]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins/planck_wavelength'
/usr/bin/qmake -unix -o Makefile planck_wavelength.pro
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/planck_wavelength'
make[2]: Entering directory `../soft/qtiplot-0.9.8/fitPlugins/planck_wavelength'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins/planck_wavelength'
make[1]: Leaving directory `../soft/qtiplot-0.9.8/fitPlugins'
cd manual/ && make -f Makefile 
make[1]: Entering directory `../soft/qtiplot-0.9.8/manual'
docbook2html -d qtiplot.dsl docbook-en/index.docbook -e no-valid
make[1]: docbook2html: Command not found
make[1]: *** [web] Error 127
make[1]: Leaving directory `../soft/qtiplot-0.9.8/manual'
make: *** [sub-manual-make_default] Error 2

I don't understand the reason for these errors.
Could you, please, help me in compiling qtiplot?
Thanks a lot.

---

### Post by bailli on 2010-07-14
Hi,

your problem seems to be connected to the generation of the pdf manual. The docbook2html executable is not found.

You could either try installing docbook2html:
```
sudo apt-get install docbook-utils
```
but I am not sure if that installs all necessary files (you might need to install other docbook packages).

or you could exclude the pdf building process of the manual from the make files by remove the "manual \" line from qtiplot.pro in the qtiplot-0.9.8 directory. (You might have to run "qmake" again.)

Hope that helps. :)

---

### Post by barmaley on 2010-07-14
Thanks a lot. It worked, I don't understand how you figured it out, but this problem was solved. Thank you.
The compilation ran for some time, but now I have another error. Here it is:

/usr/bin/ld: cannot find -lboost_date_time-mt
collect2: ld returned 1 exit status
make[1]: *** [qtiplot] Error 1
make[1]: Leaving directory `../soft/qtiplot-0.9.8/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2

I hope it is enough to define the source of the problem.
I really appreciate your help.

---

### Post by bailli on 2010-07-14
This seems to be an error on my side:

I should have installed the package libboost-all-dev instead of libboost.

So just type
```
sudo apt-get install libboost-all-dev
```

Then run make again.

---

### Post by barmaley on 2010-07-14
Thank you. It worked. make finished without errors.
It seems I'm almost there. I ran sudo make install, but there was something wrong with manual/:

make[1]: Entering directory `../soft/qtiplot-0.9.8/manual'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `../soft/qtiplot-0.9.8/manual'
make: *** [sub-manual-install_subtargets] Error 2

Any suggestions?

---

### Post by bailli on 2010-07-14
Did you run qmake again in the qtiplot-0.9.8 directory?

---

### Post by barmaley on 2010-07-14
Yes, I run 'qmake' - silence.
'make' produces this out put (it is only the end of it):

Output written in /tmp/tmpqybUdP/index.docbook.ind.
Transcript written in /tmp/tmpqybUdP/index.docbook.ilg.
This is pdfTeX, Version 3.1415926-1.40.10 (TeX Live 2009/Debian)
 restricted \write18 enabled.
entering extended mode
'qtiplot-manual-en.pdf' successfully built
make[1]: Leaving directory `../soft/qtiplot-0.9.8/manual'
cd 3rdparty/qwt/ && make -f Makefile 
make[1]: Entering directory `../soft/qtiplot-0.9.8/3rdparty/qwt'
cd src/ && make -f Makefile 
make[2]: Entering directory `../soft/qtiplot-0.9.8/3rdparty/qwt/src'
make[2]: Nothing to be done for `first'.
make[2]: Leaving directory `../soft/qtiplot-0.9.8/3rdparty/qwt/src'
make[1]: Leaving directory `../soft/qtiplot-0.9.8/3rdparty/qwt'
cd 3rdparty/qwtplot3d/ && make -f Makefile 
make[1]: Entering directory `../soft/qtiplot-0.9.8/3rdparty/qwtplot3d'
make[1]: Nothing to be done for `first'.
make[1]: Leaving directory `../soft/qtiplot-0.9.8/3rdparty/qwtplot3d'
cd qtiplot/ && make -f Makefile 
make[1]: Entering directory `../soft/qtiplot-0.9.8/qtiplot'
make[1]: Nothing to be done for `first'.
make[1]: Leaving directory `../soft/qtiplot-0.9.8/qtiplot'

I see no error, but may be you can find the problem.
Then I run 'sudo make install' and it gives errors, that I posted above.

---

### Post by bailli on 2010-07-15
Hm okay I just made a test myself. If you leave the "manual \" line in qtiplot.pro Make runs into an error in the manual directory because the Makefile there doens't have an install target. I would suggest you just remove the "manual \" line and rerun qmake and sudo make install.

I didn't run into this problem because I have that line removed myself. Building the manual always takes so much time which annoyed me while trying to get qtiplot to compile...

---

### Post by barmaley on 2010-07-15
Thank you. I removed 'manual /' line in the qtiplot.pro and everything went flawlessly. Sorry for wasting your time, I appreciate your help very much.
Just a small question, is it fully functional this way? If I understood what I've done, the program now solely doesn't have a manual, but the rest of the program was compiled as it should have?
Thanks a lot.

---

### Post by bailli on 2010-07-20
Yes the programm should be fully functional without the manual.
The help menu inside QtiPlot let's you select a help folder. If you supply the qtiplot-0.9.8/manual/html folder the help is displayed correctly.

---

### Post by barmaley on 2010-08-04
Hi, it's me again.

I was trying to compile qtiplot at home, but again I met a problem, which I don't know how to solve. Here is the output of 'make':

/opt/local/lib -lQtAssistantClient -lpthread -lGLU -lGL -lQtSvg -lQt3Support -lQtXml -lQtOpenGL -lQtGui -lQtNetwork -lQtCore 
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[1]: *** [qtiplot] Error 1
make[1]: Leaving directory `/home/casper/qtiplot/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2

Something related to GL, but what exactly? Could you, please, help me?
Thanks a lot.

---

### Post by barmaley on 2010-08-04
I found a solution here
[http://forums.nvidia.com/index.php?showtopic=171590](http://forums.nvidia.com/index.php?showtopic=171590).
Here it is if you are curious:

Solution for cannot find -lGL: There is a broken link for libGL.so, replace it.

sudo rm /usr/lib/libGL.so; sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so

Thanks anyway.

---

### Post by ls8 on 2010-09-29
See post #33 for latest information.

---

### Post by bailli on 2010-10-10
Thanks for the compile script and the compiled win32 binary.
For some reason I have been unable to build a fully featured win32 version with python support that works without a system wide installed python engine.

Just two remarks about the linux compile script. The ExeclImport lib is still not fixed for amd64 architecture. And the script will most likely not work with QtiPlot 0.9.8.3 which is I expect to be released tomorrow. I have regularly checked the svn commits and most 3rdparty libs have been removed from the official svn and resulting in even more dependencies you have to look after...

---

### Post by barmaley on 2010-10-12
Hi, people
I tried to compile qtiplot-0.9.8.3 in a new Ubuntu 10.10 and I failed, of course.
qmake was silent.
Here is the output of make:
In file included from src/plot2D/MultiLayer.h:33,
                 from src/core/ApplicationWindow.h:43,
                 from src/analysis/Filter.h:34,
                 from src/analysis/Convolution.h:32,
                 from src/analysis/Convolution.cpp:29:
src/plot2D/FrameWidget.h:34: fatal error: qwt_plot.h: No such file or directory
compilation terminated.
make[1]: *** [../tmp/qtiplot/Convolution.o] Error 1
make[1]: Leaving directory `/qtiplot-0.9.8.3/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2

If you have a solution to this problem, please, post it here.
Thanks

---

### Post by niscima on 2010-10-12
I successfully compiled qtiplot-0.9.8.3 in Kubuntu 10.10 64bit.
I am not an expert in c++ and I had to comment out 793 in file
qtiplot-0.9.8.3/qtiplot/src/origin/importOPJ.cpp, in order to get Origin import working.
/* case Origin::GraphCurve::XYZContour: */
I did not include EmfEngine and ALGLIB.
I added liborigin2 and QTeXengine to 3rdparty directory.
If I will be able to reconstruct all the steps (after many runs full of errors) I will post
the procedure.

---

### Post by niscima on 2010-10-13
Here are the steps to compile qtiplot-0.9.8.3 in Ubuntu 10.10 64bit.

1. Install packages as in message #1. Install package libqtassistantclient-dev
   (see .
2. Install muparser (see #1).
3. Install quazip (see #1).
4. Install ExcelFormat (see #1)
5. Edit qtiplot/src/core/ApplicationWindow.cpp to:
   line  199: #include <quazip/quazip.h>
   line  200: #include <quazip/quazipfile.h>
   line 4329: if (!rows && !cols){
6. Remove "manual \" line in qtiplot.pro
7. Download QTeXEngine-0.2-opensource.zip from Qtiplot website and put in
   3dparty/QTeXEngine. qmake and make in this directory.
8. Download liborigin2-13092010.zip rom Qtiplot website and put in
   3dparty/liborigin2. See its README. Download tree-2.65.tar.gz.tgz
   and put tree.h in liborigin2 directory. Download loglite-0.4.0.zip
   and put logging.hpp in liborigin2/loglite directory.
   qmake and make in liborigin2 directory.
   In liborigin2/tmp:
   ar rvs liborigin2.a *.o
   Copy liborigin2.a in liborigin2 directory.
9. Replace all "liborigin2" in qtiplot/src/origin/origin.pri with "liborigin2"
10. Comment out line 793 in file qtiplot/src/origin/importOPJ.cpp
   /* case Origin::GraphCurve::XYZContour: */.
11. Use the following build.conf:

Begins
isEmpty( QTI_ROOT ) {
  message( "each file including this config needs to set QTI_ROOT to the dir containing this file!" )
}

##########################################################
##     System specific configuration
##########################################################

# Global include path which is always added at the end of the INCLUDEPATH
SYS_INCLUDEPATH = /opt/local/include
# Global lib path and libs which is ls always added at the end of LIBS
SYS_LIBS = -L/opt/local/lib

##########################################################
## zlib ([http://www.zlib.net/](http://www.zlib.net/))
##########################################################

# include path. leave it blank to use SYS_INCLUDE
ZLIB_INCLUDEPATH = $$QTI_ROOT/3rdparty/zlib/

# muParser lib
MUPARSER_INCLUDEPATH = 
MUPARSER_LIBS = -lmuparser

# GSL lib
GSL_INCLUDEPATH =
GSL_LIBS = -lgsl -lgslcblas

# Boost lib
BOOST_INCLUDEPATH =
BOOST_LIBS = -lboost_date_time-mt -lboost_thread-mt

# QWT
QWT_INCLUDEPATH = $$QTI_ROOT/3rdparty/qwt/src
QWT_LIBS = $$QTI_ROOT/3rdparty/qwt/lib/libqwt.a

# QwtPlot3D
QWT3D_INCLUDEPATH = $$QTI_ROOT/3rdparty/qwtplot3d/include
QWT3D_LIBS = $$QTI_ROOT/3rdparty/qwtplot3d/lib/libqwtplot3d.a

##########################################################
## liborigin2 - optional. you don't have to set these variables
# [http://soft.proindependent.com/liborigin2/](http://soft.proindependent.com/liborigin2/)
##########################################################

# include path. leave it blank to use SYS_INCLUDE
LIBORIGIN_INCLUDEPATH = $$QTI_ROOT/3rdparty/liborigin2
# link statically against a copy in 3rdparty/
LIBORIGIN_LIBS = $$QTI_ROOT/3rdparty/liborigin2/liborigin2.a

# ExcelFormat - optional
# comment the next 2 lines to disable xls import
XLS_INCLUDEPATH =
XLS_LIBS = -lExcelFormat

# QuaZIP - optional
# comment the next 2 lines to disable xls import
QUAZIP_INCLUDEPATH =
QUAZIP_LIBS = -lquazip

# libpng
LIBPNG_INCLUDEPATH =
LIBPNG_LIBS = -lpng

PYTHON = python

##########################################################
## EmfEngine - optional. you don't have to set these variables
# [http://soft.proindependent.com/emf/index.html](http://soft.proindependent.com/emf/index.html)
##########################################################

# include path.
#EMF_ENGINE_INCLUDEPATH = $$QTI_ROOT/3rdparty/EmfEngine/src
# link locally against a copy in 3rdparty/
#EMF_ENGINE_LIBS = $$QTI_ROOT/3rdparty/EmfEngine/libEmfEngine.a

##########################################################
## QTeXEngine - optional. you don't have to set these variables
# [http://soft.proindependent.com/qtexengine/](http://soft.proindependent.com/qtexengine/)
##########################################################

# include path.
TEX_ENGINE_INCLUDEPATH = $$QTI_ROOT/3rdparty/QTeXEngine/src
# link locally against a copy in 3rdparty/
TEX_ENGINE_LIBS = $$QTI_ROOT/3rdparty/QTeXEngine/libQTeXEngine.a

##########################################################
## ALGLIB (2.6) - optional. you don't have to set these variables
# [http://www.alglib.net/](http://www.alglib.net/)
##########################################################

# include path.
#ALGLIB_INCLUDEPATH = $$QTI_ROOT/3rdparty/alglib/mpfr/src
# link locally against a copy in 3rdparty/
#ALGLIB_LIBS = $$QTI_ROOT/3rdparty/alglib/mpfr/libalglib.a


##########################################################
## Qt tools - allows to use specific versions
##########################################################

LUPDATE = lupdate
LRELEASE = lrelease

############################################################
##  Target specific configuration: configure Qtiplot itself
############################################################

contains( TARGET, qtiplot ) {
  # building without muParser doesn't work yet
  SCRIPTING_LANGS += muParser
  SCRIPTING_LANGS += Python

  # a console displaying output of scripts; particularly useful on Windows
  # where running QtiPlot from a terminal is inconvenient
  DEFINES         += SCRIPTING_CONSOLE

  #DEFINES         += QTIPLOT_DEMO

  # Uncomment the following line if you want to perform a custom installation using the *.path variables defined in ./qtiplot.pro.
  #CONFIG          += CustomInstall

  # Uncomment the following line if you want to build QtiPlot as a browser plugin (not working on Internet Explorer).
  #CONFIG          += BrowserPlugin
  
  CONFIG          += release
  #CONFIG          += debug
  #win32: CONFIG   += console
}
Ends

12. qmake and make in qtiplot-0.9.8.3 directory (where build.conf is).

It should compile showing the possibility to open Origin files.
I do not know what if commenting out line 793 (see above) will make a major difference.
It seems related to a different version of liborigin2 (see qtiplot forum).

---

### Post by barmaley on 2010-10-15
Thank you, niscima
I tried compiling qtiplot-0.9.8.3 following your directions, but still no go.
At step 8 I got the following error:
./logging.hpp: At global scope:
./logging.hpp:725: warning: unused parameter ‘log_param’
OriginFile.cpp: In constructor ‘OriginFile::OriginFile(const std::string&)’:
OriginFile.cpp:92: error: ‘BOOST_LOG_FINALIZE’ was not declared in this scope
make: *** [tmp/OriginFile.o] Error 1

Any ideas?

---

### Post by ls8 on 2010-10-15
Don't download loglite-0.4.0.zip, you need to compile with the one included with qtiplot-0.9.8.3 sources.


To remove the annoying donation nag screen edit qtiplot-0.9.8.3/qtiplot/src/core/QtiPlotApplication.cpp, delete lines

#ifndef QTIPLOT_PRO
	mw->showDonationDialog();
#endif

---

### Post by niscima on 2010-10-16
That's right.
logging.hpp ia already included.
I will try to recompile again trying to make things as clean as possible.
See also this slightly different procedure:
[http://doc.ubuntu-fr.org/qtiplot](http://doc.ubuntu-fr.org/qtiplot)

Regards

---

### Post by barmaley on 2010-10-16
Thanks, niscima and ls8
It worked this time. It is a great idea to make the instructions a bit more clearer. So, for example, it is only necessary to put tree.hh in the liborigin2 folder. This file can be downloaded from the web, and not the archive tree-2.6.5.zip, and so on.
It was a great help for me, thank you very much.

---

### Post by barmaley on 2010-10-18
Hi, people
On my 2nd comp at work I still have a problem compiling qtiplot. I did everything as for the 1st pc, but there is this error:

src/core/ApplicationWindow.cpp:174: fatal error: QAssistantClient: No such file or directory
compilation terminated.
make[1]: *** [../tmp/qtiplot/ApplicationWindow.o] Error 1

Any ideas?

---

### Post by niscima on 2010-10-18
Barmaley,

you have to install libqtassistantclient-dev.

Regards.

---

### Post by barmaley on 2010-10-18
Hi, niscima
Thanks for your help.

libqtassistantclient-dev is already the newest version.

I began from that point, but that was not it?

---

### Post by niscima on 2010-10-18
Instruction for 64bit ubuntu:

sudo apt-get install build-essential g++ libboost-all-dev libpng12-dev libqt4-dev 
libgsl0-dev python2.6-dev python-qt4-dev python-sip4-dev
libtool zlib1g-dev qt4-dev-tools python-all-dev libxext-dev libqtassistantclient-dev
qt-assistant-compat libqtassistantclient4 qa-assistant

Forget about libEMF and EmfEngine (probably they will work on 32 bit but for me they did not)

Sip and Pyqt should be provided by the packages above

Follow: [http://doc.ubuntu-fr.org/qtiplot](http://doc.ubuntu-fr.org/qtiplot) for
quazip, muparser, QTeXEngine, tree (do not forget to copy tree.hh in /usr/local/include), liborigin2, alglib

Follow message #1 for ExcelFormat (32 or 64)

Use build.conf from [http://doc.ubuntu-fr.org/qtiplot](http://doc.ubuntu-fr.org/qtiplot)
but use[FONT=monospace]
[/FONT]XLS_INCLUDEPATH = XLS_LIBS = -lExcelFormat Use instructions from [http://doc.ubuntu-fr.org/qtiplot](http://doc.ubuntu-fr.org/qtiplot) for
QTI_ROOT/qtiplot/src/origin/origin.pri
QTI_ROOT/qtiplot/qtiplot.pro
QTI_ROOT/qtiplot/src/origin/importOPJ.cpp

remove 'manual' line from QTI_ROOT/qtiplot.pro

do as in message #21

qmake and make

It should work. I ended up with a 58.6 qtiplot executable.
It shows odf and xls opening, origin import, python scripting.
Good luck.

---

### Post by niscima on 2010-10-18
Sorry for messing up build.conf modifications.
I hope now it will show up correctly
XLS_INCLUDEPATH =
XLS_LIBS = -lExcelFormat

---

### Post by niscima on 2010-10-18
For the manual download
[http://prdownload.berlios.de/qtiplot/qtiplot-manual-en.tar.bz2](http://prdownload.berlios.de/qtiplot/qtiplot-manual-en.tar.bz2)
and expand it somewhere.
All the installed assistants should allow to open it directly from the help menu of qtiplot

---

### Post by barmaley on 2010-10-18
Thanks, niscima
I have 32bit system, and all of the libraries installed.
I'll try to compile tomorrow and I hope I will not bother you again.

---

### Post by barmaley on 2010-10-19
Thanks a lot guys. I have finally managed to compile it. I have to follow instructions in french - that's a tough task.

---

### Post by barmaley on 2010-10-19
Origin files are not imported: Segmentation fault when trying to open any of them.
It worked in qtiplot-0.9.8.2.
Any ideas?

---

### Post by ls8 on 2010-10-21
Full guide to compile Qtiplot 0.9.8.3 on Ubuntu 10.10 Maverick Meerkat x64 (should work on i386 too).

1/ Install all necessary packages and libraries
```
sudo apt-get install build-essential g++ libboost-all-dev libpng12-dev libqt4-dev libgsl0-dev python2.6-dev python-qt4-dev python-sip4-dev pyqt4-dev-tools libqtassistantclient-dev
```

2/ Download and untar Qtiplot 0.9.8.3 source codes
```

wget http://download.berlios.de/qtiplot/qtiplot-0.9.8.3.tar.bz2
tar xjfv qtiplot-0.9.8.3.tar.bz2

```

3/ Download, untar and compile latest muParser from sources
```

wget http://downloads.sourceforge.net/project/muparser/muparser/Version%201.34/muparser_v134.tar.gz
cd qtiplot-0.9.8.3/3rdparty/
tar xzfv ../../muparser_v134.tar.gz
cd muparser_v134/
./configure --enable-shared=no
make
cd ../../../

```

4/ Download, untar and compile latest QuaZIP from sources
```

wget http://downloads.sourceforge.net/project/quazip/quazip/0.3/quazip-0.3.tar.gz
cd qtiplot-0.9.8.3/3rdparty/
tar xzfv ../../quazip-0.3.tar.gz
cd quazip-0.3/quazip/

```

Edit quazip.pro file - line #6
replace
```
CONFIG += qt warn_on
```
with
```
CONFIG += qt warn_on staticlib
```

Compile QuaZIP:
```

qmake
make
cd ../../../../

```

5/ Download and compile latest ExcelFormat from SVN
```

cd qtiplot-0.9.8.3/3rdparty/
mkdir ExcelFormat
cd ExcelFormat
wget http://shell.franken.de/svn/sky/excel/trunk/ExcelFormat/BasicExcel.cpp
wget http://shell.franken.de/svn/sky/excel/trunk/ExcelFormat/BasicExcel.hpp
wget http://shell.franken.de/svn/sky/excel/trunk/ExcelFormat/ExcelFormat.cpp
wget http://shell.franken.de/svn/sky/excel/trunk/ExcelFormat/ExcelFormat.h
g++ -c -fPIC -Wall -include string.h -I./ExcelFormat.hpp -I./BasicExcel.h -o ExcelFormat.o ExcelFormat.cpp
g++ -c -fPIC -Wall -include string.h -I./ExcelFormat.hpp -I./BasicExcel.h -o BasicExcel.o BasicExcel.cpp
ar rcs libExcelFormat.a BasicExcel.o ExcelFormat.o
cd ../../../

```

6/ Download and unzip latest liborigin2 sources
```

wget http://download.berlios.de/qtiplot/liborigin2-13092010.zip
cd qtiplot-0.9.8.3/3rdparty/
unzip ../../liborigin2-13092010.zip
cd ../../

```

7/ Download latest tree.hh header file and copy it to the liborigin2 folder
```

cd qtiplot-0.9.8.3/3rdparty/liborigin2/
wget http://tree.phi-sci.com/tree.hh
cd ../../../

```

8/ Download, untar and compile latest QTeXEngine from sources
```

wget http://download.berlios.de/qtiplot/QTeXEngine-0.2-opensource.zip
cd qtiplot-0.9.8.3/3rdparty/
unzip ../../QTeXEngine-0.2-opensource.zip
cd QTeXEngine/
qmake
make
cd ../../../

```

9/ Download, untar and compile ALGLIB 2.6.0 from sources
```
wget http://www.alglib.net/translator/re/alglib-2.6.0.cpp.zip
mkdir qtiplot-$VERSION/3rdparty/alglib
cd qtiplot-$VERSION/3rdparty/alglib/
unzip ../../../alglib-2.6.0.cpp.zip
cd cpp
chmod +x build
./build gcc
cd ../../../../

```

10/ Edit some files:

qtiplot.pro - delete line #4
```
manual \
```

qtiplot/src/origin/importOPJ.cpp - delete line #793
```
case Origin::GraphCurve::XYZContour:
```

qtiplot/src/origin/origin.pri - replace each occurence of
```
3rpdarty/liborigin
```
with
```
3rpdarty/liborigin2
```

qtiplot/src/core/QtiPlotApplication.cpp - delete lines #60-#62
```

#ifndef QTIPLOT_PRO
             mw->showDonationDialog();
#endif  

```

build.conf
```

isEmpty( QTI_ROOT ) {
  message( "each file including this config needs to set QTI_ROOT to the dir containing this file!" )
}

##########################################################
##     System specific configuration
##########################################################

# Global include path which is always added at the end of the INCLUDEPATH
SYS_INCLUDEPATH = /opt/local/include
# Global lib path and libs which is ls always added at the end of LIBS
SYS_LIBS = -L/opt/local/lib

##########################################################
## zlib (http://www.zlib.net/)
##########################################################

# include path. leave it blank to use SYS_INCLUDE
ZLIB_INCLUDEPATH = $$QTI_ROOT/3rdparty/zlib/

##########################################################
## muParser (http://muparser.sourceforge.net/)
##########################################################

# include path. leave it blank to use SYS_INCLUDE
MUPARSER_INCLUDEPATH = $$QTI_ROOT/3rdparty/muparser_v134/include
# link statically against a copy in 3rdparty/
MUPARSER_LIBS = $$QTI_ROOT/3rdparty/muparser_v134/lib/libmuparser.a
# or dynamically against a system-wide installation
#MUPARSER_LIBS = -lmuparser

##########################################################
## GNU Sientific Library (http://www.gnu.org/software/gsl/)
##########################################################

# include path. leave it blank to use SYS_INCLUDE
GSL_INCLUDEPATH = 
# link dynamically against a system-wide installation
GSL_LIBS = -lgsl -lgslcblas

##########################################################
## QWT - use local copy till upstream catches up
# http://qwt.sourceforge.net/index.html
##########################################################

# include path.
QWT_INCLUDEPATH = $$QTI_ROOT/3rdparty/qwt/src
# link locally against a copy in 3rdparty/
QWT_LIBS = $$QTI_ROOT/3rdparty/qwt/lib/libqwt.a

##########################################################
## QwtPlot3D - use local copy till upstream catches up
# http://qwtplot3d.sourceforge.net/
##########################################################

# include path.
QWT3D_INCLUDEPATH = $$QTI_ROOT/3rdparty/qwtplot3d/include
# link locally against a copy in 3rdparty/
QWT3D_LIBS = $$QTI_ROOT/3rdparty/qwtplot3d/lib/libqwtplot3d.a

##########################################################
## Boost libraries (http://www.boost.org/) - optional
##########################################################

# include path. leave it blank to use SYS_INCLUDE
BOOST_INCLUDEPATH = 
# link dynamically against a system-wide installation
BOOST_LIBS = -lboost_date_time-mt -lboost_thread-mt

##########################################################
## liborigin2 - optional. you don't have to set these variables
# http://soft.proindependent.com/liborigin2/
##########################################################

# include path. leave it blank to use SYS_INCLUDE
LIBORIGIN_INCLUDEPATH = $$QTI_ROOT/3rdparty/liborigin2
# link statically against a copy in 3rdparty/
LIBORIGIN_LIBS = $$QTI_ROOT/3rdparty/liborigin2/liborigin2.a

###########################################################
## ExcelFormat - optional. you don't have to set these variables
# http://www.codeproject.com/KB/office/ExcelFormat.aspx
###########################################################

# include path.
XLS_INCLUDEPATH = $$QTI_ROOT/3rdparty/ExcelFormat/
# link locally against a copy in 3rdparty/
XLS_LIBS = $$QTI_ROOT/3rdparty/ExcelFormat/libExcelFormat.a

###########################################################
## QuaZIP - optional. you don't have to set these variables
# http://quazip.sourceforge.net/
###########################################################

# include path.
QUAZIP_INCLUDEPATH = $$QTI_ROOT/3rdparty/quazip-0.3/quazip/
# link locally against a copy in 3rdparty/
QUAZIP_LIBS = $$QTI_ROOT/3rdparty/quazip-0.3/quazip/libquazip.a

##########################################################
## libpng - optional. you don't have to set these variables
##########################################################

# include path. leave it blank to use SYS_INCLUDE
LIBPNG_INCLUDEPATH = 
# link dynamically against a system-wide installation
LIBPNG_LIBS = -lpng

##########################################################
## QTeXEngine - optional. you don't have to set these variables
# http://soft.proindependent.com/qtexengine/
##########################################################

# include path.
TEX_ENGINE_INCLUDEPATH = $$QTI_ROOT/3rdparty/QTeXEngine/src
# link locally against a copy in 3rdparty/
TEX_ENGINE_LIBS = $$QTI_ROOT/3rdparty/QTeXEngine/libQTeXEngine.a

##########################################################
### ALGLIB (2.6) - optional. you don't have to set these variables
## http://www.alglib.net/
###########################################################

# include path.
ALGLIB_INCLUDEPATH = $$QTI_ROOT/3rdparty/alglib/cpp/src
# link locally against a copy in 3rdparty/
ALGLIB_LIBS = $$QTI_ROOT/3rdparty/alglib/cpp/out/libalglib.a

##########################################################
## python - only used if python is needed
##########################################################

# the python interpreter to use
# (unix only, windows will use what ever is configured to execute .py files!)
PYTHON = python

##########################################################
## Qt tools - allows to use specific versions
##########################################################

LUPDATE = lupdate
LRELEASE = lrelease

############################################################
##  Target specific configuration: configure Qtiplot itself
############################################################

contains( TARGET, qtiplot ) {
  # building without muParser doesn't work yet
  SCRIPTING_LANGS += muParser
  SCRIPTING_LANGS += Python

  # a console displaying output of scripts; particularly useful on Windows
  # where running QtiPlot from a terminal is inconvenient
  DEFINES         += SCRIPTING_CONSOLE

  #DEFINES         += QTIPLOT_DEMO

  # Uncomment the following line if you want to perform a custom installation using the *.path variables defined in ./qtiplot.pro.
  #CONFIG          += CustomInstall

  # Uncomment the following line if you want to build QtiPlot as a browser plugin (not working on Internet Explorer).
  #CONFIG          += BrowserPlugin
  
  CONFIG          += release
  #CONFIG          += debug
  #win32: CONFIG   += console
}

```

11/ Compile Qtiplot 0.9.8.3
```

qmake
make

```

12/ Start Qtiplot 0.9.8.3
```

qtiplot/qtiplot

```

[IMG]http://img651.imageshack.us/img651/9818/origin0983.png[/IMG]

---

### Post by niscima on 2010-10-21
Thanks a lot ls8.
It works.
If you add the following to build-all:

wget [http://www.alglib.net/translator/re/alglib-2.6.0.cpp.zip](http://www.alglib.net/translator/re/alglib-2.6.0.cpp.zip)
cd qtiplot-$VERSION/3rdparty/
unzip ../../alglib-2.6.0.cpp.zip
cd cpp
chmod +x build
/.build gcc
cd ../../../

and the following to build.conf

##########################################################
## ALGLIB (2.6) - optional. you don't have to set these variables
# [http://www.alglib.net/](http://www.alglib.net/)
##########################################################

# include path.
ALGLIB_INCLUDEPATH = $$QTI_ROOT/3rdparty/cpp/out
# link locally against a copy in 3rdparty/
ALGLIB_LIBS = $$QTI_ROOT/3rdparty/cpp/out/libalglib.a

It will compile with alglib support.

Thanks again

---

### Post by ls8 on 2010-10-21
Sure, no problem. What functionality does the Alglib bring to Qtiplot?

---

### Post by niscima on 2010-10-21
According to manual:

"If QtiPlot has been built with support for ALGLIB, you can also change the dimensions of a 
matrix by resampling it, using bilinear or bicubic interpolation"

Thanks.

---

### Post by ls8 on 2010-10-22
Both Post#33 and online script updated, now with ALGLIB 2.6.0 support.

---

### Post by niscima on 2010-10-22
I checked already alglib 3.0.0 and does not seem to be compatible with qtiplot 0.9.8.3 source files.
Qtiplot readme.html says that you need alglib 2.6.0 and alglib site says that new version is not compatible with the previous one (you can just check the src folder and see how different the number of include files is).

---

### Post by ls8 on 2010-10-22
Yes, I found that too. The post#33 and scripts are now updated for ALGLIB 2.6.0. I think it should work on Ubuntu 10.04 too, just libqtassistantclient-dev is not necessary to install (Ubuntu 10.04 includes an older Qt which includes QtAssistant by default). Maybe someone can test it?

**Edit Oct25:** [COLOR="Blue"]Tested and works with Ubuntu 10.04 and Ubuntu 10.10, both 32 and 64bit versions.[/COLOR] Don't install libqtassistantclient-dev on Ubuntu 10.04, this package does not exist for Lucid.

---

### Post by jones.79 on 2010-11-19
Very nice script!!


I am using Ubuntu 10.04 and when I ran the script it stops saying that qmake is neccessary and one should install the package qt4-dev-tools (or another qt3...).
Can someone confirm this?

If this is common maybe it should be added to the neccessary packages line. Is this one needed for 10.10, too or is qmake in one of the listed packages?

There could be two commented lines in the script, one for 10.04 (without libqtassistantclient-dev and with qt4-dev-tools) and another one for 10.10 .

Any maybe you could edit post #33 so that the first lines mention that a script is available at the very bottom ;)

Kind regards,
jones

---

### Post by d_darlac on 2010-11-30
It didn't work form me..
here is the error message:
cd fitPlugins && qmake fitPlugins.pro -o Makefile
cd fitPlugins && make -f Makefile
make[1]: Entering directory `/home/dimitris/qtiplot-0.9.8.3/fitPlugins'
cd explin && qmake explin.pro -o Makefile
cd explin && make -f Makefile
make[2]: Entering directory `/home/dimitris/qtiplot-0.9.8.3/fitPlugins/explin'
gcc -c -pipe -g -Wall -W -O2 -D_REENTRANT -fPIC  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/opt/local/include -I/usr/include/qt3 -o explin.o explin.c
explin.c:33:28: error: gsl/gsl_vector.h: No such file or directory
explin.c:34:28: error: gsl/gsl_matrix.h: No such file or directory
explin.c:56: warning: type defaults to ‘int’ in declaration of ‘gsl_vector’
explin.c:56: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
explin.c:70: warning: type defaults to ‘int’ in declaration of ‘gsl_vector’
explin.c:70: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
explin.c:85: warning: type defaults to ‘int’ in declaration of ‘gsl_vector’
explin.c:85: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
explin.c:103: warning: type defaults to ‘int’ in declaration of ‘gsl_vector’
explin.c:103: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
make[2]: *** [explin.o] Error 1
make[2]: Leaving directory `/home/dimitris/qtiplot-0.9.8.3/fitPlugins/explin'
make[1]: *** [sub-explin] Error 2
make[1]: Leaving directory `/home/dimitris/qtiplot-0.9.8.3/fitPlugins'
make: *** [sub-fitPlugins] Error 2

any help would be appreciated!

---

### Post by jones.79 on 2010-11-30
Is the gsl-dev package (don't know if this is the correct name...) installed?

---

### Post by d_darlac on 2010-11-30
I tried to install the package but I get a message that the package is obsolete, and the lobgsl0-dev is being used instead

---

### Post by jones.79 on 2010-11-30
And libgsl0-dev is installed? :) 
Well, on my system everything works fine, and the missing header files are in /usr/include/gsl. I also have libgsl0ldbl installed, maybe this one is neccessary, too.

If it is still not working search for the missing header files on your system
(gsl_vector.h gsl_matrix.h) and add the include-path to the Makefile (e.g. -I/usr/include/...)

---

### Post by d_darlac on 2010-12-01
no, I have installed libgsl0ldbl too - 
I will try to manually add the headers - 
I will update the post soon

---

### Post by jones.79 on 2010-12-01
Have you searched for the missing files? Where are they?

---

### Post by d_darlac on 2010-12-02
I did a search for the files, no luck - 
it is interesting since the previous qtiplot version works fine - 
not sure what the next step is

---

### Post by jones.79 on 2010-12-02
Hm, you need that gsl-stuff to compile.
If you cant find it with a package manager or something similar
you have to get them here [http://www.gnu.org/software/gsl/](http://www.gnu.org/software/gsl/)

---

### Post by d_darlac on 2010-12-02
I compiled it, but still getting the same problem...
I am planning to upgrade to Maverick next week - so I will try again with a clean install...
I will updated the thread on the new install - thanks for your help

---

### Post by UChris on 2011-01-11
ls8: Thank you 1000 times!  I have been having so much trouble getting this new version working.

I've followed the script line for line, and am getting stuck on the final make.

I get the following error:
```
src/matrix/Matrix.cpp:1672: error: call of overloaded ‘GetWorksheet(size_t)’ is ambiguous
../3rdparty/ExcelFormat/BasicExcel.hpp:1727: note: candidates are: YExcel::BasicExcelWorksheet* YExcel::BasicExcel::GetWorksheet(int)
../3rdparty/ExcelFormat/BasicExcel.hpp:1728: note:                 YExcel::BasicExcelWorksheet* YExcel::BasicExcel::GetWorksheet(const char*)
../3rdparty/ExcelFormat/BasicExcel.hpp:1729: note:                 YExcel::BasicExcelWorksheet* YExcel::BasicExcel::GetWorksheet(const wchar_t*)
make[1]: *** [../tmp/qtiplot/Matrix.o] Error 1
make[1]: Leaving directory `/home/chris/sigh/qtiplot-0.9.8.3/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2
```Any ideas?  

I had to download libboost-all-dev separately, because I am running Linux Mint (8 Helena - x64 Edition), but every other step went swimmingly.  There are a few warnings before the error, but they are all "X will be initialized after Y".

---

### Post by niscima on 2011-01-12
Reply to message #50.

Use ExcelFormat libraries attached to message #1.

It should work

---

### Post by UChris on 2011-01-18
Get ExcelFormat from first post, recompile, and attempt to make qtiplot:

```
../tmp/qtiplot/ApplicationWindow.o: In function `ApplicationWindow::importExcelCrossplatform(QString const&, int)':
ApplicationWindow.cpp:(.text+0xaf8db): undefined reference to `YExcel::BasicExcel::GetWorksheet(int)'
ApplicationWindow.cpp:(.text+0xaf8f1): undefined reference to `YExcel::BasicExcelWorksheet::GetTotalRows() const'
ApplicationWindow.cpp:(.text+0xaf8ff): undefined reference to `YExcel::BasicExcelWorksheet::GetTotalCols() const'
ApplicationWindow.cpp:(.text+0xafbbb): undefined reference to `YExcel::BasicExcelWorksheet::Cell(int, int)'
collect2: ld returned 1 exit status
make: *** [qtiplot] Error 1

```

---

### Post by volfoni54 on 2011-01-22
Hi,

You must link with the ExcelFormat library. Could you tell us what is the location and the exact name of this lib ?

Otherwise, you can find all explanations on: [http://doc.ubuntu-fr.org/qtiplot](http://doc.ubuntu-fr.org/qtiplot). If you don"t speak french, I can explain.

Thanks

Raoul

---

### Post by barmaley on 2011-02-20
Hi, ubuntu people.
I was trying to compile qtiplot-0.9.8.4 using the french web-site, but with no luck. When I got to the make of qtiplot, I got the following error:
cd qtiplot/ && make -f Makefile 
make[1]: Entering directory `/home/casper/QtiPlot/qtiplot-0.9.8.4/qtiplot'
g++ -c -pipe -O2 -D_REENTRANT -Wall -W -DSCRIPTING_CONSOLE -DSVN_REVISION="\"\"" -DQT_PLUGIN -DSCRIPTING_MUPARSER -DSCRIPTING_PYTHON -DGL2PS_HAVE_LIBPNG -DTEX_OUTPUT -DHAVE_TAMUANOVA -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_QT3SUPPORT_LIB -DQT3_SUPPORT -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I/usr/include/qt4/QtAssistantClient -I/usr/include/qt4/QtAssistant -I../3rdparty/zlib -I/usr/include/muParser -I../3rdparty/qwt/src -I../3rdparty/qwtplot3d/include -Iicons -Isrc/analysis -Isrc/analysis/dialogs -Isrc/core -Isrc/excel -Isrc/lib/include -Isrc/lib/3rdparty/qtcolorpicker/src -Isrc/plot2D -Isrc/plot2D/dialogs -Isrc/plot3D -Isrc/matrix -Isrc/table -Isrc/scripting -I/usr/include/python2.6 -I../3rdparty/QTeXEngine/src -I../3rdparty/tamu_anova/ -I/opt/local/include -I/usr/X11R6/include -I/home/casper/QtiPlot/qtiplot-0.9.8.4/tmp/qtiplot -o ../tmp/qtiplot/sipqtiAnova.o ../tmp/qtiplot/sipqtiAnova.cpp
In file included from src/scripting/qti.sip:3396:
src/analysis/Anova.h:33: fatal error: tamu_anova.h: No such file or directory
compilation terminated.
make[1]: *** [../tmp/qtiplot/sipqtiAnova.o] Error 1
make[1]: Leaving directory `/home/casper/QtiPlot/qtiplot-0.9.8.4/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2

Any help is greatly appreciated.

---

### Post by volfoni54 on 2011-02-21
Hi,

First of all, my page has not been tested so it may stay somme mistakes.

Did you install tamu_anova as I write on the ubuntu french page ??
If you did so. It is very important to know where is the location of the tamu_anova directory and the qtiplot-0.9.8.4 directory to solve your problem.

Do you use the same build.conf file ?

Thanks.

Raoul

---

### Post by volfoni54 on 2011-02-21
I see on your command line that your tamu_anova is relative to : **-I../3rdparty/tamu_anova/**.

So I think, you don't use the same configuration file.

Raoul

---

### Post by niscima on 2011-02-21
I successfully compiled 0.9.8.4 version on Ubuntu Maverick.
The opening of .opj files and the import of .xls and .odf files has been disabled.
So putting references to excelimport and liborigin2 is simply useless.

---

### Post by volfoni54 on 2011-02-21
Opj file import could be useful ...

---

### Post by niscima on 2011-02-21
This is what ita say when trying to open an opj file.

---

### Post by volfoni54 on 2011-02-21
Effectively, you are right...

Opj, xls and odf imports are now disabled. It's a pity.

Regards

---

### Post by barmaley on 2011-02-21
Here is the content of QtiPlot folder:
casper@casper-home:~/QtiPlot$ ls
cpp
EmfEngine
ExcelFormat_src
liborigin2
QTeXEngine
qtiplot-0.9.8.4
tamu-anova-0.2

I used the build.config from the french site and I still have an error:

g++ -c -pipe -O2 -D_REENTRANT -Wall -W -DSCRIPTING_CONSOLE -DSVN_REVISION="\"\"" -DQT_PLUGIN -DSCRIPTING_MUPARSER -DSCRIPTING_PYTHON -DGL2PS_HAVE_LIBPNG -DTEX_OUTPUT -DHAVE_ALGLIB -DHAVE_TAMUANOVA -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_QT3SUPPORT_LIB -DQT3_SUPPORT -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I/usr/include/qt4/QtAssistantClient -I/usr/include/qt4/QtAssistant -I../3rdparty/zlib -I/usr/local/include -I../3rdparty/qwt/src -I../3rdparty/qwtplot3d/include -Iicons -Isrc/analysis -Isrc/analysis/dialogs -Isrc/core -Isrc/excel -Isrc/lib/include -Isrc/lib/3rdparty/qtcolorpicker/src -Isrc/plot2D -Isrc/plot2D/dialogs -Isrc/plot3D -Isrc/matrix -Isrc/table -Isrc/scripting -I/usr/include/python2.6 -I../../QTexEngine/src/ -I../../cpp/src -I../../tamu_anova-0.2/ -I-I/../tmp/qtiplot -I/usr/X11R6/include -I/home/casper/QtiPlot/qtiplot-0.9.8.4/tmp/qtiplot -o ../tmp/qtiplot/sipqtiAnova.o ../tmp/qtiplot/sipqtiAnova.cpp
In file included from src/scripting/qti.sip:3396:
src/analysis/Anova.h:33: fatal error: tamu_anova.h: No such file or directory
compilation terminated.

I have tried to compile qtiplot using this site:
[http://elubuntu.blogspot.com/2011/02/compilare-qtiplot-0984.html?showComment=1298300856752#c1457899482721242809](http://elubuntu.blogspot.com/2011/02/compilare-qtiplot-0984.html?showComment=1298300856752#c1457899482721242809)

He has everything in 3rdparty folder, and The build.config is different. I still had a problem with that tamu_nova. Does anyone know how to compile without tamu_nova, or can provide with the step-by-step instructions that work.
Thanks for your help.

---

### Post by barmaley on 2011-02-21
I found the reason for that anova error, it was "tamu-anova", and should be "tamu_anova". Well, now I have another one:
g++: ../3rdparty/qwtplot3d/lib/libqwtplot3d.a: No such file or directory

Who knows what to do, please, help.

---

### Post by volfoni54 on 2011-02-21
Did you had the line 

unix:CONFIG   +=    staticlib

on the 3rdparty/qwtplot3d/libqwtplot3d.pro ?

---

### Post by barmaley on 2011-02-21
"""unix:CONFIG += staticlib
on the 3rdparty/qwtplot3d/libqwtplot3d.pro ?"""

Do you mean 3rdparty/qwtplot3d/qwtplot3d.pro ?
I did not have such a line in this file, but I did not have it for qtiplot-0.9.8.3 and it was compiled successfully.
Where should I put that line?

---

### Post by volfoni54 on 2011-02-22
> **barmaley said:**
> 

Do you mean 3rdparty/qwtplot3d/qwtplot3d.pro ?


Yes...
> **barmaley said:**
> 
I did not have such a line in this file, but I did not have it for qtiplot-0.9.8.3 and it was compiled successfully.
Where should I put that line?
IN the 3rdparty/qwtplot3d/qwtplot3d.pro where you want. I put it on line 17. Here are the first lines :

# pro file for building the makefile for qwtplot3d

#



include (qwtplot3d.pri)



CONFIG          += qt warn_on opengl thread zlib release

MOC_DIR          = tmp

OBJECTS_DIR      = tmp

INCLUDEPATH      = include

DEPENDPATH       = include src

QT              += opengl



CONFIG          += dll

win32:CONFIG    += exceptions

win32:dll:DEFINES    += QT_DLL QWT3D_DLL QWT3D_MAKEDLL

win32:QMAKE_CXXFLAGS += $$QMAKE_CFLAGS_STL

unix:CONFIG		+= staticlib



# Comment the next line, if you have zlib on your windows system

win32:CONFIG    -= zlib

---

### Post by barmaley on 2011-02-22
Hi, everyone
It's killing me. I added the "unix:CONFIG  += staticlib" line to 3rdparty/qwtplot3d/qwtplot3d.pro. After "make" command, the compilation was doing the job for quite a bit, and then I got a new error. I attached it to the comment, since the forum did not allow me to post it as it is :)
Need your help, guys.
Thanks.

---

### Post by volfoni54 on 2011-02-24
> **barmaley said:**
> Hi, everyone
It's killing me. I added the "unix:CONFIG  += staticlib" line to 3rdparty/qwtplot3d/qwtplot3d.pro. After "make" command, the compilation was doing the job for quite a bit, and then I got a new error. I attached it to the comment, since the forum did not allow me to post it as it is :)
Need your help, guys.
Thanks.

I don't know what is this error. could you try do to a 'make clean' and compile again.

What is your version's number of muParser ?

Thanks

Raoul

---

### Post by barmaley on 2011-02-24
I installed muparser_v134. I took it from this web-page [http://downloads.sourceforge.net/project/muparser/muparser/Version%201.34/muparser_v134.tar.gz](http://downloads.sourceforge.net/project/muparser/muparser/Version%201.34/muparser_v134.tar.gz)
actually I followed the french site directions.
Do you think I should re-install it?

---

### Post by volfoni54 on 2011-02-24
> **barmaley said:**
> 
Do you think I should re-install it?

No, I think you should do a "make clean", delete the files in QTI_ROOT/tmp/qtiplot and then try yo recompile it.

Do you have more errors ?

Thanks

Raoul

---

### Post by barmaley on 2011-02-24
I did make clean and cleaned QTI_ROOT/tmp/qtiplot folder, after that I ran qmake and make again, but still ERROR:

src/scripting/muParserScripting.cpp:103: warning: deprecated conversion from string constant to ‘char*’
src/scripting/muParserScripting.cpp:103: warning: deprecated conversion from string constant to ‘char*’
g++ -c -pipe -O2 -D_REENTRANT -Wall -W -DSCRIPTING_CONSOLE -DSVN_REVISION="\"\"" -DQT_PLUGIN -DSCRIPTING_MUPARSER -DSCRIPTING_PYTHON -DGL2PS_HAVE_LIBPNG -DTEX_OUTPUT -DHAVE_ALGLIB -DHAVE_TAMUANOVA -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_QT3SUPPORT_LIB -DQT3_SUPPORT -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I/usr/include/qt4/QtAssistantClient -I/usr/include/qt4/QtAssistant -I../3rdparty/zlib -I/usr/local/include -I../3rdparty/qwt/src -I../3rdparty/qwtplot3d/include -Iicons -Isrc/analysis -Isrc/analysis/dialogs -Isrc/core -Isrc/excel -Isrc/lib/include -Isrc/lib/3rdparty/qtcolorpicker/src -Isrc/plot2D -Isrc/plot2D/dialogs -Isrc/plot3D -Isrc/matrix -Isrc/table -Isrc/scripting -I/usr/include/python2.6 -I../../QTexEngine/src/ -I../../cpp/src -I../../tamu_anova-0.2 -I-I/../tmp/qtiplot -I/usr/X11R6/include -I/home/casper/QtiPlot_fr/qtiplot-0.9.8.4/tmp/qtiplot -o ../tmp/qtiplot/PythonScript.o src/scripting/PythonScript.cpp
g++ -c -pipe -O2 -D_REENTRANT -Wall -W -DSCRIPTING_CONSOLE -DSVN_REVISION="\"\"" -DQT_PLUGIN -DSCRIPTING_MUPARSER -DSCRIPTING_PYTHON -DGL2PS_HAVE_LIBPNG -DTEX_OUTPUT -DHAVE_ALGLIB -DHAVE_TAMUANOVA -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_QT3SUPPORT_LIB -DQT3_SUPPORT -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I/usr/include/qt4/QtAssistantClient -I/usr/include/qt4/QtAssistant -I../3rdparty/zlib -I/usr/local/include -I../3rdparty/qwt/src -I../3rdparty/qwtplot3d/include -Iicons -Isrc/analysis -Isrc/analysis/dialogs -Isrc/core -Isrc/excel -Isrc/lib/include -Isrc/lib/3rdparty/qtcolorpicker/src -Isrc/plot2D -Isrc/plot2D/dialogs -Isrc/plot3D -Isrc/matrix -Isrc/table -Isrc/scripting -I/usr/include/python2.6 -I../../QTexEngine/src/ -I../../cpp/src -I../../tamu_anova-0.2 -I-I/../tmp/qtiplot -I/usr/X11R6/include -I/home/casper/QtiPlot_fr/qtiplot-0.9.8.4/tmp/qtiplot -o ../tmp/qtiplot/PythonScripting.o src/scripting/PythonScripting.cpp
src/scripting/PythonScripting.cpp:61: fatal error: sipAPIqti.h: No such file or directory
compilation terminated.
make[1]: *** [../tmp/qtiplot/PythonScripting.o] Error 1

Do I have to compile all those sip and muparser, etc in the QTI_ROOT/tmp/ folder? It should not matter, since I used "sudo make install" for all of them, so those libraries are now installed for the entire system. What is wrong with this qtiplot, it is always a struggle, but this time it is outrageous.

---

### Post by wetscape on 2011-02-24
hello,everyone! I am compiling the files in the folder 'qwt', but there is a fatal error at the end.

                     p [PHP]{ margin-bottom: 0.21cm; }  make[2]: Entering directory `/home/cx/qti/qtiplot-0.9.8.4/3rdparty/qwt/src' 
 g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -Imoc/ -o obj/qwt_abstract_scale_draw.o qwt_abstract_scale_draw.cpp 
 In file included from qwt_painter.h:17, 
                  from qwt_abstract_scale_draw.cpp:18: 
 qwt_layout_metrics.h:64: error: ‘QPointF’ does not name a type 
 make[2]: *** [obj/qwt_abstract_scale_draw.o] error 1 
 make[2]:Leaving directory `/home/cx/qti/qtiplot-0.9.8.4/3rdparty/qwt/src' 
 make[1]: *** [sub-src] error 2 
 make[1]:Leaving directory `/home/cx/qti/qtiplot-0.9.8.4/3rdparty/qwt' 
 make: *** [sub-3rdparty-qwt] error 2 
 
[/PHP] i cannot find a sufficient way to cope in google etc. and get the meaning of '[FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]‘QPointF’ does not name a type [/FONT]'. and what should i do?? thanks for your suggestions....

---

### Post by volfoni54 on 2011-02-25
> **barmaley said:**
> I/home/casper/QtiPlot_fr/qtiplot-0.9.8.4/tmp/qtiplot -o ../tmp/qtiplot/PythonScripting.o src/scripting/PythonScripting.cpp
src/scripting/PythonScripting.cpp:61: fatal error: sipAPIqti.h: No such file or directory


Could you tell me if this file is present in the tmp/qtiplot directory ?

Raoul

---

### Post by volfoni54 on 2011-02-25
> **wetscape said:**
> hello,everyone! I am compiling the files in the folder 'qwt', but there is a fatal error at the end.

                     p [PHP]{ margin-bottom: 0.21cm; }  make[2]: Entering directory `/home/cx/qti/qtiplot-0.9.8.4/3rdparty/qwt/src' 
 g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -Imoc/ -o obj/qwt_abstract_scale_draw.o qwt_abstract_scale_draw.cpp 
 In file included from qwt_painter.h:17, 
                  from qwt_abstract_scale_draw.cpp:18: 
 qwt_layout_metrics.h:64: error: ‘QPointF’ does not name a type 
 make[2]: *** [obj/qwt_abstract_scale_draw.o] error 1 
 make[2]:Leaving directory `/home/cx/qti/qtiplot-0.9.8.4/3rdparty/qwt/src' 
 make[1]: *** [sub-src] error 2 
 make[1]:Leaving directory `/home/cx/qti/qtiplot-0.9.8.4/3rdparty/qwt' 
 make: *** [sub-3rdparty-qwt] error 2 
 
[/PHP] i cannot find a sufficient way to cope in google etc. and get the meaning of '[FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]‘QPointF’ does not name a type [/FONT]'. and what should i do?? thanks for your suggestions....

Quite strange this error. What is your version of Ubuntu ?

---

### Post by wetscape on 2011-02-25
> **volfoni54 said:**
> Quite strange this error. What is your version of Ubuntu ?
ubuntu10.04 and the qtiplot is 0.9.8.4 that i got from the official site..

---

### Post by volfoni54 on 2011-02-25
> **wetscape said:**
> ubuntu10.04 and the qtiplot is 0.9.8.4 that i got from the official site..

Did you install all the lib dev as I wrote on the french page ?

---

### Post by barmaley on 2011-02-26
> **volfoni54 said:**
> Could you tell me if this file is present in the tmp/qtiplot directory ?

Raoul

Hi, ubuntu people
There is no such file in this directory. What does it mean? I see it in qtiplot-0.9.8.3 folder. Some library was not installed properly?

---

### Post by barmaley on 2011-02-26
In case I type qmake, I get the error related to sip*.h.
In case I type qmake qtiplot.pro, I get an error related to muParser. which I reported on in previous post.
The error is attached in a txt-file.
SOS!!!

---

### Post by wetscape on 2011-02-27
> **volfoni54 said:**
> Did you install all the lib dev as I wrote on the french page ?
do you mean the notice in term of "À partir de la version 0.9.8.4" on 'http://doc.ubuntu-fr.org/qtiplot'??
i've tried it right now but came the same error. thanks for your support sincerely but i would lost my confidence!!

i referenced the official site of qti  "http://poolinfo.physik.hu-berlin.de/qtiplot-installer/README.html" and  installed all the libs and did as the steps required that went on  smoothly before this error.  i coped several problems followed as the  caution and the experience on page 1 and 5.  what could i do for my  lost,please??

---

### Post by niscima on 2011-02-27
Hi.
Am I wrong saying that trying to compile qtiplot 0.9.8.4 is, at this moment, just a waste of time?
I mean. I compiled it. It runs. Import of excel and odf files and opening of opj files is disabled. All the plugins are missing from the provided source (I wonder if this is compatible with the gpl license).
This is, I believe, the same thing one can get downloading the evaluation version.
The only, probably unfair, thing you get compiling it by yourself, is that one can disable the donation box.
So what's the point in compiling it?
Any comment will be appreciated.

---

### Post by wetscape on 2011-02-27
> **volfoni54 said:**
> Did you install all the lib dev as I wrote on the french page ?
[SIZE=3]i tried the way written in the 1st floor right now, and it came up a similarly strange error:"quazipfileinfo.h:44: error: ‘QString’ does not name a type" when i make the ODF import file. so i conclude a law:  it will error whenever the word began with 'Q' on my computer such as 'QPointF', 'QString'...............:o:(:confused:[/SIZE]

---

### Post by niscima on 2011-02-27
I forgot to say that compiling you also get the python scripting support.
Regards.

---

### Post by wetscape on 2011-02-27
hello! the problem i pasted in #71 and the following floors has been solved. i refered from 
"[FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]http://www.allegro.cc/forums/thread/586909[/FONT] ",
'class QPointF ' and 'QwtPolygon' should be declared before all other files being included...and it goes around.....
unfortunately, another error jumped!!!!!!!!!!!:guitar:

```
                      p { margin-bottom: 0.21cm; }[FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]make[2]: [/FONT]entering directory [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]`/home/cx/qti/qtiplot-0.9.8.4/3rdparty/qwt/src' [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/include/qt3 -Imoc/ -o obj/qwt_abstract_scale_draw.o qwt_abstract_scale_draw.cpp [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]Assembler messages: [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]Fatal error: can't create obj/qwt_abstract_scale_draw.o: Permission denied [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]In file included from qwt_layout_metrics.h:15, [/FONT]
                  [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]from qwt_painter.h:18, [/FONT]
                  [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]from qwt_abstract_scale_draw.cpp:18: [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]qwt_polygon.h:25: error: expected initializer before &#8216;QwtPolygon&#8217; [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]make[2]: *** [obj/qwt_abstract_scale_draw.o] [/FONT]error [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]2 [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]make[2]:[/FONT]leaving directory [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]`/home/cx/qti/qtiplot-0.9.8.4/3rdparty/qwt/src' [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]make[1]: *** [sub-src] [/FONT]error [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]2 [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]make[1]:[/FONT]leaving [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]`/home/cx/qti/qtiplot-0.9.8.4/3rdparty/qwt' [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]make: *** [sub-3rdparty-qwt] [/FONT]error [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]2 [/FONT]
 [FONT=&#25991;&#27849;&#39551;&#24494;&#31859;&#40657;, serif]cx@cx-desktop:~/qti/qtiplot-0.9.8.4$[/FONT]
 
```
and the code of qwt_polygon is:
 ```
 
/* -*- mode: C++ ; c-file-style: "stroustrup" -*- *****************************
 * Qwt Widget Library
 * Copyright (C) 1997   Josef Wilgen
 * Copyright (C) 2002   Uwe Rathmann
 * 
 * This library is free software; you can redistribute it and/or
 * modify it under the terms of the Qwt License, Version 1.0
 *****************************************************************************/

// vim: expandtab

#ifndef QWT_POLYGON_H
#define QWT_POLYGON_H

#include "qwt_global.h"

/*!
  \def QwtPolygon
 */

#if QT_VERSION < 0x040000
#include <qpointarray.h>
#include "qwt_double_rect.h"


typedef QPointArray QwtPolygon;
typedef QMemArray<QwtDoublePoint> QwtPolygonF;

#else

#include <qpolygon.h>
typedef QPolygon QwtPolygon;
typedef QPolygonF QwtPolygonF;
#endif

#endif


```

HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by barmaley on 2011-03-01
Hi, ubuntu people
No news as for the qtiplot-0.9.8.4 compilation.
No one is interested?
I could not find anything helpful allover the internet. This forum was my last island.
Would be grateful for any help.

---

### Post by barmaley on 2011-03-03
Hi, everybody
There is a precompiled version of qtiplot-0.9.8.4 on their home page. It works without crashing, though no python scripting is supported.

---

### Post by wetscape on 2011-03-04
> **barmaley said:**
> Hi, everybody
There is a precompiled version of qtiplot-0.9.8.4 on their home page. It works without crashing, though no python scripting is supported.
where?? how can i get it, please?

---

### Post by barmaley on 2011-03-04
wget [http://download.berlios.de/qtiplot/qtiplot-0.9.8.4-linux.tar.bz2](http://download.berlios.de/qtiplot/qtiplot-0.9.8.4-linux.tar.bz2)
tar xjvf qtiplot-0.9.8.4-linux.tar.bz2
cd qtiplot-0.9.8.4/
./qtiplot

and here you have it.
No Python scripting support and no Origin opj-files export, but works and stable.
enjoy

P.S. I mainly use Qtiplot for non-linear fit of spectral lines, especially in case there are 2 or 3 lines in one profile.
     In version 0.9.8.3 the fitting plug-in was a bit buggy, the cursor point capture was not the best, but in version 0.9.8.4 it 
     seems to be even worse. It is extremely difficult to compile the free version, but the pre-compiled version is not better than
     previous one in view of the old features and plug-ins.
     That's my impression so far.

---

### Post by ls8 on 2011-03-09
> **barmaley said:**
> ...No Python scripting support and no Origin opj-files export, but works and stable...

Origin OPJ files export is available as an option?

---

### Post by barmaley on 2011-03-09
In my version of qtiplot-0.9.8.4, when I'm trying to open opj-file it says:
"This functionality is only available on QtiPlot Pro version, please subscribe for a maintenance contract".

In the free source it is an option, but I never succeeded in compiling the latest version. If someone knows how to compile qtiplot-0.9.8.4, please advice.

---

### Post by barmaley on 2011-03-18
Hi, ubuntu people.
There is a new version of qtiplot - 0.9.8.5
Let's see who will be the 1st to successfully compile it ;b

---

### Post by volfoni54 on 2011-03-19
> **barmaley said:**
> Hi, ubuntu people.
There is a new version of qtiplot - 0.9.8.5
Let's see who will be the 1st to successfully compile it ;b

I did it !

I have updated the French page of compilation of QtiPlot ([http://doc.ubuntu-fr.org/qtiplot](http://doc.ubuntu-fr.org/qtiplot)). 

May be, She is now more simple.

Let me know if you have problem !


Raoul

---

### Post by barmaley on 2011-03-20
Hi, everybody
I have tried to compile the new qtiplot-0.9.8.5 and I got the following error:
cd qtiplot/ && make -f Makefile 
make[1]: Entering directory `/home/casper/QtiPlot_fr/qtiplot-0.9.8.5/qtiplot'
g++ -c -pipe -O2 -D_REENTRANT -Wall -W -DSVN_REVISION="\"\"" -DQT_PLUGIN -DSCRIPTING_MUPARSER -DSCRIPTING_PYTHON -DGL2PS_HAVE_LIBPNG -DTEX_OUTPUT -DHAVE_ALGLIB -DHAVE_TAMUANOVA -DQT_NO_DEBUG -DQT_SVG_LIB -DQT_QT3SUPPORT_LIB -DQT3_SUPPORT -DQT_XML_LIB -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtXml -I/usr/include/qt4/Qt3Support -I/usr/include/qt4/QtSvg -I/usr/include/qt4 -I/usr/include/qt4/QtAssistantClient -I/usr/include/qt4/QtAssistant -I../3rdparty/zlib -I/usr/local/include -I../3rdparty/qwt/src -I../3rdparty/qwtplot3d/include -Iicons -Isrc/analysis -Isrc/analysis/dialogs -Isrc/core -Isrc/excel -Isrc/lib/include -Isrc/lib/3rdparty/qtcolorpicker/src -Isrc/plot2D -Isrc/plot2D/dialogs -Isrc/plot3D -Isrc/matrix -Isrc/table -Isrc/scripting -I/usr/include/python2.6 -I../../../QtiPlotQTeXEngine/src -I../../../../QtiPlot/cpp/src -I../../tamu_anova-0.2 -I/usr/X11R6/include -I/home/casper/QtiPlot_fr/qtiplot-0.9.8.5/tmp/qtiplot -o ../tmp/qtiplot/PythonScripting.o src/scripting/PythonScripting.cpp
src/scripting/PythonScripting.cpp:61: fatal error: sipAPIqti.h: No such file or directory
compilation terminated.
make[1]: *** [../tmp/qtiplot/PythonScripting.o] Error 1
make[1]: Leaving directory `/home/casper/QtiPlot_fr/qtiplot-0.9.8.5/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2

If someone knows how to resolve the error, please, help.

---

### Post by volfoni54 on 2011-03-21
> **barmaley said:**
> 
src/scripting/PythonScripting.cpp:61: fatal error: sipAPIqti.h: No such file or directory
compilation terminated.
make[1]: *** [../tmp/qtiplot/PythonScripting.o] Error 1
make[1]: Leaving directory `/home/casper/QtiPlot_fr/qtiplot-0.9.8.5/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2


The file sipAPIqti.h is in 'qtiplot-0.9.8.5/tmp/qtiplot' directory. I often had this error. I solved it by modifying this line in the build.conf file (at the beginning) :

```
SYS_INCLUDEPATH = -I/$$QTI_ROOT/tmp/qtiplot
```

---

### Post by barmaley on 2011-03-21
Thanks for reply, volfoni54.
I used your build.conf from the very beginning, but the sipAPIqti.h is not in the tmp/qtiplot directory, actually there is no file with h-extension. I have no idea what is wrong.
Any idea?
I used another build.conf (a mixture of what I have for 0.9.8.3 and yours). make worked for quite a while, but then it gave this error:
see attached text

---

### Post by volfoni54 on 2011-03-22
> **barmaley said:**
> Thanks for reply, volfoni54.
I used your build.conf from the very beginning, but the sipAPIqti.h is not in the tmp/qtiplot directory, actually there is no file with h-extension. I have no idea what is wrong.
Any idea?
I used another build.conf (a mixture of what I have for 0.9.8.3 and yours). make worked for quite a while, but then it gave this error:
see attached text

I don't why you didn't had the sipAPIqti.h file. Once, I noticed that a second compilation could bring it.

I think that your new error is due to your version of MuParser or may be you should do a 'make clean' and try again.

Courage (as we say in French).

Raoul
PS : Where are you ? we always have almost 6 hours behind

---

### Post by barmaley on 2011-03-22
Thanks Raoul.
I have compiled it at work - went flawlessly.
Now I have to repeat the same steps at home.

I am in US, east coast. That's why there is a 6 hours time difference.
Thanks a lot for your help.

---

### Post by volfoni54 on 2011-03-22
> **barmaley said:**
> Thanks Raoul.
I have compiled it at work - went flawlessly.
Now I have to repeat the same steps at home.

I am in US, east coast. That's why there is a 6 hours time difference.
Thanks a lot for your help.

Very good !!

In the buikd.conf file, may be the relative paths (../../../etc.) are not exactly the same than yours.

Raoul

---

### Post by barmaley on 2011-03-22
On that french page, there is a typo. In line cd sip-4.11.1 should be sip-4.12.1.

Thanks for your help, Raoul

---

### Post by barmaley on 2011-03-22
This is weird. On my work pc there was no errors, at home I still have errors. Now it is this one:

../tmp/qtiplot/muParserScript.o:muParserScript.cpp:(.text+0x1fb8): more undefined references to `mu::ParserCallback::ParserCallback(double (*)(double, double), bool)' follow
collect2: ld returned 1 exit status
make[1]: *** [qtiplot] Error 1
make[1]: Leaving directory `/home/casper/QtiPlot/qtiplot-0.9.8.5/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2

What the hack?

---

### Post by volfoni54 on 2011-03-22
Are you sure to have a version of MuParser > 1.32 and where is the libmuparser.so ? (in /usr/local/lib ?)

If yes, do a 'make clean' and try to recompile...


Raoul

---

### Post by barmaley on 2011-03-24
It was very weird.
I was not able to install the muparser-1.34 from sources, even though there were no errors during the compilation. So, I installed it from the deb-files. After that make ran without errors too.

sudo make install gave tjis error :
cd manual/ && make -f Makefile install
make[1]: Entering directory `/home/casper/QtiPlot/qtiplot-0.9.8.5/manual'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/casper/QtiPlot/qtiplot-0.9.8.5/manual'
make: *** [sub-manual-install_subtargets] Error 2

But it seems I can run qtiplot by typing qtiplot/qtiplot.
Thanks for your help.

---

### Post by volfoni54 on 2011-03-24
> **barmaley said:**
> It was very weird.
I was not able to install the muparser-1.34 from sources, even though there were no errors during the compilation.


Could you explain why you managed to compile it but you were not able to install it ?
> **barmaley said:**
> 
 So, I installed it from the deb-files. After that make ran without errors too.

sudo make install gave tjis error :
cd manual/ && make -f Makefile install
make[1]: Entering directory `/home/casper/QtiPlot/qtiplot-0.9.8.5/manual'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/casper/QtiPlot/qtiplot-0.9.8.5/manual'
make: *** [sub-manual-install_subtargets] Error 2

But it seems I can run qtiplot by typing qtiplot/qtiplot.
Thanks for your help.
This is normal, there is no istall rule in Makefile.

If you want to install qtiplot, the command line is (in the qtiplot-0.9.8.5 directory):
> sudo make install

---

### Post by barmaley on 2011-03-24
I had to install muparser with the deb-file, then I was able to compile qtiplot.

That error was a result of sudo make install command.

---

### Post by volfoni54 on 2011-05-10
Version 0.9.8.6 is out !

---

### Post by barmaley on 2011-05-11
How to compile qtiplot-0.9.8.6?

I'm sorry for asking the same question version after version, but it becomes more and more complicated to compile newer versions.
Thanks for your help.

---

### Post by volfoni54 on 2011-05-12
> **barmaley said:**
> How to compile qtiplot-0.9.8.6?

I'm sorry for asking the same question version after version, but it becomes more and more complicated to compile newer versions.
Thanks for your help.

This new version will help us to manage to compile Qtiplot :

1. What is your version of Ubuntu ?
2. Have you already installed 'libEMF', 'muParser', 'sip', 'PyQt' ?

Thanks

Raoul

---

### Post by barmaley on 2011-05-15
Hi, ubuntu people.
I have partially compiled qtiplot-0.9.8.6.
Here is a short report:
I followed the web page [http://doc.ubuntu-fr.org/qtiplot](http://doc.ubuntu-fr.org/qtiplot) in order to compile the program. I downloaded and used the latest versions of required libraries, except alglib, only 2.6 worked. Also, the file qtiplot.pro does not contain these line any more:
233 #LIBS        += src/plugins/libQtiPlotdBasePlugin.a
234 #LIBS        += src/plugins/libQtiPlotDatabasePlugin.a                                                                                                   
235 #LIBS        += src/plugins/libQtiPlotCsvPlugin.a
236 #LIBS        += src/plugins/libQtiPlotTexPlugin.a
237 #LIBS        += src/plugins/libQtiPlotOdsPlugin.a
238 #LIBS        += src/plugins/libQtiPlotExcelPlugin.a
239 #LIBS        += src/plugins/libQtiPlotOriginPlugin.a
240 #LIBS        += src/plugins/libQtiPlotEmfExportPlugin.a
241 #LIBS        += ../3rdparty/quazip/lib/libquazip.a
242 #LIBS        += ../3rdparty/EmfEngine/libEmfEngine.a

So there was nothing to comment out.
"qmake" and "make" worked from the first time, but the "sudo make install" gave the following error:
cd manual/ && make -f Makefile install
make[1]: Entering directory `/home/casper/QtiPlot/qtiplot-0.9.8.6/manual'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/casper/QtiPlot/qtiplot-0.9.8.6/manual'
make: *** [sub-manual-install_subtargets] Error 2

In any case, I can run qtiplot/qtiplot - it works, but it does not allow to import OriginLab opj-files.

---

### Post by volfoni54 on 2011-05-17
> **barmaley said:**
> Hi, ubuntu people.
I have partially compiled qtiplot-0.9.8.6.
Here is a short report:
I followed the web page [http://doc.ubuntu-fr.org/qtiplot](http://doc.ubuntu-fr.org/qtiplot) in order to compile the program. I downloaded and used the latest versions of required libraries, except alglib, only 2.6 worked. Also, the file qtiplot.pro does not contain these line any more:
233 #LIBS        += src/plugins/libQtiPlotdBasePlugin.a
234 #LIBS        += src/plugins/libQtiPlotDatabasePlugin.a                                                                                                   
235 #LIBS        += src/plugins/libQtiPlotCsvPlugin.a
236 #LIBS        += src/plugins/libQtiPlotTexPlugin.a
237 #LIBS        += src/plugins/libQtiPlotOdsPlugin.a
238 #LIBS        += src/plugins/libQtiPlotExcelPlugin.a
239 #LIBS        += src/plugins/libQtiPlotOriginPlugin.a
240 #LIBS        += src/plugins/libQtiPlotEmfExportPlugin.a
241 #LIBS        += ../3rdparty/quazip/lib/libquazip.a
242 #LIBS        += ../3rdparty/EmfEngine/libEmfEngine.a

So there was nothing to comment out.
"qmake" and "make" worked from the first time, but the "sudo make install" gave the following error:
cd manual/ && make -f Makefile install
make[1]: Entering directory `/home/casper/QtiPlot/qtiplot-0.9.8.6/manual'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/casper/QtiPlot/qtiplot-0.9.8.6/manual'
make: *** [sub-manual-install_subtargets] Error 2

In any case, I can run qtiplot/qtiplot - it works, but it does not allow to import OriginLab opj-files.

It's a good news !

You can not import OPJ file from the source files. You have to subscribe an maintenance contract...

Raoul

---

### Post by barmaley on 2011-05-17
I could import opj-files in qtiplot-0.9.8.4 and previous versions compiled from the sources.
I don't understand the logic: I'm on my own with the source files, the installation instructions have no use, but, on the other hand, even if I manage to compile the program without "maintenance contract", I'm still limited in options.

---

### Post by volfoni54 on 2011-05-19
> **barmaley said:**
> I could import opj-files in qtiplot-0.9.8.4 and previous versions compiled from the sources.
I don't understand the logic: I'm on my own with the source files, the installation instructions have no use, but, on the other hand, even if I manage to compile the program without "maintenance contract", I'm still limited in options.

Absolutly !

But this is the new politic of QtiPlot team.
Importation of .opj, .xls and .ods files are not allowed from the sources.

---

### Post by volfoni54 on 2011-05-23
> **volfoni54 said:**
> Absolutly !

But this is the new politic of QtiPlot team.
Importation of .opj, .xls and .ods files are not allowed from the sources.

Edit  In the trunk, it seems that the next version will permit the import of Excel and Calc files.

---

### Post by yuri.ulrich on 2011-05-26
There is a way, but it is a serious piece of work: you can edit the source to use the old Excel (import/export) and ODS (import only) plugins and the newest liborigin2 instead of the new jodconverter-plugin system for which the sources are not public available since 0.9.8.4.

The new added features (Database, xlsx support and ods export) are missing, but better than no format support at all as in the official opensource 0.9.8.6. On the other hand (thats useful on windows especially), you don´t need java and openoffice installed to work.

And thanks for the compilation guide, I tried to compile qtiplot on windows for ca. 2 weeks before it was succesful, it was a big help for me...

P.S. I think it shouldn`t be too difficult to rewrite the ODS-import-plugin for XLSX-support (zip-packed and XML-based format too), but I´m unfortunately no programmer to realize such project.

---

### Post by volfoni54 on 2011-06-04
> **yuri.ulrich said:**
> There is a way, but it is a serious piece of work: you can edit the source to use the old Excel (import/export) and ODS (import only) plugins and the newest liborigin2 instead of the new jodconverter-plugin system for which the sources are not public available since 0.9.8.4.

The new added features (Database, xlsx support and ods export) are missing, but better than no format support at all as in the official opensource 0.9.8.6. On the other hand (thats useful on windows especially), you don´t need java and openoffice installed to work.

And thanks for the compilation guide, I tried to compile qtiplot on windows for ca. 2 weeks before it was succesful, it was a big help for me...

P.S. I think it shouldn`t be too difficult to rewrite the ODS-import-plugin for XLSX-support (zip-packed and XML-based format too), but I´m unfortunately no programmer to realize such project.

Hi,

I've updated the french web page for the compilation of QtiPlot under Ubuntu ([QtiPlot page]("http://doc.ubuntu-fr.org/qtiplot")).

Good luck !

Raoul

---

### Post by euzada on 2011-06-06
Hello Raoul,


I applied your method to compile the latest version of qtiplot (0.9.8.6) and it works but I have this problem when I want to install qtiplot (sudo make install):

Thank you for your help,
Elias

make[1]: Leaving directory `/home/euzada/QtiPlot/qtiplot-0.9.8.6/fitPlugins'
cd manual/ && make -f Makefile install
make[1]: Entering directory `/home/euzada/QtiPlot/qtiplot-0.9.8.6/manual'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/euzada/QtiPlot/qtiplot-0.9.8.6/manual'
make: *** [sub-manual-install_subtargets] Error 2

---

### Post by volfoni54 on 2011-06-07
> **euzada said:**
> Hello Raoul,


I applied your method to compile the latest version of qtiplot (0.9.8.6) and it works but I have this problem when I want to install qtiplot (sudo make install):

Thank you for your help,
Elias

make[1]: Leaving directory `/home/euzada/QtiPlot/qtiplot-0.9.8.6/fitPlugins'
cd manual/ && make -f Makefile install
make[1]: Entering directory `/home/euzada/QtiPlot/qtiplot-0.9.8.6/manual'
make[1]: *** No rule to make target `install'.  Stop.
make[1]: Leaving directory `/home/euzada/QtiPlot/qtiplot-0.9.8.6/manual'
make: *** [sub-manual-install_subtargets] Error 2

It seems that the manual cannot be installed.
Have you commented the line #4 of the QTI_ROOT/qtiplot.pro file ?

Thanks

Raoul

---

