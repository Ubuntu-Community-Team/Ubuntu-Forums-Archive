---
title: "cannot compile bitchx from the source at all."
date: 2006-05-30
forum: Desktop Environments
---

### Post by mikekc on 2006-05-30
I've installed build-essentials and libncurses, ncurses etc lots of things still cannot get it to compile from the source.  The reason I want it to compile from the source is because the bitchx package itself via apt-get does not have proxy support in it or things like that.   Anyways here is a configure log I generated 
------------------------------------------------------------------------
Welcome to the BitchX-1.1-final configuration

checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether ln -s works... yes
checking for gmake... no
checking for make... make
checking whether make sets ${MAKE}... yes
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking for library containing strerror... none required
checking whether gcc accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether ln -s works... yes
checking for gmake... no
checking for make... make
checking whether make sets ${MAKE}... yes
checking how to run the C preprocessor... gcc -E
checking whether gcc needs -traditional... no
checking for library containing strerror... none required
checking for AIX... no
checking for gawk... gawk
checking for getpwnam in -lsun... no
checking for inet_addr in -ldgc... no
checking for res_mkquery in -lresolv... yes
checking for res_mkquery in -lc... yes
checking for crypt in -lcrypt... yes
checking for pow in -lm... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
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
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking net/if.h usability... yes
checking net/if.h presence... yes
checking for net/if.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/fcntl.h usability... yes
checking sys/fcntl.h presence... yes
checking for sys/fcntl.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking sys/file.h usability... yes
checking sys/file.h presence... yes
checking for sys/file.h... yes
checking sys/syslimits.h usability... no
checking sys/syslimits.h presence... no
checking for sys/syslimits.h... no
checking netinet/in_systm.h usability... yes
checking netinet/in_systm.h presence... yes
checking for netinet/in_systm.h... yes
checking sys/in_systm.h usability... no
checking sys/in_systm.h presence... no
checking for sys/in_systm.h... no
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking sys/un.h usability... yes
checking sys/un.h presence... yes
checking for sys/un.h... yes
checking sys/filio.h usability... no
checking sys/filio.h presence... no
checking for sys/filio.h... no
checking regex.h usability... yes
checking regex.h presence... yes
checking for regex.h... yes
checking resolv.h usability... yes
checking resolv.h presence... yes
checking for resolv.h... yes
checking arpa/nameser.h usability... yes
checking arpa/nameser.h presence... yes
checking for arpa/nameser.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking sys/ndir.h usability... no
checking sys/ndir.h presence... no
checking for sys/ndir.h... no
checking sys/dir.h usability... yes
checking sys/dir.h presence... yes
checking for sys/dir.h... yes
checking ndir.h usability... no
checking ndir.h presence... no
checking for ndir.h... no
checking for stpcpy in string.h... no
checking for getpgid in unistd.h... no
checking for killpg in signal.h... yes
checking for getpass in unistd.h... yes
checking for errno in errno.h... no
checking for struct linger in sys/socket.h... yes
checking for sun_len in sys/un.h... no
checking for bcopy in string.h... yes
checking for gcc option to accept ANSI C... none needed
checking for an ANSI C-conforming const... yes
checking for uid_t in sys/types.h... yes
checking for inline... inline
checking for mode_t... yes
checking for off_t... yes
checking for pid_t... yes
checking for size_t... yes
checking return type of signal handlers... void
checking for sys_siglist declaration in signal.h or unistd.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for unsigned int... yes
checking size of unsigned int... 4
checking for working alloca.h... yes
checking for alloca... yes
checking whether getpgrp requires zero arguments... yes
checking whether setpgrp takes no argument... yes
checking for strftime... yes
checking for socket... yes
checking for gethostname... yes
checking for gettimeofday... yes
checking for strtoul... yes
checking for strlcpy... no
checking for strlcat... no
checking for stpcpy... yes
checking for vsnprintf... yes
checking for snprintf... yes
checking for setsid... yes
checking for strerror... yes
checking for uname... yes
checking for getrusage... yes
checking for sysconf... yes
checking for getpgid... yes
checking for killpg... yes
checking for getlogin... yes
checking for realpath... yes
checking for fchdir... yes
checking for getpass... yes
checking for fpathconf... yes
checking for getpwent... yes
checking for setvbuf... yes
checking for select... yes
checking for mkstemp... yes
checking for memmove... yes
checking for scandir... yes
checking for gethostbyname... yes
checking for connect... yes
checking for inet_aton... yes
checking whether setvbuf arguments are reversed... no
checking for non-blocking type... posix
checking for a list of signal names... yes
checking whether to enable GTK support... no
checking whether to enable Win32 GUI support... no
checking whether to enable OS/2 PM support... no
checking whether to enable sound support... no
checking whether to enable SSL support... no
checking whether to use use tgetent or setupterm... setupterm
checking for setupterm in -lncurses... yes
checking for tparm in ncurses.h... yes
checking for tparm in -lncurses... yes
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking ncurses/termcap.h usability... no
checking ncurses/termcap.h presence... no
checking for ncurses/termcap.h... no
checking termcap.h usability... yes
checking termcap.h presence... yes
checking for termcap.h... yes
checking for tputs in ncurses/termcap.h... no
checking for tputs in termcap.h... (cached) no
checking for tputs in -lncurses... yes
checking whether to enable Tcl support... no
checking for unix mail directory... /var/spool/mail
checking for default server list... none
checking whether to enable IPv6 support... no
checking whether to enable SOCKS support... no
checking whether to enable CD-ROM support... no
checking whether to enable dmalloc debugging support... no
checking whether to enable plugin support... not building with plugin support - you will not be able to use plugins
configure: creating ./config.status
config.status: creating Makefile
config.status: creating BitchX.spec
config.status: creating gtkBitchX.spec
config.status: creating bx-conf/Makefile
config.status: creating doc/BitchX.bat

config.status: creating doc/Makefile
config.status: creating dll/Makefile
config.status: creating dll/abot/Makefile
config.status: creating dll/acro/Makefile
config.status: creating dll/aim/Makefile
config.status: creating dll/aim/toc/Makefile
config.status: creating dll/amp/Makefile
config.status: creating dll/arcfour/Makefile
config.status: creating dll/autocycle/Makefile
config.status: creating dll/aim/Makefile
config.status: creating dll/blowfish/Makefile
config.status: creating dll/cavlink/Makefile
config.status: creating dll/cdrom/Makefile
config.status: creating dll/encrypt/Makefile
config.status: creating dll/europa/Makefile
config.status: creating dll/fserv/Makefile
config.status: creating dll/hint/Makefile
config.status: creating dll/identd/Makefile
config.status: creating dll/nap/Makefile
config.status: creating dll/nicklist/Makefile
config.status: creating dll/pkga/Makefile
config.status: creating dll/possum/Makefile
config.status: creating dll/qbx/Makefile
config.status: creating dll/qmail/Makefile
config.status: creating dll/scan/Makefile
config.status: creating dll/wavplay/Makefile
config.status: creating dll/xmms/Makefile
config.status: creating source/Makefile
config.status: creating include/defs.h
config.status: include/defs.h is unchanged
config.status: executing default commands

BitchX (c) 1996-2002 Colten Edwards
----------------------------------------------------------

The configuration script has finished. You should look through
"include/config.h" and make any changes you would like to make.

Now type "make" to compile BitchX.
------------------------------------------------------------------------
this is what happens when I type make
-------------------------------------------------------------------------
make
alias.c: In function âdestroy_arglistâ:
alias.c:746: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âadd_var_aliasâ:
alias.c:937: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:941: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âadd_cmd_aliasâ:
alias.c:1017: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1021: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âadd_var_stub_aliasâ:
alias.c:1055: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1059: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âadd_cmd_stub_aliasâ:
alias.c:1085: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âfind_var_aliasâ:
alias.c:1157: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âfind_cmd_aliasâ:
alias.c:1223: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âdelete_all_var_aliasâ:
alias.c:1401: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1412: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âdelete_var_aliasâ:
alias.c:1423: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1434: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âdelete_cmd_aliasâ:
alias.c:1448: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1460: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âglob_cmd_aliasâ:
alias.c:1710: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1724: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1734: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âglob_assign_aliasâ:
alias.c:1752: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1766: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1776: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âpmatch_cmd_aliasâ:
alias.c:1793: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1804: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1812: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âpmatch_assign_aliasâ:
alias.c:1829: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1840: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1848: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âget_subarray_elementsâ:
alias.c:1876: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1894: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:1903: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âBX_make_local_stackâ:
alias.c:2067: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âdestroy_call_stackâ:
alias.c:2205: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âaliasctlâ:
alias.c:2338: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:2362: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c: In function âdo_stack_aliasâ:
alias.c:2456: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:2458: warning: dereferencing type-punned pointer will break strict-aliasing rules
alias.c:2463: warning: dereferencing type-punned pointer will break strict-aliasing rules
array.c: In function âdelete_arrayâ:
array.c:353: warning: dereferencing type-punned pointer will break strict-aliasing rules
array.c:359: warning: dereferencing type-punned pointer will break strict-aliasing rules
array.c: In function âdelete_all_arraysâ:
array.c:393: warning: dereferencing type-punned pointer will break strict-aliasing rules
array.c: In function âfunction_setitemâ:
array.c:683: warning: dereferencing type-punned pointer will break strict-aliasing rules
banlist.c: In function âshitlist_eraseâ:
banlist.c:235: warning: dereferencing type-punned pointer will break strict-aliasing rules
banlist.c: In function âmasskickâ:
banlist.c:798: warning: dereferencing type-punned pointer will break strict-aliasing rules
banlist.c: In function âmassbanâ:
banlist.c:994: warning: dereferencing type-punned pointer will break strict-aliasing rules
banlist.c: In function âremove_bansâ:
banlist.c:1446: warning: dereferencing type-punned pointer will break strict-aliasing rules
banlist.c:1460: warning: dereferencing type-punned pointer will break strict-aliasing rules
cdcc.c: In function âl_queueâ:
cdcc.c:1060: warning: dereferencing type-punned pointer will break strict-aliasing rules
cdcc.c: In function âl_loadâ:
cdcc.c:1193: warning: dereferencing type-punned pointer will break strict-aliasing rules
cdcc.c: In function âadd_filesâ:
cdcc.c:1320: warning: dereferencing type-punned pointer will break strict-aliasing rules
cdcc.c: In function âdel_packâ:
cdcc.c:1401: warning: dereferencing type-punned pointer will break strict-aliasing rules
cdcc.c:1434: warning: dereferencing type-punned pointer will break strict-aliasing rules
cdcc.c: In function âdcc_sendfrom_queueâ:
cdcc.c:1552: warning: dereferencing type-punned pointer will break strict-aliasing rules
chelp.c: In function âread_fileâ:
chelp.c:191: warning: dereferencing type-punned pointer will break strict-aliasing rules
chelp.c:197: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c: In function âdo_getoutâ:
commands.c:1199: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c:1208: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c:1216: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c:1225: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c: In function âcheck_wait_commandâ:
commands.c:1864: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c: In function âadd_to_ajoin_listâ:
commands.c:2341: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c:2360: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c: In function âauto_joinâ:
commands.c:2399: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c:2406: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c:2408: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c: In function âe_hostnameâ:
commands.c:2774: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c: In function âbackâ:
commands.c:2983: warning: pointer targets in passing argument 1 of âstripansicodesâ differ in signedness
commands.c: In function âcommand_completionâ:
commands.c:4060: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c:4148: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands.c:4170: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands2.c: In function âadd_ban_wordâ:
commands2.c:209: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands2.c:215: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands2.c:223: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands2.c:228: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands2.c: In function âshow_versionâ:
commands2.c:985: warning: pointer targets in passing argument 1 of âstripansicodesâ differ in signedness
commands2.c: In function âadd_bad_nickâ:
commands2.c:1470: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands2.c:1474: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands2.c:1478: warning: dereferencing type-punned pointer will break strict-aliasing rules
commands2.c: In function âhandle_reconnectâ:
commands2.c:2457: warning: pointer targets in passing argument 3 of âgetpeernameâ differ in signedness
cset.c: In function âcheck_cset_queueâ:
cset.c:355: warning: dereferencing type-punned pointer will break strict-aliasing rules
cset.c:365: warning: dereferencing type-punned pointer will break strict-aliasing rules
cset.c: In function âcreate_csets_for_channelâ:
cset.c:654: warning: dereferencing type-punned pointer will break strict-aliasing rules
ctcp.c:179: error: static declaration of âctcp_typeâ follows non-static declaration
/home/acid/BitchX/include/ctcp.h:59: error: previous declaration of âctcp_typeâ was here
ctcp.c: In function âdo_versionâ:
ctcp.c:896: warning: pointer targets in passing argument 1 of âstripansicodesâ differ in signedness
ctcp.c: In function âdo_notice_ctcpâ:
ctcp.c:1367: warning: pointer targets in passing argument 1 of âstripansiâ differ in signedness
make[1]: *** [ctcp.o] Error 1
make: *** [BitchX] Error 2
-----------------------------------------------------------------------

I can't seem to figure out what I need to do or what I need.  Does anyone know?

---

### Post by fooey on 2006-08-04
ya i had the same problem... wonder if you ever figured it out

---

### Post by mikekc on 2006-08-04
I just ended up using the binaries from the site... they work good enough.  I wish I could use the source though but that doesn't seem possible.  Not sure why.  Oh well the binaries work good.

---

### Post by white_tiger_daniel on 2006-08-06
This may sound a bit 'noobish', but how do you use the binaries?

---

### Post by crazysloth on 2007-06-10
Save this to bx-ubuntu.patch and run from the BitchX directory (patch -p1 < bx-ubuntu.patch)

diff -urp ../BitchX/include/ctcp.h ./include/ctcp.h
--- ../BitchX/include/ctcp.h    2003-04-10 18:09:07.000000000 -0700
+++ ./include/ctcp.h    2007-06-10 14:28:54.000000000 -0700
@@ -56,7 +56,7 @@
 extern CtcpEntryDll *dll_ctcp;


-extern         char    *ctcp_type[];
+// extern              char    *ctcp_type[];
 extern         int     sed;
 extern         int     in_ctcp_flag;

diff -urp ../BitchX/include/struct.h ./include/struct.h
--- ../BitchX/include/struct.h  2003-04-10 18:09:07.000000000 -0700
+++ ./include/struct.h  2007-06-10 14:34:46.000000000 -0700
@@ -1064,7 +1064,7 @@ struct    timeval time;
        int     delete;
 }      TimerList;

-extern TimerList *PendingTimers;
+// extern TimerList *PendingTimers;
 typedef struct nicktab_stru
 {
        struct nicktab_stru *next;
diff -urp ../BitchX/source/term.c ./source/term.c
--- ../BitchX/source/term.c     2003-04-10 18:09:07.000000000 -0700
+++ ./source/term.c     2007-06-10 14:33:27.000000000 -0700
@@ -92,7 +92,7 @@ extern        int             tgetflag();
 #endif

 extern  char    *getenv();
-extern char    *tparm();
+// extern      char    *tparm();

 /*
  * The old code assumed termcap. termcap is almost always present, but on

---

### Post by jesushero on 2008-07-01
> **crazysloth said:**
> Save this to bx-ubuntu.patch and run from the BitchX directory (patch -p1 < bx-ubuntu.patch)

diff -urp ../BitchX/include/ctcp.h ./include/ctcp.h
--- ../BitchX/include/ctcp.h    2003-04-10 18:09:07.000000000 -0700
+++ ./include/ctcp.h    2007-06-10 14:28:54.000000000 -0700
@@ -56,7 +56,7 @@
 extern CtcpEntryDll *dll_ctcp;


-extern         char    *ctcp_type[];
+// extern              char    *ctcp_type[];
 extern         int     sed;
 extern         int     in_ctcp_flag;

diff -urp ../BitchX/include/struct.h ./include/struct.h
--- ../BitchX/include/struct.h  2003-04-10 18:09:07.000000000 -0700
+++ ./include/struct.h  2007-06-10 14:34:46.000000000 -0700
@@ -1064,7 +1064,7 @@ struct    timeval time;
        int     delete;
 }      TimerList;

-extern TimerList *PendingTimers;
+// extern TimerList *PendingTimers;
 typedef struct nicktab_stru
 {
        struct nicktab_stru *next;
diff -urp ../BitchX/source/term.c ./source/term.c
--- ../BitchX/source/term.c     2003-04-10 18:09:07.000000000 -0700
+++ ./source/term.c     2007-06-10 14:33:27.000000000 -0700
@@ -92,7 +92,7 @@ extern        int             tgetflag();
 #endif

 extern  char    *getenv();
-extern char    *tparm();
+// extern      char    *tparm();

 /*
  * The old code assumed termcap. termcap is almost always present, but on



This is an interesting solution but it doesn't work as is, perhaps since the patch is not fully pasted here.. Can you help me out a bit by checking to see if there's something missing there? patch returns several error messages.. Could it have to do with the brackets? 

Let me know.. Thanks..

---

