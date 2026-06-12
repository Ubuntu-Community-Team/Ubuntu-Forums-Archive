---
title: "MySQL 4.0.27 won't compile -- needs Termcap?"
date: 2006-08-22
forum: Desktop Environments
---

### Post by ChantCd_com on 2006-08-22
--------------------------------------------------------------------------------

I'm using Ubuntu 6.06.1 LTS (Server-only package)

Here's the error I'm getting:
"checking for termcap functions library... configure: error: No curses/termcap library found"

I installed the following library, but MySQL 'configure' still reports the same problem:

--------------------------------------------------------------------
The termcap-compat package provides the libtermcap.so.2 and /etc/termcap files which are required to run non-Debian, binary-only termcap-based programs. Since libc6-based programs are hopefully "modern" enough to be linked with ncurses (or slang), this package only provides a libc5-based libtermcap library. 

You do not need to install this package to run Debian-packaged programs since Debian GNU/Linux uses terminfo and not termcap. You need this package if a program (that you cannot recompile) fails to run with the error message "...: can't load library 'libtermcap.so.2'" or complains about a missing /etc/termcap file. 

The termcap-compat package isn't meant to be used to compile programs therefore it doesn't provide all the necessary files for compilation. If you want to compile a program that claims to need termcap, why not try ncurses's termcap emulation instead? It's as simple as linking with ncurses instead of libtermcap (i.e. replace the '-ltermcap' with '-lncurses' in the makefile). Ncurses' termcap emulation routines translate terminfo entries to termcap entries on the fly, so you don't even need an /etc/termcap file. 

This package provides: 

libtermcap.so shared library, version 2.0.8
termcap database, version 10.2.7
--------------------------------------------------------------------

---

### Post by Nimefurahi on 2006-10-19
Dear ChantCD_com,

I notice this post is 2 months old, but if you're still having the same problem, make sure you have the following installed:

(you probably have these, but to be sure)
sudo apt-get install gcc
sudo apt-get install libgcc1
sudo apt-get install g++
sudo apt-get install cpp
sudo apt-get install ncurses-base
sudo apt-get install ncurses-bin
sudo apt-get install ncurses-term
sudo apt-get install libncurses5

(and most importantly)
sudo apt-get install libncurses5-dev

I trust that will resolve your problem if you haven't already done so.

Cheers,
Nimefurahi

---

### Post by cosmolee on 2006-12-24
Where does one find the " termcap-compat" package?  I've searched synaptic on 6.06 and 6.10, but can't find it.  I need the "libtermcap.so.2" file also.  

TIA.

---

### Post by Nimefurahi on 2006-12-25
Good question. However, I'm not so sure that you even need termcap. Use instead the ncurses' emulation of termcap referred to as "term-info" provided by ncurses-term.

Before (re)compiling mysql, follow the instructions posted above and again here below:

sudo apt-get install gcc
sudo apt-get install libgcc1
sudo apt-get install g++
sudo apt-get install cpp
sudo apt-get install ncurses-base
sudo apt-get install ncurses-bin
sudo apt-get install ncurses-term
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev

Notice the package "ncurses-term". I believe ncurses-term will yield the "term-info" that will take the place (in the Debain context) of "termcap" that your compilation protests of not having available. Ignoring all protests otherwise, my compilation was happy with the "term-info" emulation of termcap provided by ncurses-term. Please make sure that you have all the other packages installed as well.

Give it a try.

---

### Post by cosmolee on 2006-12-25
Thanks for your reply Nimefurahi, however, "libtermcap.so.2" is the file I'm actually looking for, and it doesn't seem to be included with "ncurses-term".   I already have that package installed, but `find` doesn't show it on my system.  In fact, a search in Synaptic for "libtermcap.so.2" turns up nothing.  

I don't actually need the file for MySQL, but for another DB package.  However, I found a reference to "libtermcap.so.2" in this thread...

Cosmo

---

### Post by Nimefurahi on 2006-12-25
Cosmolee,

Understood. Well then, take a look at [http://packages.debian.org/stable/oldlibs/termcap-compat]("http://packages.debian.org/stable/oldlibs/termcap-compat")

I'm hoping that may be what you're looking for.

---

### Post by cosmolee on 2007-01-02
I downloaded the termcap-compat package & un-tarred it.  I haven't used C code or `make` in a very long time, so forgive me if I don't know what I'm doing here.


$ ll
total 1760
-rw-r--r-- 1 cosmo cosmo   3440 Feb 15  1998 ChangeLog
-rw-r--r-- 1 cosmo cosmo   2430 Feb 15  1998 Makefile
-rw-r--r-- 1 cosmo cosmo   3714 Feb 15  1998 README
drwxr-xr-x 2 cosmo cosmo   4096 Feb  3  2000 debian
drwxr-xr-x 2 cosmo cosmo   4096 Jan  2 17:08 pic
-rw-r--r-- 1 cosmo cosmo  14167 Oct 26  1999 termcap.c
-rw-r--r-- 1 cosmo cosmo   1588 Feb 15  1998 termcap.h
-rw-r--r-- 1 cosmo cosmo   2093 Feb 15  1998 termcap.info
-rw-r--r-- 1 cosmo cosmo  47407 Feb 15  1998 termcap.info-1
-rw-r--r-- 1 cosmo cosmo  43849 Feb 15  1998 termcap.info-2
-rw-r--r-- 1 cosmo cosmo  49307 Feb 15  1998 termcap.info-3
-rw-r--r-- 1 cosmo cosmo   9761 Feb 15  1998 termcap.info-4
-rw-r--r-- 1 cosmo cosmo   6708 Jan  2 17:08 termcap.o
-rw-r--r-- 1 cosmo cosmo 141690 Feb 15  1998 termcap.texi
-rw-r--r-- 1 cosmo cosmo 631716 Feb  3  2000 termtypes.tc
-rw-r--r-- 1 cosmo cosmo 629726 Oct 30  1999 termtypes.tc~
-rw-r--r-- 1 cosmo cosmo 146167 Feb 15  1998 texinfo.tex
-rw-r--r-- 1 cosmo cosmo   7748 Jan  2 17:30 tparam.c
-rw-r--r-- 1 cosmo cosmo    246 Feb 15  1998 version.c
$


I tried running a `make`, but got these errors.:  

$ make
gcc -O -I. -c tparam.c
In file included from tparam.c:34:
/usr/include/string.h:292: error: expected declaration specifiers or '...' before '(' token
/usr/include/string.h:292: error: expected declaration specifiers or '...' before '(' token
/usr/include/string.h:292: error: expected declaration specifiers or '...' before '(' token
/usr/include/string.h:293: error: conflicting types for 'memcpy'
make: *** [tparam.o] Error 1
$

Are there messages actually telling me that there's an error in the "string.h" header file?  That doesn't seem likely.


Any idea what is going on?  TIA.

---

### Post by andrikos on 2007-07-09
Like I said to another thread....


If someone still has the problem with libtermcap i have to suggest this simple solution

sudo ln -s /lib/libncurses.so.5 /lib/libtermcap.so.2

Ncurses also works as a wrapper for the old termcap. It worked for me in another program i needed to run.

---

### Post by Bodiesel on 2007-07-18
> **andrikos said:**
> Like I said to another thread....


If someone still has the problem with libtermcap i have to suggest this simple solution

sudo ln -s /lib/libncurses.so.5 /lib/libtermcap.so.2

Ncurses also works as a wrapper for the old termcap. It worked for me in another program i needed to run.

Thanks! Almost a year later and your post is still quite helpful. It solved a problem I was facing trying to run a visual analysis package.

---

