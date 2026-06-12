---
title: "Replace Thunar with Nautilus in Maverick?"
date: 2010-11-02
forum: Desktop Environments
---

### Post by copb.phoenix on 2010-11-02
The topic is pretty much the only question. I have a deep love for most of XFCE, but nothing can ever replace Nautilus to me. So, how do I arrange everything to completely and safely remove Thunar?

I'm not terminal shy ~ software engineering student. It might also matter that I'm running the 64 -bit version and that my language skills aren't the greatest right now because of a massive headache.

Thanks in advance!

---

### Post by hhh on 2010-11-02
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1167149](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1167149)

---

### Post by 3Miro on 2010-11-02
If you want to use Nautilus, then just install it. I have Thunar under Gnome and while the Places menu opens Nautilus, I have Thunar shortcut on the panel. If you want Nautilus to manage mounting media and such as well as show wallpaper, then the above post should cover it.

---

### Post by copb.phoenix on 2010-11-02
I've collected a pair of errors in between somewhere:
[http://bit.ly/ljmErrors101102](http://bit.ly/ljmErrors101102)

- The first error throws itself at login
- The second error happens whenever I try to use any folder link on the machine. Yes, I can run Nautilus and it runs just fine, but I was hoping for the same style of response that it would give under GNOME (or Thunar under XFCE, etc.)

The startup entry reads "nautilus" for the command to issue, and thunar has been removed via Aptitude (aptitude purge). Leaving Thunar installed makes it want to handle everything for the filesystem, removing it creates those two errors (at least), neither of which is something I want... What am I doing wrong here?

@hhh: If XFCE behaves the way I think it does (sincerely didn't pour over documentation), that would drastically change my right-click menu on the desktop... I am at the point of needing a way to integrate it to replace Thunar, not various parts of XFCE.

Or I'm being unnecessary rude. Sincerely, thanks to you and the others so far, but something isn't right with that configuration. I had stumbled through that post via a search before, but assumed that it didn't work with Maverick for whatever reason when I tried it.

---

### Post by hhh on 2010-11-03
Maybe this?...
[http://ubuntuforums.org/showpost.php?p=4490813&postcount=2](http://ubuntuforums.org/showpost.php?p=4490813&postcount=2)

---

### Post by copb.phoenix on 2010-11-03
Unfortunately, no. Reinstalling Thunar (which is probably the easiest way to make sure I match the environment for that post) does at least clear up the two errors, but once again Thunar insists on loading itself as the file manager even after following the directions verbatim in that post.

And of course it clears up the two errors ~ XFCE wants Thunar, give it Thunar and it's happy even if I'm not. Mildly frustrating to say the least.

---

### Post by hhh on 2010-11-03
Gah! So have xfdesktop manage the desktop but have nautilus manage files. The problems are that nautilus wants to take over the desktop, though you can run it with --no-desktop to solve that, and that xfdesktop is linked to Thunar. Add to that the fact that if anyone normally wants to switch file managers in Xfce they want PCManFM and you have almost nothing to work with.

I did find this though...
[http://old.nabble.com/Xfdesktop-and-nautilus-td29064121.html](http://old.nabble.com/Xfdesktop-and-nautilus-td29064121.html)
It's recent too, I'd try and get in touch with Victor there.

---

### Post by copb.phoenix on 2010-11-03
```

lakejm@ffd-lt-x1010:~/progs/xfdesktop-4.6.2$ ./configure --with-file-manager-fallback=nautilus
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
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
checking minix/config.h usability... no
checking minix/config.h presence... no
checking for minix/config.h... no
checking whether it is safe to define __EXTENSIONS__... yes
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking whether NLS is requested... yes
checking for intltool >= 0.31... 0.41.1 found
checking for intltool-update... /usr/bin/intltool-update
checking for intltool-merge... /usr/bin/intltool-merge
checking for intltool-extract... /usr/bin/intltool-extract
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for perl... /usr/bin/perl
checking for perl >= 5.8.1... 5.10.1
checking for ANSI C header files... (cached) yes
checking ctype.h usability... yes
checking ctype.h presence... yes
checking for ctype.h... yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking math.h usability... yes
checking math.h presence... yes
checking for math.h... yes
checking signal.h usability... yes
checking signal.h presence... yes
checking for signal.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for string.h... (cached) yes
checking sys/mman.h usability... yes
checking sys/mman.h presence... yes
checking for sys/mman.h... yes
checking for sys/stat.h... (cached) yes
checking sys/statvfs.h usability... yes
checking sys/statvfs.h presence... yes
checking for sys/statvfs.h... yes
checking for sys/types.h... (cached) yes
checking sys/wait.h usability... yes
checking sys/wait.h presence... yes
checking for sys/wait.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking for unistd.h... (cached) yes
checking for mmap... yes
checking for sigaction... yes
checking for srandom... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... (cached) /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... (cached) /usr/bin/msgfmt
checking for xgettext... (cached) /usr/bin/xgettext
checking for catalogs to be installed...  am ar ast az be bg bn_IN ca cs da de dz el en_GB eo es_MX es et eu fa fi fr gl gu he hi hu hy id it ja ka kk ko lt lv mk mr ms nb nl nn pa pl pt_BR pt ro ru si sk sq sv ta tr ug uk ur_PK ur vi zh_CN zh_TW
checking for bind_textdomain_codeset... (cached) yes
checking for locales directory... ${datarootdir}/locale
checking for additional xgettext flags... --keyword=Q_ --from-code=UTF-8
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for main in -lX11... yes
checking for SmcSaveYourselfDone in -lSM... yes
checking for pkg-config... /usr/bin/pkg-config
checking for pkg-config >= 0.9.0... 0.25
checking for gmodule-2.0 >= 2.10.0... not found
*** The required package gmodule-2.0 was not found on your system.
*** Please install gmodule-2.0 (atleast version 2.10.0) or adjust
*** the PKG_CONFIG_PATH environment variable if you
*** installed the package in a nonstandard prefix so that
*** pkg-config is able to find it.

```

What's wrong here? I can't find the package, and Google isn't much help... I'm sorry, I know I'm being a bother, but this actually has taught me proper use of source patches now, if nothing else.

---

### Post by hhh on 2010-11-03
OK, but only if you post how to patch, I've never learned:^)

---

### Post by hhh on 2010-11-04
Last post was just kidding. After some Googling, this is my best guess...
[http://packages.ubuntu.com/maverick/libglib2.0-dev](http://packages.ubuntu.com/maverick/libglib2.0-dev)

If that's not it, I'll say again sign up for an oldnabble account and get in touch with Victor.

---

### Post by copb.phoenix on 2010-11-04
Nah, it's fine. I'd recognise that face anywhere :^) . Just classes, headaches, and sickness keeps me away from my machine.

Anyway, after finally resolving all the packages I was missing and compiling, I now don't get any complaints from xfdesktop, but my desktop isn't being managed by anything.

Ouch. And I didn't remove Thunar because it's my understanding from that configuration line that thunar is still supposed to handle everything but file management.

I'm going to keep working at this. Usted hhh, thank you so very much for your help, but I do believe this one is one that needs directed to the author of the patch file now. I'm going to try to compile/install one more time, and then I'll be off to (briefly) bug them.

Is there any way to repay you on these forums?

---

### Post by The_Eddster on 2011-08-17
Can anyone tell me how to apply that patch? I've googled how to apply patches but I'm still completely lost :(

The only reason I want nautilus to replace thunar is so that double clicking on shell scripts will open them in a text editor instead of launching them by default (much to my annoyance!)

I also want to steer clear of replacing xfdesktop with nautilus if possible, since I'm using xinerama to support dual monitors.

Thanks in advance

---

