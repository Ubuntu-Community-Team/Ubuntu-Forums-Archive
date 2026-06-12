---
title: "Newbie troubles attempting to install Wally Version 1.3.2"
date: 2008-12-05
forum: General Help
---

### Post by rockophonic on 2008-12-05
I am a newbie trying to install Wally Version 1.3.2.  I just picked up my first copy of "Linux Format" magazine, and came across the Wally Desktop image changer. So, I'm really wanting to install this, but after reading the instructions and attempting the install I'm running into problems.

The instructions say that I have to use Qt tools to build this (this is my first attempt at making a build by the way).  So I went into the synaptics package manager; found qt4-qtconfig and installed; found qt4-dev-tools and installed; found qt4-designer and installed; and i installed qt4-doc.

I also have all the libqt4 libraries installed.

I also read and made sure that I installed libexif12 and libexif-dev.

Next, the instructions read:
"In the main directory just type (as root):

qmake

make

make install


When I type in qmake I get:

me@me-desktop:/root$ qmake
Usage: qmake [mode] [options] [files]

QMake has two modes, one mode for generating project files based on
some heuristics, and the other for generating makefiles. Normally you
shouldn't need to specify a mode, as makefile generation is the default
mode for qmake, but you may use this to test qmake on an existing project

Mode:
  -project       Put qmake into project file generation mode
                 In this mode qmake interprets files as files to
                 be built,
                 defaults to *.c; *.ui; *.y; *.l; *.ts; *.qrc; *.h; *.hpp; *.hh; *.hxx; *.H; *.cpp; *.cc; *.cxx; *.C
  -makefile      Put qmake into makefile generation mode (default)
                 In this mode qmake interprets files as project files to
                 be processed, if skipped qmake will try to find a project
                 file in your current working directory

Warnings Options:
  -Wnone         Turn off all warnings
  -Wall          Turn on all warnings
  -Wparser       Turn on parser warnings
  -Wlogic        Turn on logic warnings

Options:
   * You can place any variable assignment in options and it will be     *
   * processed as if it was in [files]. These assignments will be parsed *
   * before [files].                                                     *
  -o file        Write output to file
  -unix          Run in unix mode
  -win32         Run in win32 mode
  -macx          Run in Mac OS X mode
  -d             Increase debug level
  -t templ       Overrides TEMPLATE as templ
  -tp prefix     Overrides TEMPLATE so that prefix is prefixed into the value
  -help          This help
  -v             Version information
  -after         All variable assignments after this will be
                 parsed after [files]
  -norecursive   Don't do a recursive search
  -recursive     Do a recursive search
  -cache file    Use file as cache           [makefile mode only]
  -spec spec     Use spec as QMAKESPEC       [makefile mode only]
  -nocache       Don't use a cache file      [makefile mode only]
  -nodepend      Don't generate dependencies [makefile mode only]
  -nomoc         Don't generate moc targets  [makefile mode only]
  -nopwd         Don't look for files in pwd [project mode only]


And when I type make I get:

me@me-desktop:/root$ make
make: *** No targets specified and no makefile found.  Stop.


Can't get past this.  
I would really like to be able to install this.  Any help would be greatly appreciated.

:D

---

### Post by jcm4 on 2008-12-31
Having the same problem, bump.

---

