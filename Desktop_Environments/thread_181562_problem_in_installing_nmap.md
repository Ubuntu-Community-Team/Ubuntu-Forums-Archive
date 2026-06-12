---
title: "problem in installing nmap"
date: 2006-05-24
forum: Desktop Environments
---

### Post by networkPlaces on 2006-05-24
when i run the configure from the shell or consule whtever u call it, it displays an error, which is given below. i have anjuta IDE installed, which i suppose must have a compiler. can anyone tell me how to solve this problem 


checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
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
checking for g++... MISSING
configure: error: Could not locate a C++ compiler. If it exists, add it to yourPATH or give configure the CXX=path_to_compiler argument.  Otherwise, install aC++ compiler such as g++ or install a binary package of Nmap (see [http://www.insecure.org/nmap/nmap_download.html](http://www.insecure.org/nmap/nmap_download.html) ))

---

### Post by i++ on 2006-05-24
what version of ubuntu are you running? just do
```
sudo apt-get install g++
```

or open your synaptic and install g++-4.0

:) 

i++

---

### Post by networkPlaces on 2006-05-24
i am new to linux, sorry for the trouble, compiler problem was solved, thank you, but now there is another problem (problem in installing nmap on ubuntu 5.10 i think).

when i run the "configure" command it completes its execution and then the "make" command  says no such file or directory, i have also tried "./make" but same result. The configure command finishes with this 

*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the*** exact error that occured. This usually means GTK+ is incorrectly installed.configure: WARNING: NMAPFE WILL NOT BE BUILT -- BUT NMAP SHOULD STILL WORK
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
configure: creating ./config.status
config.status: creating Makefile... and then a dragon appears :-).

i've extracted some of the erros from the config.log, if some one is interested



conftest.c:2: error: syntax error before 'me'
configure:2150: $? = 1
configure: failed program was:
| #ifndef __cplusplus
|   choke me
| #endif

conftest.c:29:24: error: sys/sockio.h: No such file or directory
conftest.c:29:21: error: bstring.h: No such file or directory
conftest.c:41:25: error: openssl/ssl.h: No such file or directory
conftest.c:75:18: error: pcap.h: No such file or directory

conftest.c:75:18: error: pcre.h: No such file or directory

conftest.c:48: error: 'struct sockaddr' has no member named 'sa_len'
configure:6620: $? = 1
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #ifdef __cplusplus
| extern "C" void std::exit (int) throw (); using std::exit;
| #endif

---

### Post by i++ on 2006-05-24
thats okay, we all learn somehow!

try typing the following in the terminal ```
sudo apt-get install nmap
```

Or go System>Administration>Synaptic Package Manager  and scroll down to nmap, select it and click apply 

:) hope this helps

---

### Post by networkPlaces on 2006-05-24
Done thank you

---

