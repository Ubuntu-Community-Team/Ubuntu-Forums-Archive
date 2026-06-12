---
title: "Compiling frin source"
date: 2006-10-01
forum: Desktop Environments
---

### Post by RudolfMDLT on 2006-10-01
I have been using Ubuntu now for about 6 months and today thought I'd try something new, compiling from source.

I have read up a little on this but for some reason it just won't work with the programs and themes that I have downloaded. as far as I know:

Un-Tar the source code
Set your home directory to the directory containing the make file
then type in 

configure

make

Sudo make install

configure doesn't work, so I used sh configure to run it as a script.


Here is what happened and some error messages.
[PHP]
rudolf@rudolf:~/Desktop/QtCurve-KDE3-0.43.20$ sh configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
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
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking whether g++ supports -Wmissing-format-attribute... no
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... no
checking whether g++ supports -Wno-long-long... no
checking whether g++ supports -Wnon-virtual-dtor... no
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
rudolf@rudolf:~/Desktop/QtCurve-KDE3-0.43.20$ make
make: *** No targets specified and no makefile found.  Stop.
rudolf@rudolf:~/Desktop/QtCurve-KDE3-0.43.20$ sudo make install
Password:
make: *** No rule to make target `install'.  Stop.

[/PHP]

Any help will be appreciated,

Thanks

---

### Post by lagagnon on 2006-10-01
When you run a script from within a directory you should use ./ in fron of the name, eg: ./configure .

But your main problem is you do not have the gcc development environment installed (it does not come pre-loaded with Ubuntu by default). Do this:

sudo apt-get install build-essential

---

### Post by RudolfMDLT on 2006-10-02
Thanks! - This sorted it out!

---

