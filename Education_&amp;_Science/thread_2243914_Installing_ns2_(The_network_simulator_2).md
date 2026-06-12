---
title: "Installing ns2 (The network simulator 2)"
date: 2014-09-12
forum: Education &amp; Science
---

### Post by capslock4 on 2014-09-12
Hi everybody!
I am trying to install ns2 to support for my study but I got into some of the problems while installing the *nam* package.
Firstly, I run *./install* in ns-allinone-2.35 folder. It has seemed to be install success with the notifications:

```
ln: failed to create symbolic link &#8216;ns&#8217;: File exists
Please compile your nam separately.
ln: failed to create symbolic link &#8216;xgraph&#8217;: File exists
ln: failed to create symbolic link &#8216;sgb2ns&#8217;: File exists
ln: failed to create symbolic link &#8216;sgb2hierns&#8217;: File exists
ln: failed to create symbolic link &#8216;sgb2comns&#8217;: File exists
ln: failed to create symbolic link &#8216;itm&#8217;: File exists
ln: failed to create symbolic link &#8216;sgb2alt&#8217;: File exists
ln: failed to create symbolic link &#8216;edriver&#8217;: File exists

```

Then I try to run *./configure --with-tcl=./tcl* in nam-1.35 folder but I encountered an error:
```
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
No .configure file found in current directory
Continuing with default options...
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for ANSI C header files... (cached) yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for string.h... (cached) yes
checking for main in -lXbsd... no
checking for socket in -lsocket... no
checking for gethostbyname in -lnsl... yes
checking for dcgettext in -lintl... no
checking for getnodebyname in -ldnet_stub... no
checking that g++ can handle -O2... yes
checking for zlib.h... no
checking for libz1.2.3... no
checking for X11 header files
checking for X11 library archive
checking for XOpenDisplay in -lX11... yes
checking for XShmAttach in -lXext... no
warning: compiling without -lXext
checking for tcl.h... no
checking for tclInt.h... no
checking for libtcl8.6... no
checking for init.tcl... no
checking for http.tcl... no
**checking Tcl http.tcl library... configure: error: Couldn't find http.tcl in **      /http     /http2.5     /http2.4     /http2.3     /http2.1     /http2.0     /http1.0     
```
I found this link [http://ubuntuforums.org/archive/index.php/t-803445.html](http://ubuntuforums.org/archive/index.php/t-803445.html) and follow to do but the package hasn't still installed yet. 
Please help me to solve my issues.
Thanks in advance.

---

### Post by Lars Noodén on 2014-09-12
Have you looked at gns3?  It is in the repository and can be installed with a click or two.  If that does the job then you won't need to struggle with a manual installation.

---

### Post by capslock4 on 2014-09-12
@Lars Noodén 
thank you for your recommendation, I'll try to discover gns3 too.
However, my professor requests us using ns2 to practise some mini projects. Therefore I am happy to install both ns2 and gns3 on my computer.
:)

---

### Post by capslock4 on 2014-09-12
My problem has been solved when I found this link. I hope it useful for everyone gets into the same problem. :D
[http://forums.techarena.in/operating-systems/1127458.htm](http://forums.techarena.in/operating-systems/1127458.htm)

> 
This is the problem with nam file .NAM is not installed correctly
you have to correct it
Goto ns-allinone-2.34/nam-1.14
then open Xwd.c file
there delete the header file #include <X11/Xmu/WinUtil.h>
save the file.
goto command prompt n(or terminal ) and move to  /ns-allinone-2.34/nam-1.14
$ sudo make
then only nam-1.14 will be installed and nam.exe will be appear
 
then move to /ns-allinone-2.34/bin
 
create link for nam 
 
$ ln -s $CUR_PATH/nam-$NAMVER/nam${EXE} nam${EXE}
 
Now it will work

---

