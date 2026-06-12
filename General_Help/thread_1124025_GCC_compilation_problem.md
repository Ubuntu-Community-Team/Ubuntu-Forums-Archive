---
title: "GCC compilation problem"
date: 2009-04-12
forum: General Help
---

### Post by jrober04 on 2009-04-12
Hey everyone,

I am relatively new to ubuntu and am trying to install Maq sequence alignment program and I have run into a snag.  I try to run ./configure and i end up with an error that it can't find ANSI C header files...and make then fails.  I can't figure out was is wrong with it.  Any help would be greatly appreciated.

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking if gcc accepts -m64... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... no
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged

---

### Post by soltanis on 2009-04-12
Have you installed build-essential?

```

sudo apt-get install build-essential

```

---

### Post by jrober04 on 2009-04-12
yes i have it installed and it is the newest version

---

### Post by soltanis on 2009-04-12
Nothing seems to be wrong with the output of the ./configure session you posted. Do you get the error when you run make?

Type this into a text editor and save the file as "test.c" without the quotes:

```

#include <stdio.h>

void main()
{
        printf("standard c library works\n");
}

```

Then, cd to the directory where you saved the file and run

```

gcc test.c
./a.out

# you should see
standard c library works

```

Post back if you get a compilation error, and please post the output of where you got the error.

---

### Post by jrober04 on 2009-04-13
The test showed that the standard c library worked but running make on maq shows:

james@james-laptop:~/Desktop/maq-0.7.1$ make
make  all-am
make[1]: Entering directory `/home/james/Desktop/maq-0.7.1'
g++  -Wall -m64 -D_FASTMAP -DMAQ_LONGREADS -g -O2   -o maq main.o const.o seq.o bfa.o read.o fasta2bfa.o fastq2bfq.o merge.o match_aux.o match.o sort_mapping.o assemble.o pileup.o mapcheck.o get_pos.o assopt.o aux_utils.o rbcc.o subsnp.o pair_stat.o indel_soa.o maqmap.o maqmap_conv.o altchr.o submap.o rmdup.o simulate.o genran.o indel_pe.o stdaln.o indel_call.o eland2maq.o csmap2ntmap.o break_pair.o glfgen.o -lm -lz 
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.3.2/../../../libz.so when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/gcc/i486-linux-gnu/4.3.2/../../../libz.a when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/libz.so when searching for -lz
/usr/bin/ld: skipping incompatible /usr/lib/libz.a when searching for -lz
/usr/bin/ld: cannot find -lz
collect2: ld returned 1 exit status
make[1]: *** [maq] Error 1
make[1]: Leaving directory `/home/james/Desktop/maq-0.7.1'
make: *** [all] Error 2

---

### Post by soltanis on 2009-04-13
You need to install zlib.

```

sudo apt-get install zlib1g-dev

```

---

### Post by jrober04 on 2009-04-13
I originally thought that was the issue too, but i have zlib installed and it is the newest version

---

### Post by mc4man on 2009-04-13
You may want to post what release of ubuntu your using (Intrepid, jaunty) and whether 32 or 64 bit

maq is available in ubuntu for the first time in jaunty, so there may be some problems building in intrepid (particularly 32 bit

The jaunty 0.7.1-1 package should install into intrepid without any issues, how well it runs I wouldn't know (though no harm in your trying

[http://packages.ubuntu.com/jaunty/maq](http://packages.ubuntu.com/jaunty/maq)

---

### Post by soltanis on 2009-04-13
Might be a 32/64 bit compatibility problem. Perhaps if you build zlib yourself, it will solve the problem of incompatible libraries.

---

### Post by jrober04 on 2009-04-13
Thanks for all the help,

by using jaunty, I was able to install maq but the program TopHat that will align spliced reads using Bowtie is reading compilation errors too.I am using a 32 bit machine and the program is supposed to work on both platforms.

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for gawk... (cached) gawk
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for ar... ar
checking for perl... /usr/bin/perl
checking for bash... /bin/bash
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking if gcc accepts -m64... yes
checking for gzread in -lz... no
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... no
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for int32_t... yes
checking for size_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for uint8_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... no
checking for memset... yes
checking for strdup... yes
checking for strrchr... yes
checking for strtol... yes
checking for strsep... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

-- TopHat 0.8.3 Configuration Results --
  C compiler:          gcc -Wall -g3 -m64 -O3   -DNDEBUG
  C++ compiler:        g++ -Wall -g3 -m64 -O3   -DNDEBUG
  GCC version:         gcc (Ubuntu 4.3.2-1ubuntu12) 4.3.2
  Host System type:    i686-pc-linux-gnu
  Install prefix:      /usr/bin
  Install eprefix:     ${prefix}

  See config.h for further configuration information.
  Email <cole@cs.umd.edu> with questions and bug reports.


make then gives these errors:
james@james-laptop:~/Desktop/tophat-0.8.3$ make
make  all-recursive
make[1]: Entering directory `/home/james/Desktop/tophat-0.8.3'
Making all in src
make[2]: Entering directory `/home/james/Desktop/tophat-0.8.3/src'
g++ -DHAVE_CONFIG_H -I. -I..    -Wall -g3 -m64 -O3   -DNDEBUG -I./SeqAn-1.1 -Wall -g3 -m64 -O3   -DNDEBUG -MT reads.o -MD -MP -MF .deps/reads.Tpo -c -o reads.o reads.cpp
In file included from /usr/include/c++/4.3/bits/stl_algo.h:65,
                 from /usr/include/c++/4.3/algorithm:67,
                 from ./SeqAn-1.1/seqan/basic.h:38,
                 from ./SeqAn-1.1/seqan/sequence.h:27,
                 from bwt_map.h:14,
                 from reads.cpp:18:
/usr/include/c++/4.3/cstdlib:124: error: ‘::malloc’ has not been declared
In file included from ./SeqAn-1.1/seqan/basic.h:52,
                 from ./SeqAn-1.1/seqan/sequence.h:27,
                 from bwt_map.h:14,
                 from reads.cpp:18:
./SeqAn-1.1/seqan/basic/basic_profile.h: In function ‘void* _proMalloc(size_t)’:
./SeqAn-1.1/seqan/basic/basic_profile.h:484: error: ‘malloc’ was not declared in this scope
In file included from ./SeqAn-1.1/seqan/sequence.h:62,
                 from bwt_map.h:14,
                 from reads.cpp:18:
./SeqAn-1.1/seqan/sequence/sequence_multiple.h: In function ‘typename seqan::Size<seqan::String<TValue, TSpec> >::Type seqan::_findIthNonZeroValue(const seqan::String<TValue, TSpec>&, TPos)’:
./SeqAn-1.1/seqan/sequence/sequence_multiple.h:995: warning: suggest explicit braces to avoid ambiguous ‘else’
make[2]: *** [reads.o] Error 1
make[2]: Leaving directory `/home/james/Desktop/tophat-0.8.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/james/Desktop/tophat-0.8.3'
make: *** [all] Error 2


thanks for all your help so far

---

### Post by jrober04 on 2009-04-13
I thought I should clarify that maq is a neccessary program for bowtie and tophat programs to run. I followed the instructions using jaunty to install maq but now tophat wont compile properly

---

### Post by sb9002 on 2009-10-16
Hi jrober04,

I am running into the same problem on a jaunty box when trying to install tophat. i was wondering if you were able to come up with a workaround solution for this. It would be great to get some tips from you on that.

Thanks.

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gawk... no
checking for mawk... mawk
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for ar... ar
checking for perl... /usr/bin/perl
checking for bash... /bin/bash
checking for a Python interpreter with version >= 2.4... python
checking for python... /usr/bin/python
checking for python version... 2.6
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.6/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.6/site-packages
checking if gcc accepts -m64... yes
checking for gzread in -lz... no
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... no
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for int32_t... yes
checking for size_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for uint8_t... yes
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... no
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... no
checking for memset... no
checking for strdup... no
checking for strrchr... no
checking for strtol... no
checking for strsep... no
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking dependency style of g++... gcc3
configure: creating ./config.status
config.status: creating Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

-- TopHat 1.0.11 Configuration Results --
  C compiler:          gcc -Wall -g -m64 -O3  -DNDEBUG
  C++ compiler:        g++ -Wall -g -m64 -O3  -DNDEBUG
  GCC version:         gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3
  Host System type:    i686-pc-linux-gnu
  Install prefix:      /home/work/software/tophat-1.0.11
  Install eprefix:     ${prefix}

---

