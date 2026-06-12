---
title: "compiling amile"
date: 2009-02-28
forum: General Help
---

### Post by StOoZ on 2009-02-28
I know its in the repos , but I need to compile it in this case , I did exactly what they say here :
[http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian]("http://www.amule.org/wiki/index.php/HowTo_Compile_In_Debian")

and this is what I get :
[PHP]rom@linux:~/Downloads/aMule-2.2.3$ ./configure --disable-debug --enable-optimize
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking if this is a FreeBSD 4 or earlier system... no
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for gawk... (cached) gawk
checking for egrep... grep -E
checking whether make sets $(MAKE)... (cached) yes
checking for flex... flex
checking for yywrap in -lfl... yes
checking lex output file root... lex.yy
checking whether yytext is a pointer... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for bison... no
checking for byacc... no
checking for ranlib... (cached) ranlib
checking for strip... strip
checking for ar... ar
checking for ld... ld
checking for zlib >= 1.1.4... yes (version 1.2.3.3)
checking for File::Copy... ok
checking whether we need the GUI... yes
checking for the --with-toolkit option... will be automatically detected
checking for the --with-wxshared option... will be automatically detected
checking for the --with-wxdebug option... will be automatically detected
checking for the --with-wxversion option... will be automatically detected
checking for wx-config... /usr/local/bin/wx-config
checking for wxWidgets version >= 2.8.0 (--unicode=yes)... no
configure: error: 
    The requested wxWidgets build couldn't be found.
    
    The configuration you asked for aMule requires a wxWidgets
    build with the following settings:
        --unicode=yes
    but such build is not available.

    To see the wxWidgets builds available on this system, please use
    'wx-config --list' command. To use the default build, returned by
    'wx-config --selected-config', use the options with their 'auto'
    default values.

    If you still get this error, then check that 'wx-config' is
    in path, the directory where wxWidgets libraries are installed
    (returned by 'wx-config --libs' command) is in LD_LIBRARY_PATH
    or equivalent variable and wxWidgets version is 2.8.0 or above.
[PHP][/PHP][/PHP]

---

### Post by jjgomera on 2009-02-28
you need install the package wx2.8-headers

---

### Post by StOoZ on 2009-02-28
are you sure?
I compiled the whole wx-widgets package , exactly as they mentioned on the source , and its still doesnt work...

---

### Post by jjgomera on 2009-02-28
excuse me, i wanted to say libwxgtk2.8-dev

really, i dont understant why to compile wxwidgets 2.8 when it is in oficial repo, ah, yes, i think this section of howto is for debian etch:

>     *  Debian Etch includes aMule 2.1.3 and wxwidgets 2.6.3 

    * aMule 2.1.x needs wxwidgets 2.6. You cannot compile it with newer versions of wxwidgets.
    * aMule 2.2.x needs wxwidgets 2.8. You cannot compile it with older versions of wxwidgets. 

Well, never mind, do you compile wxwidgets successfully, including instalation:

 # make install
 # ldconfig

---

