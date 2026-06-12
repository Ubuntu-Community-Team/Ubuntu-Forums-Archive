---
title: "Help needed to run xmgls (radware) un ubuntu."
date: 2010-08-21
forum: Education &amp; Science
---

### Post by gudwindavids on 2010-08-21
Hi everyone, I am new to the site so my greetings go to all the members.
I have been using ubuntu now for about 1 month beforehand I used scientific linux, which I found to be very awkward when it came to wireless compatibility and I also found  yum  to be very poor when compared to apt, Anyway I will get to the main point of the post. I need to analyse data using the program Radware link given below

[http://radware.phy.ornl.gov/download.html](http://radware.phy.ornl.gov/download.html)      ----   > [rw01.0.9.zip]("ftp://radware.phy.ornl.gov/pub/radware/vms/rw01_0_9.zip") (1.2MB)
                                               [Linux motif static-linked programs.]("ftp://radware.phy.ornl.gov/pub/radware/linux/rw01.1.0.static.tgz") (3MB)
                                               [README]("ftp://radware.phy.ornl.gov/pub/radware/unix/README") file for Unix
And I think you need these to compile in ubuntu

lesstif2
lesstif2-dev
libreadline5
libreadline5-dev
readline-common

Then go to src directory and then cp Makefile.linux Makefile
edit the Makefile so that 
 
INSTALL_DIR = ${HOME}/rw_current
        INSTALL = /usr/bin/install 
    INSTALL_BIN = /usr/bin/install

or whatever you wish.
Ok then 

make all
make install

and it should all compile. 
This is fine and I can run the program gf3 and all other programs that don't use the .gls files. However when I use xmlev or xmgls and try to load in the demo.gls file ( in demo directory) I get the following error message

ERROR - cannot open file font.dat
 -- Check that the environment variable or logical name
     RADWARE_FONT_LOC is properly defined, and that the file
     font.dat exists in the directory to which it points.

I have tried editing the hidden files .radware.bashrc and .radwarerc to point towards the /font directory in which the error points out but it still does not work.
Also when I try to run xmlev or xm4dg  I get the following error which I do not fully understand. 

gudwin@ubuntu:~/rw_current/bin$ xmlev
Trying to create pixmap of size 600 by 500
*** buffer overflow detected ***: xmlev terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f745d9305f7]
/lib/libc.so.6[0x7f745d92f5a0]
xmlev[0x40b904]
xmlev[0x405d5a]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f745d857abd]
xmlev[0x403619]
======= Memory map: ========
00400000-00450000 r-xp 00000000 07:00 206258                             /usr/local/bin/xmlev
0064f000-00650000 r--p 0004f000 07:00 206258                             /usr/local/bin/xmlev
00650000-00652000 rw-p 00050000 07:00 206258                             /usr/local/bin/xmlev
00652000-01a3a000 rw-p 00000000 00:00 0 
03910000-039a7000 rw-p 00000000 00:00 0                                  [heap]
7f745c1b7000-7f745c1cd000 r-xp 00000000 07:00 11044                      /lib/libgcc_s.so.1
7f745c1cd000-7f745c3cc000 ---p 00016000 07:00 11044                      /lib/libgcc_s.so.1
7f745c3cc000-7f745c3cd000 r--p 00015000 07:00 11044                      /lib/libgcc_s.so.1
7f745c3cd000-7f745c3ce000 rw-p 00016000 07:00 11044                      /lib/libgcc_s.so.1
7f745c3ce000-7f745c3d3000 r-xp 00000000 07:00 7844                       /usr/lib/libXfixes.so.3.1.0
7f745c3d3000-7f745c5d2000 ---p 00005000 07:00 7844                       /usr/lib/libXfixes.so.3.1.0
7f745c5d2000-7f745c5d3000 r--p 00004000 07:00 7844                       /usr/lib/libXfixes.so.3.1.0
7f745c5d3000-7f745c5d4000 rw-p 00005000 07:00 7844                       /usr/lib/libXfixes.so.3.1.0
7f745c5d4000-7f745c5dd000 r-xp 00000000 07:00 7864                       /usr/lib/libXrender.so.1.3.0
7f745c5dd000-7f745c7dc000 ---p 00009000 07:00 7864                       /usr/lib/libXrender.so.1.3.0
7f745c7dc000-7f745c7dd000 r--p 00008000 07:00 7864                       /usr/lib/libXrender.so.1.3.0
7f745c7dd000-7f745c7de000 rw-p 00009000 07:00 7864                       /usr/lib/libXrender.so.1.3.0
7f745c7de000-7f745c7e7000 r-xp 00000000 07:00 7836                       /usr/lib/libXcursor.so.1.0.2
7f745c7e7000-7f745c9e6000 ---p 00009000 07:00 7836                       /usr/lib/libXcursor.so.1.0.2
7f745c9e6000-7f745c9e7000 r--p 00008000 07:00 7836                       /usr/lib/libXcursor.so.1.0.2
7f745c9e7000-7f745c9e8000 rw-p 00009000 07:00 7836                       /usr/lib/libXcursor.so.1.0.2
7f745c9e8000-7f745c9ed000 r-xp 00000000 07:00 7840                       /usr/lib/libXdmcp.so.6.0.0
7f745c9ed000-7f745cbec000 ---p 00005000 07:00 7840                       /usr/lib/libXdmcp.so.6.0.0
7f745cbec000-7f745cbed000 rw-p 00004000 07:00 7840                       /usr/lib/libXdmcp.so.6.0.0
7f745cbed000-7f745cbf0000 r-xp 00000000 07:00 1769                       /lib/libuuid.so.1.3.0
7f745cbf0000-7f745cdf0000 ---p 00003000 07:00 1769                       /lib/libuuid.so.1.3.0
7f745cdf0000-7f745cdf1000 r--p 00003000 07:00 1769                       /lib/libuuid.so.1.3.0
7f745cdf1000-7f745cdf2000 rw-p 00004000 07:00 1769                       /lib/libuuid.so.1.3.0
7f745cdf2000-7f745cdf4000 r-xp 00000000 07:00 1662                       /lib/libdl-2.10.1.so
7f745cdf4000-7f745cff4000 ---p 00002000 07:00 1662                       /lib/libdl-2.10.1.so
7f745cff4000-7f745cff5000 r--p 00002000 07:00 1662                       /lib/libdl-2.10.1.so
7f745cff5000-7f745cff6000 rw-p 00003000 07:00 1662                       /lib/libdl-2.10.1.so
7f745cff6000-7f745d011000 r-xp 00000000 07:00 8862                       /usr/lib/libxcb.so.1.1.0
7f745d011000-7f745d210000 ---p 0001b000 07:00 8862                       /usr/lib/libxcb.so.1.1.0
7f745d210000-7f745d211000 r--p 0001a000 07:00 8862                       /usr/lib/libxcb.so.1.1.0
7f745d211000-7f745d212000 rw-p 0001b000 07:00 8862                       /usr/lib/libxcb.so.1.1.0
7f745d212000-7f745d214000 r-xp 00000000 07:00 7829                       /usr/lib/libXau.so.6.0.0
7f745d214000-7f745d413000 ---p 00002000 07:00 7829                       /usr/lib/libXau.so.6.0.0
7f745d413000-7f745d414000 r--p 00001000 07:00 7829                       /usr/lib/libXau.so.6.0.0
7f745d414000-7f745d415000 rw-p 00002000 07:00 7829                       /usr/lib/libXau.so.6.0.0
7f745d415000-7f745d42c000 r-xp 00000000 07:00 7792                       /usr/lib/libICE.so.6.3.0
7f745d42c000-7f745d62b000 ---p 00017000 07:00 7792                       /usr/lib/libICE.so.6.3.0
7f745d62b000-7f745d62c000 r--p 00016000 07:00 7792                       /usr/lib/libICE.so.6.3.0
7f745d62c000-7f745d62d000 rw-p 00017000 07:00 7792                       /usr/lib/libICE.so.6.3.0
7f745d62d000-7f745d630000 rw-p 00000000 00:00 0 
7f745d630000-7f745d638000 r-xp 00000000 07:00 7821                       /usr/lib/libSM.so.6.0.0
7f745d638000-7f745d837000 ---p 00008000 07:00 7821                       /usr/lib/libSM.so.6.0.0
7f745d837000-7f745d838000 r--p 00007000 07:00 7821                       /usr/lib/libSM.so.6.0.0
7f745d838000-7f745d839000 rw-p 00008000 07:00 7821                       /usr/lib/libSM.so.6.0.0
7f745d839000-7f745d99f000 r-xp 00000000 07:00 1648                       /lib/libc-2.10.1.so
7f745d99f000-7f745db9e000 ---p 00166000 07:00 1648                       /lib/libc-2.10.1.so
7f745db9e000-7f745dba2000 r--p 00165000 07:00 1648                       /lib/libc-2.10.1.so
7f745dba2000-7f745dba3000 rw-p 00169000 07:00 1648                       /lib/libc-2.10.1.so
7f745dba3000-7f745dba8000 rw-p 00000000 00:00 0 
7f745dba8000-7f745dbe6000 r-xp 00000000 07:00 1694                       /lib/libncurses.so.5.7
7f745dbe6000-7f745dde6000 ---p 0003e000 07:00 1694                       /lib/libncurses.so.5.7
7f745dde6000-7f745ddea000 r--p 0003e000 07:00 1694                       /lib/libncurses.so.5.7
7f745ddea000-7f745ddeb000 rw-p 00042000 07:00 1694                       /lib/libncurses.so.5.7
7f745ddeb000-7f745de21000 r-xp 00000000 07:00 8314                       /lib/libreadline.so.5.2
7f745de21000-7f745e020000 ---p 00036000 07:00 8314                       /lib/libreadline.so.5.2
7f745e020000-7f745e022000 r--p 00035000 07:00 8314                       /lib/libreadline.so.5.2
7f745e022000-7f745e028000 rw-p 00037000 07:00 8314                       /lib/libreadline.so.5.2
7f745e028000-7f745e029000 rw-p 00000000 00:00 0 
7f745e029000-7f745e0ab000 r-xp 00000000 07:00 1690                       /lib/libm-2.10.1.soAborted

 I never had this problem with scientific linux, but I really want to begin using the programs in ubuntu, so if anyone can help me I would be very grateful.

Cheers 

Gudwin

---

### Post by ohioBen on 2010-09-29
I have had the same issues.  Radware's xm programs have worked on some computers of mine and not others.

I was able to get xmesc and xmlev to work by copying a working executable file into the place of the non working one.  Also, I think using the static-linked motif files that are downloadable at his website may have worked for me once, though it isn't working now.

Also, I have the same issue with the location of font.dat being improperly defined even after editing my bashrc files....

---

### Post by ohioBen on 2010-10-01
[B]>> ERROR - cannot open file font.dat
 >> -- Check that the environment variable or logical name
     >> RADWARE_FONT_LOC is properly defined, and that the file
     >> font.dat exists in the directory to which it points.[/B]

To solve this I went to my environment variables at /etc/environment and added the variable RADWARE_FONT_LOC.  I needed to restart my computer and then it worked.  

To solve the error with xmlev and or xmgls, I went in to the source code directory ../rw01/src while in a terminal.  I then recompiled the xm234.c file, then recompiled the whole xmlev.  My exact commands were...
$ gcc xm234.c -c
$ make xmlev

If you are having the same problem with levit8r (which I was) I did the following

$ gcc levit8ra.c -c
$ make levitr8r

Both created new executables in the src folder which I then copied into my rw_current/bin folder.  I didn't have a problem with xmgls, although I suspect if you do the following...

$ gcc xmgls.c -c
$ make xmgls

...It might work

Cheers

---

### Post by aeonian on 2011-03-03
I also ran into the same problem and the solution is as said by "ohioBen", just need a little more tweak. Instead of doing 
$ gcc levit8ra.c -c
$ make levitr8r

separately, one can do

$ gcc *.c -c
$ make all 
$ make install

and this will solve all the problems (or errors)

---

