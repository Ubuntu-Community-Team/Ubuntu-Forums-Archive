---
title: "Chess engine Crafty compile help"
date: 2010-05-26
forum: Gaming &amp; Leisure
---

### Post by Emperor045 on 2010-05-26
Hi there. I'm trying to compile Crafty, a chess engine, in Ubuntu, but  it keeps failing. The output is as following when giving the command  "make linux"

   
                                                 make target=LINUX \
        CC=gcc CXX=g++ \
        CFLAGS='-pg -Wall -pipe' \
        CXFLAGS='' \
        LDFLAGS=' -pg -lstdc++ -lpthread' \
        opt=' -DTRACE -DINLINE64 -DCPUS=2' \
        crafty-make
make[1]: Map '/home/darryl/Downloads/crafty-23.2.2' wordt binnengegaan
make[2]: Map '/home/darryl/Downloads/crafty-23.2.2' wordt binnengegaan
gcc -pg -Wall -pipe -DTRACE -DINLINE64 -DCPUS=2 -DLINUX -c crafty.c
In file included from crafty.c:29:
book.c: In function &#8216;BookUp&#8217;:
book.c:1146: warning: format not a string literal and no format  arguments
In file included from crafty.c:45:
option.c: In function &#8216;Option&#8217;:
option.c:1756: warning: format &#8216;%lld&#8217; expects type &#8216;long long int&#8217;, but  argument 3 has type &#8216;size_t&#8217;
option.c:1759: warning: format &#8216;%lld&#8217; expects type &#8216;long long int&#8217;, but  argument 3 has type &#8216;size_t&#8217;
inline64.h: Assembler messages:
inline64.h:11: Error: suffix or operands invalid for `bsr'
inline64.h:13: Error: suffix or operands invalid for `movq'
inline64.h:24: Error: suffix or operands invalid for `bsf'
inline64.h:26: Error: suffix or operands invalid for `movq'
inline64.h:49: Error: suffix or operands invalid for `xor'
inline64.h:50: Error: suffix or operands invalid for `test'
inline64.h:52: Error: suffix or operands invalid for `lea'
inline64.h:53: Error: suffix or operands invalid for `inc'
inline64.h:54: Error: suffix or operands invalid for `and'
make[2]: *** [crafty.o] Fout 1
make[2]: Map '/home/darryl/Downloads/crafty-23.2.2' wordt verlaten
make[1]: *** [crafty-make] Fout 2
make[1]: Map '/home/darryl/Downloads/crafty-23.2.2' wordt verlaten
make: *** [linux] Fout 2
darryl@darrylm1:~/Downloads/crafty-23.2.2$ ^C
darryl@darrylm1:~/Downloads/crafty-23.2.2$ ^C
darryl@darrylm1:~/Downloads/crafty-23.2.2$  

                               
I've already installed the compile build essentials which was part  of gcc, so that's not the problem. Anyone?

---

