---
title: "xbmc, where did it install to, how do i open the program?"
date: 2009-06-13
forum: General Help
---

### Post by xfearxnxloathing on 2009-06-13
this is prob very noobish but i just installed xbmc via terminal, rebooted and now im looking for the program so i can check it out.  i dont see it under Sound and Video or anything and i also tried typing in the command terminal "xbmc", nothing happened..  please help

---

### Post by ellgor on 2009-06-13
HI,

Try using sudo xbmc, its sometimes a security thing.

Regards, Ellgor.

---

### Post by xfearxnxloathing on 2009-06-18
apparently its not installed..  yet is why, i get this error when i do ```
./configure
```

```
~/XBMC$ ./configure
configure: Ensuring config.guess and config.sub exist and is executable
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ccache... none
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for gawk... no
checking for mawk... mawk
checking whether ln -s works... yes
checking whether make sets $(MAKE)... yes
checking how to run the C++ preprocessor... g++ -E
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
checking boost/shared_ptr.hpp usability... no
checking boost/shared_ptr.hpp presence... no
checking for boost/shared_ptr.hpp... no
configure: error: Could not find a required library. Please see the README for your platform.
```

anyone have any idea?

---

### Post by mixmaster on 2009-06-18
You appear to be trying to build and install the source code without some necessary pre-requisite software.  This can be a pain.

Unless you really want to do a source-code build this link 
[http://xbmc.org/forum/showthread.php?t=33327](http://xbmc.org/forum/showthread.php?t=33327)
should tell you how to set up your repositories to download and install precompiled binaries.

---

### Post by xfearxnxloathing on 2009-06-18
i added their site to sourcelists and got the key for it.  how do i download and install xbmc an easy way then?

---

### Post by Mack1 on 2009-06-21
This worked perfectly for me on ubuntu 9.04, 3 mins install in total:

add this key via the terminal:
gpg --no-default-keyring --keyring /tmp/tmp.keyring --keyserver keyserver.ubuntu.com --recv 91E7EE5E && gpg --no-default-keyring --keyring /tmp/tmp.keyring --export --armor 91E7EE5E | sudo apt-key add - && rm /tmp/tmp.keyring

type in terminal:
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

Go to third parties software and click add, type this in:
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) jaunty main

(for hardy type in hardy in stead of jaunty)

Click close, click reload

in terminal type:
Sudo apt-get install xbmc

eh voila, done!

You can start xbmc through the ubuntu menu under video or:
xbmc in terminal

have fun!
Mack1 is online now Report Post   	Edit/Delete Message

---

### Post by xfearxnxloathing on 2009-06-25
> **Mack1 said:**
> This worked perfectly for me on ubuntu 9.04, 3 mins install in total:

add this key via the terminal:
gpg --no-default-keyring --keyring /tmp/tmp.keyring --keyserver keyserver.ubuntu.com --recv 91E7EE5E && gpg --no-default-keyring --keyring /tmp/tmp.keyring --export --armor 91E7EE5E | sudo apt-key add - && rm /tmp/tmp.keyring

type in terminal:
gksu --desktop /usr/share/applications/software-properties.desktop /usr/bin/software-properties-gtk

Go to third parties software and click add, type this in:
deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) jaunty main

(for hardy type in hardy in stead of jaunty)

Click close, click reload

in terminal type:
Sudo apt-get install xbmc

eh voila, done!

You can start xbmc through the ubuntu menu under video or:
xbmc in terminal

have fun!
Mack1 is online now Report Post   	Edit/Delete Message

worked like a charm!  =]

thnx!!

---

### Post by jake16424 on 2009-06-26
> **xfearxnxloathing said:**
> apparently its not installed..  yet is why, i get this error when i do ```
./configure
```

```
~/XBMC$ ./configure
configure: Ensuring config.guess and config.sub exist and is executable
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ccache... none
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for gawk... no
checking for mawk... mawk
checking whether ln -s works... yes
checking whether make sets $(MAKE)... yes
checking how to run the C++ preprocessor... g++ -E
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
checking boost/shared_ptr.hpp usability... no
checking boost/shared_ptr.hpp presence... no
checking for boost/shared_ptr.hpp... no
configure: error: Could not find a required library. Please see the README for your platform.
```

anyone have any idea?

looks like something got missed when you installed the first time, try uninstall , reinstall? or make certain you have all the packets needed

---

