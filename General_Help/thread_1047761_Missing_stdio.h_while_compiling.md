---
title: "Missing stdio.h while compiling"
date: 2009-01-22
forum: General Help
---

### Post by Horus-I on 2009-01-22
I know everyone is sick of hearing this question, and I really hate to make it my first post, but I've been searching for a while now and tried several proposed solutions to no avail.  gcc can't find stdio.h I don't know if my problem is unique, a lot of people have given up, or if I really just suck at searching forums.  I'm running ibex updated about fifteen minutes ago.  Some details:

Firstly, I DO have build-essentials:

> $ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done


Secondly, I do have stdio.h.  At least there is a file at /usr/include/stdio.h.  I don't really know what it is supposed to look like beyond that.  
> :/usr/include$ ls
aio.h        endian.h        ieee754.h     netdb.h     resolv.h     tar.h
aliases.h    envz.h          ifaddrs.h     neteconet   rpc          termio.h
alloca.h     err.h           inttypes.h    netinet     rpcsvc       termios.h
a.out.h      errno.h         langinfo.h    netipx      sched.h      tgmath.h
argp.h       error.h         lastlog.h     netiucv     scsi         thread_db.h
argz.h       execinfo.h      libgen.h      netpacket   search.h     time.h
ar.h         fcntl.h         libgpilotdCM  netrom      semaphore.h  ttyent.h
arpa         features.h      libintl.h     netrose     setjmp.h     ucontext.h
asm          fenv.h          libio.h       nfs         sgtty.h      ulimit.h
asm-generic  fmtmsg.h        limits.h      nl_types.h  shadow.h     unistd.h
assert.h     fnmatch.h       link.h        nss.h       signal.h     ustat.h
bits         fpu_control.h   linux         obstack.h   spawn.h      utime.h
byteswap.h   fstab.h         locale.h      paths.h     stab.h       utmp.h
c++          fts.h           malloc.h      poll.h      stdint.h     utmpx.h
compiz       ftw.h           math.h        printf.h    stdio_ext.h  values.h
complex.h    _G_config.h     mcheck.h      protocols   **_stdio.h_**      wait.h
cpio.h       gconv.h         memory.h      pthread.h   stdlib.h     wchar.h
crypt.h      getopt.h        mntent.h      pty.h       string.h     wctype.h
ctype.h      glob.h          monetary.h    pwd.h       strings.h    wordexp.h
cups         gnu             mqueue.h      python2.4   stropts.h    X11
dbus-1.0     gnu-versions.h  net           python2.5   sys          xlocale.h
dirent.h     gpilotd         netash        re_comp.h   syscall.h
dlfcn.h      grp.h           netatalk      regex.h     sysexits.h
elf.h        iconv.h         netax25       regexp.h    syslog.h


Thirdly, my /home is on a seperate partition from / (and thus, from /usr/include).  I don't know if that would change anything.

My problem is that when I attempt to compile, gcc aparently can't find stdio.h, e.g:

> $ gcc -o helloworld helloworld.c
helloworld.c:1:20: error:  stdio.h: No such file or directory

Does anyone have an idea that isn't installing build-essential or installing libc6-dev?

---

### Post by AliTabuger7 on 2009-01-22
whats the exact line that it is refering to look like?

---

### Post by Horus-I on 2009-01-22
#include <stdio.h>

---

### Post by AliTabuger7 on 2009-01-23
I'm only an intermediate programmer, but isn't that supposed to be
#include <iostream>

I also don't know if i've ever seen a .h file used as an include, but again that is probably just because of my relatively little experience. Perhaps you could also try.
#include <stdio>

---

### Post by ByteJuggler on 2009-01-23
Please try

```
gcc -v -c -o helloworld helloworld.c
```

And post the output here.  This will (amonst other things) print the header search path in use.  If you have the headers present, but gcc isn't finding them, this suggests that your search path is somehow wrong.  (Have you got a customised .profile or .bash_profile?)

---

### Post by ByteJuggler on 2009-01-23
> **AliTabuger7 said:**
> I'm only an intermediate programmer, but isn't that supposed to be
#include <iostream>

I also don't know if i've ever seen a .h file used as an include, but again that is probably just because of my relatively little experience. Perhaps you could also try.
#include <stdio>

You would be right if he was doing C++, but he's doing C, so no.   For C, you include the header neame, e.g. <stdio.h>.

Cheers

---

### Post by jespdj on 2009-01-23
> **AliTabuger7 said:**
> I'm only an intermediate programmer, but isn't that supposed to be
#include <iostream>

I also don't know if i've ever seen a .h file used as an include, but again that is probably just because of my relatively little experience. Perhaps you could also try.
#include <stdio>
If you are programming in C++, then you should use iostream, or #include <cstdio> if you want the C version of the header file.

If you are programming in C, then #include <stdio.h> is correct.

Normally, for this problem, installing build-essential should be the only thing you need to do. However, if that doesn't help, then something might be wrong with the configuration of the compiler and / or the stuff from the build-essential package.

Do you have set any environment variables which might make gcc not look in the standard place for header files?

Try removing build-essential and reinstalling it:
```
sudo apt-get purge build-essential
sudo apt-get install build-essential
```

---

### Post by ByteJuggler on 2009-01-23
Also, please post the output of

```
ls -al /usr/include/stdio.h
```

Want to check it's world readable.

---

