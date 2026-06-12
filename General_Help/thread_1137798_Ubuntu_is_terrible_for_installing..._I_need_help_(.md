---
title: "Ubuntu is terrible for installing... I need help :("
date: 2009-04-25
forum: General Help
---

### Post by gta117 on 2009-04-25
Please someone help me! I have spent a long, long time on this, and can not find any means to solve it... Now I got the terminal thing posted, its much easier for people to look into. 

EDIT: for the short and sweet folks:   	 	 	 	 	 	  Originally tried to install gnomenu, by following the instructions for 1.7, ended up with glib's make file take over and messing things up. My comp is OBSESSED with the location and make file of glib, and no mater how many times I uninstall it, it will not go away! The terminal text in open office I have on the starter would be a big help for anyone trying to help me. 
 



I am sorry, but no one should ever be forced to go through the terminal. I just switched over to ubuntu, and had 2 other people switch over too. I am working on 2 other people right now.  They all want, including me, to have the vista look, because ubuntu looks ugly, and we all know the format. So I have been TRYING to do that. But with so many packages, many not even in the list, and some not even packaged so its not a simple double click and install like in windows, it does not shock me that windows is still in the lead at all.

 Aside from the rant, and Regardless if people think the terminal is so easy (which its not, esp with the people who I work with who know next to nothing about computers) I have run into one problem after another installing stuff. This time I am really stumped, and even after several days of searching and working the terminal, I can not crack it. I have been lucky I have no job, and have had the chance to work on this thing. Please help.   Below is the terminal text. I was even nice enough to separate it and show you guys what I was trying to do, and what I got. I know how it goes and feels, and I know you guys are just trying to help, even with slightly angry ubuntu users.

EDIT: So I finally managed to get the attachment things to work! bloody no-script was blocking the other part of the site. *sighs* To much time has been lost. the attachment is a text file of my terminal, because the quote or codes botch the easy to read look. sorry. :( here is part of the code problem.

 > 

[LEFT]
[LIST]
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ sudo make  
 cd /home/chivalry/Desktop/glib-1.2.8 && /home/chivalry/Desktop/glib-1.2.8/missing automake --gnu --include-deps Makefile  
 cd: 1: can't cd to /home/chivalry/Desktop/glib-1.2.8  
 make: *** [/home/chivalry/Desktop/glib-1.2.8/Makefile.in] Error 2  
[*]   	 	 	 	 	 	  &&&&&&&&&&&&&&&&&&&&&&
 chivalry@Chivalrys-Computer:~$ ?  
 bash: ?: command not found  
 chivalry@Chivalrys-Computer:~$ space  
 bash: space: command not found  
 chivalry@Chivalrys-Computer:~$ ok, so whats up with that?  
 bash: ok,: command not found  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ sudo make install  
 cd /home/chivalry/Desktop/glib-1.2.8 && /home/chivalry/Desktop/glib-1.2.8/missing automake --gnu --include-deps Makefile  
 cd: 1: can't cd to /home/chivalry/Desktop/glib-1.2.8  
 make: *** [/home/chivalry/Desktop/glib-1.2.8/Makefile.in] Error 2  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ sudo make uninstall  
 cd /home/chivalry/Desktop/glib-1.2.8 && /home/chivalry/Desktop/glib-1.2.8/missing automake --gnu --include-deps Makefile  
 cd: 1: can't cd to /home/chivalry/Desktop/glib-1.2.8  
 make: *** [/home/chivalry/Desktop/glib-1.2.8/Makefile.in] Error 2  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ lets put the folders on the desk?  
 bash: lets: command not found  
 chivalry@Chivalrys-Computer:~$  
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ make  
 make  all-recursive  
 make[1]: Entering directory `/home/chivalry'  
 Making all in .  
 make[2]: Entering directory `/home/chivalry'  
 make[2]: Leaving directory `/home/chivalry'  
 Making all in gmodule  
 make[2]: Entering directory `/home/chivalry/gmodule'  
 make[2]: Nothing to be done for `all'.  
 make[2]: Leaving directory `/home/chivalry/gmodule'  
 Making all in gthread  
 make[2]: Entering directory `/home/chivalry/gthread'  
 make[2]: Nothing to be done for `all'.  
 make[2]: Leaving directory `/home/chivalry/gthread'  
 Making all in docs  
 make[2]: Entering directory `/home/chivalry/docs'  
 make[2]: Nothing to be done for `all'.  
 make[2]: Leaving directory `/home/chivalry/docs'  
 Making all in tests  
 make[2]: Entering directory `/home/chivalry/tests'  
 make[2]: Nothing to be done for `all'.  
 make[2]: Leaving directory `/home/chivalry/tests'  
 make[1]: Leaving directory `/home/chivalry'  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ ok....  
 bash: ok....: command not found  
 chivalry@Chivalrys-Computer:~$ sudo make install  
[*]   	 	 	 	 	 	  Making install in .  
 make[1]: Entering directory `/home/chivalry'  
 make[2]: Entering directory `/home/chivalry'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ./libtool  --mode=install /usr/bin/install -c libglib.la /usr/local/lib/libglib.la  
 /usr/bin/install -c .libs/libglib-1.2.so.0.0.8 /usr/local/lib/libglib-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libglib-1.2.so.0 && ln -s libglib-1.2.so.0.0.8 libglib-1.2.so.0)  
 (cd /usr/local/lib && rm -f libglib.so && ln -s libglib-1.2.so.0.0.8 libglib.so)  
 /usr/bin/install -c .libs/libglib.lai /usr/local/lib/libglib.la  
 /usr/bin/install -c .libs/libglib.a /usr/local/lib/libglib.a  
 ranlib /usr/local/lib/libglib.a  
 chmod 644 /usr/local/lib/libglib.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/bin  
  /usr/bin/install -c  glib-config /usr/local/bin/glib-config  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib/glib/include  
  /usr/bin/install -c -m 644 glibconfig.h /usr/local/lib/glib/include/glibconfig.h  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/share/aclocal  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/glib.m4 /usr/local/share/aclocal/glib.m4  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/include  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/glib.h /usr/local/include/glib.h  
 make[2]: Leaving directory `/home/chivalry'  
 make[1]: Leaving directory `/home/chivalry'  
 Making install in gmodule  
 make[1]: Entering directory `/home/chivalry/gmodule'  
 make[2]: Entering directory `/home/chivalry/gmodule'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ../libtool  --mode=install /usr/bin/install -c -m 644 libgmodule.la /usr/local/lib/libgmodule.la 
 /usr/bin/install -c -m 644 .libs/libgmodule-1.2.so.0.0.8 /usr/local/lib/libgmodule-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libgmodule-1.2.so.0 && ln -s libgmodule-1.2.so.0.0.8 libgmodule-1.2.so.0)  
 (cd /usr/local/lib && rm -f libgmodule.so && ln -s libgmodule-1.2.so.0.0.8 libgmodule.so) 
 /usr/bin/install -c -m 644 .libs/libgmodule.lai /usr/local/lib/libgmodule.la  
 /usr/bin/install -c -m 644 .libs/libgmodule.a /usr/local/lib/libgmodule.a  
 ranlib /usr/local/lib/libgmodule.a  
 chmod 644 /usr/local/lib/libgmodule.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/include  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/gmodule/gmodule.h /usr/local/include/gmodule.h  
 make[2]: Leaving directory `/home/chivalry/gmodule'  
 make[1]: Leaving directory `/home/chivalry/gmodule'  
 Making install in gthread  
 make[1]: Entering directory `/home/chivalry/gthread'  
 make[2]: Entering directory `/home/chivalry/gthread'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ../libtool  --mode=install /usr/bin/install -c libgthread.la /usr/local/lib/libgthread.la  
 /usr/bin/install -c .libs/libgthread-1.2.so.0.0.8 /usr/local/lib/libgthread-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libgthread-1.2.so.0 && ln -s libgthread-1.2.so.0.0.8 libgthread-1.2.so.0)  
 (cd /usr/local/lib && rm -f libgthread.so && ln -s libgthread-1.2.so.0.0.8 libgthread.so) 
 /usr/bin/install -c .libs/libgthread.lai /usr/local/lib/libgthread.la  
 /usr/bin/install -c .libs/libgthread.a /usr/local/lib/libgthread.a  
 ranlib /usr/local/lib/libgthread.a  
 chmod 644 /usr/local/lib/libgthread.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 make[2]: Nothing to be done for `install-data-am'.  
 make[2]: Leaving directory `/home/chivalry/gthread'  
 make[1]: Leaving directory `/home/chivalry/gthread'  
 Making install in docs  
 make[1]: Entering directory `/home/chivalry/docs'  
 make[2]: Entering directory `/home/chivalry/docs'  
 make[2]: Nothing to be done for `install-exec-am'.  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/info  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/docs/glib.info /usr/local/info/glib.info  
 make  install-man1  
 make[3]: Entering directory `/home/chivalry/docs'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/man/man1  
  /usr/bin/install -c -m 644 glib-config.1 /usr/local/man/man1/glib-config.1  
 make[3]: Leaving directory `/home/chivalry/docs'  
 make[2]: Leaving directory `/home/chivalry/docs'  
 make[1]: Leaving directory `/home/chivalry/docs'  
 Making install in tests  
 make[1]: Entering directory `/home/chivalry/tests'  
 make[2]: Entering directory `/home/chivalry/tests'  
 make[2]: Nothing to be done for `install-exec-am'.  
 make[2]: Nothing to be done for `install-data-am'.  
 make[2]: Leaving directory `/home/chivalry/tests'  
 make[1]: Leaving directory `/home/chivalry/tests'  
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ nothing to be done? OMG! >_< Ok, lets uninstall it...  
 bash: Ok,: No such file or directory  
 chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ sudo make uninstall  
[*]   	 	 	 	 	 	  Making uninstall in .  
 make[1]: Entering directory `/home/chivalry'  
 list='libglib.la'; for p in $list; do \ 
 	  /bin/sh ./libtool  --mode=uninstall rm -f /usr/local/lib/$p; \  
 	done  
 rm -f /usr/local/lib/libglib.la /usr/local/lib/libglib-1.2.so.0.0.8 /usr/local/lib/libglib-1.2.so.0 /usr/local/lib/libglib.so /usr/local/lib/libglib.a  
 list='glib-config'; for p in $list; do \  
 	  rm -f /usr/local/bin/`echo $p|sed 's,x,x,'`; \  
 	done  
 list='glibconfig.h'; for p in $list; do \  
 	  rm -f /usr/local/lib/glib/include/$p; \  
 	done  
 list='glib.m4'; for p in $list; do \  
 	  rm -f /usr/local/share/aclocal/$p; \ 
 	done  
 list='glib.h'; for p in $list; do \  
 	  rm -f /usr/local/include/$p; \  
 	done  
 make[1]: Leaving directory `/home/chivalry'  
 Making uninstall in gmodule  
 make[1]: Entering directory `/home/chivalry/gmodule'  
 list='libgmodule.la libgplugin_a.la libgplugin_b.la'; for p in $list; do \  
 	  /bin/sh ../libtool  --mode=uninstall rm -f /usr/local/lib/$p; \  
 	done  
 rm -f /usr/local/lib/libgmodule.la /usr/local/lib/libgmodule-1.2.so.0.0.8 /usr/local/lib/libgmodule-1.2.so.0 /usr/local/lib/libgmodule.so /usr/local/lib/libgmodule.a  
 list='gmodule.h'; for p in $list; do \  
 	  rm -f /usr/local/include/$p; \  
 	done  
 make[1]: Leaving directory `/home/chivalry/gmodule'  
 Making uninstall in gthread  
 make[1]: Entering directory `/home/chivalry/gthread'  
 list='libgthread.la'; for p in $list; do \  
 	  /bin/sh ../libtool  --mode=uninstall rm -f /usr/local/lib/$p; \  
 	done  
 rm -f /usr/local/lib/libgthread.la /usr/local/lib/libgthread-1.2.so.0.0.8 /usr/local/lib/libgthread-1.2.so.0 /usr/local/lib/libgthread.so /usr/local/lib/libgthread.a  
 make[1]: Leaving directory `/home/chivalry/gthread'  
 Making uninstall in docs  
 make[1]: Entering directory `/home/chivalry/docs'  
 :  
 install-info(glib.info): no entry for file `glib'  
 list='glib.info'; \  
 	for file in $list; do \  
 	  (cd /usr/local/info && rm -f $file $file-[0-9] $file-[0-9][0-9]); \  
 	done  
 make  uninstall-man1  
 make[2]: Entering directory `/home/chivalry/docs'  
  rm -f /usr/local/man/man1/glib-config.1  
 make[2]: Leaving directory `/home/chivalry/docs'  
 make[1]: Leaving directory `/home/chivalry/docs'  
 Making uninstall in tests  
 make[1]: Entering directory `/home/chivalry/tests'  
 make[1]: Nothing to be done for `uninstall'.  
 make[1]: Leaving directory `/home/chivalry/tests'  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ you got to be kidding me! Well, lets ignore it and install what I wanted to install...  
 bash: you: command not found  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ sudo make install '/home/chivalry/Desktop/My Documents/gnomenu/Makefile'  
 Making install in .  
 make[1]: Entering directory `/home/chivalry'  
 make[2]: Entering directory `/home/chivalry'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ./libtool  --mode=install /usr/bin/install -c libglib.la /usr/local/lib/libglib.la  
 /usr/bin/install -c .libs/libglib-1.2.so.0.0.8 /usr/local/lib/libglib-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libglib-1.2.so.0 && ln -s libglib-1.2.so.0.0.8 libglib-1.2.so.0)  
 (cd /usr/local/lib && rm -f libglib.so && ln -s libglib-1.2.so.0.0.8 libglib.so)  
 /usr/bin/install -c .libs/libglib.lai /usr/local/lib/libglib.la  
 /usr/bin/install -c .libs/libglib.a /usr/local/lib/libglib.a  
 ranlib /usr/local/lib/libglib.a  
 chmod 644 /usr/local/lib/libglib.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/bin  
  /usr/bin/install -c  glib-config /usr/local/bin/glib-config  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib/glib/include  
  /usr/bin/install -c -m 644 glibconfig.h /usr/local/lib/glib/include/glibconfig.h  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/share/aclocal  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/glib.m4 /usr/local/share/aclocal/glib.m4  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/include  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/glib.h /usr/local/include/glib.h  
 make[2]: Leaving directory `/home/chivalry'  
 make[1]: Leaving directory `/home/chivalry'  
 Making install in gmodule  
 make[1]: Entering directory `/home/chivalry/gmodule'  
 make[2]: Entering directory `/home/chivalry/gmodule'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ../libtool  --mode=install /usr/bin/install -c -m 644 libgmodule.la /usr/local/lib/libgmodule.la 
 /usr/bin/install -c -m 644 .libs/libgmodule-1.2.so.0.0.8 /usr/local/lib/libgmodule-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libgmodule-1.2.so.0 && ln -s libgmodule-1.2.so.0.0.8 libgmodule-1.2.so.0)  
 (cd /usr/local/lib && rm -f libgmodule.so && ln -s libgmodule-1.2.so.0.0.8 libgmodule.so) 
 /usr/bin/install -c -m 644 .libs/libgmodule.lai /usr/local/lib/libgmodule.la  
 /usr/bin/install -c -m 644 .libs/libgmodule.a /usr/local/lib/libgmodule.a  
 ranlib /usr/local/lib/libgmodule.a  
 chmod 644 /usr/local/lib/libgmodule.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/include  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/gmodule/gmodule.h /usr/local/include/gmodule.h  
 make[2]: Leaving directory `/home/chivalry/gmodule'  
 make[1]: Leaving directory `/home/chivalry/gmodule'  
 Making install in gthread  
 make[1]: Entering directory `/home/chivalry/gthread'  
 make[2]: Entering directory `/home/chivalry/gthread'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ../libtool  --mode=install /usr/bin/install -c libgthread.la /usr/local/lib/libgthread.la  
 /usr/bin/install -c .libs/libgthread-1.2.so.0.0.8 /usr/local/lib/libgthread-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libgthread-1.2.so.0 && ln -s libgthread-1.2.so.0.0.8 libgthread-1.2.so.0)  
 (cd /usr/local/lib && rm -f libgthread.so && ln -s libgthread-1.2.so.0.0.8 libgthread.so) 
 /usr/bin/install -c .libs/libgthread.lai /usr/local/lib/libgthread.la  
 /usr/bin/install -c .libs/libgthread.a /usr/local/lib/libgthread.a  
 ranlib /usr/local/lib/libgthread.a  
 chmod 644 /usr/local/lib/libgthread.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 make[2]: Nothing to be done for `install-data-am'.  
 make[2]: Leaving directory `/home/chivalry/gthread'  
 make[1]: Leaving directory `/home/chivalry/gthread'  
 Making install in docs  
 make[1]: Entering directory `/home/chivalry/docs'  
 make[2]: Entering directory `/home/chivalry/docs'  
 make[2]: Nothing to be done for `install-exec-am'.  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/info  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/docs/glib.info /usr/local/info/glib.info  
 make  install-man1  
 make[3]: Entering directory `/home/chivalry/docs'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/man/man1  
  /usr/bin/install -c -m 644 glib-config.1 /usr/local/man/man1/glib-config.1  
 make[3]: Leaving directory `/home/chivalry/docs'  
 make[2]: Leaving directory `/home/chivalry/docs'  
 make[1]: Leaving directory `/home/chivalry/docs'  
 Making install in tests  
 make[1]: Entering directory `/home/chivalry/tests'  
 make[2]: Entering directory `/home/chivalry/tests'  
 make[2]: Nothing to be done for `install-exec-am'.  
 make[2]: Nothing to be done for `install-data-am'.  
 make[2]: Leaving directory `/home/chivalry/tests'  
 make[1]: Leaving directory `/home/chivalry/tests'  
 make: Nothing to be done for `/home/chivalry/Desktop/My Documents/gnomenu/Makefile'.  
 chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ so, even when I want to install gnomenu, it will not let me with the make, which does often work for me. Wtf? Ubuntu, right now, I hate you!!!!  
 so, I am stuck in a tough spot guys. Seriously guys, Wtf? Ubuntu, right now, I hate you!
 bash: so,: command not found  
 chivalry@Chivalrys-Computer:~$ I need help!
 &&&&&&&&&&&&&&&&&&&&&&
[/LIST]
   	 	 	 	 	Man I hope this comes out good on the fourms to read! THis is what is in the odt file.


[/LEFT]
  
OK, so, I think glib is the problem here, and it is taking on my makes. arrrg. I wish I new more, but I never worked with dos. I am a savy comp person, with hardware and software, but not dos and Linux.  Please help. Thank you!  

-gta117

---

### Post by 3Miro on 2009-04-25
What are you trying to install? You should use the graphical Add/Remove or Synaptic and all the packages are listed. People give terminal commands because copy/paste is easier than instructions go here, click there.

If you want more of a Vista look, try kubuntu (don't use anything before 9.04). By default it looks more like windows.

---

### Post by HermanAB on 2009-04-25
Uhmmm...  If you want to run Linux with pointy-clicky wizards just like Windows, then you should use Mandriva or Suse, not Ubuntu.  Each to his own. If you don't like the way Ubuntu does things, then why are fighting with it? You should use a distribution that does things the way you want.  Simple as that.

---

### Post by Dr_Willis on 2009-04-25
I think you need to clarify what it is you are trying to do exactly.
Im not sure what you are trying to do to get a 'vista' look, or wanting to compile. There are vista themes

rereading the post a few times..  it seems this is one of the issues

chivalry@Chivalrys-Computer:~$ **sudo make cd /home/chivalry/Desktop/glib-1.2.8 **


You seem to be merging 2 commands together..  

 the normal way to do things would be similer to 

$ cd directory
$ command you run
$ sudo other commands.

---

### Post by mb_webguy on 2009-04-25
I have no idea why you think you need to use the terminal just to get the look and feel of Vista.  You can do everything from the desktop.

Just right-click the top panel and remove it.  Add the Main Menu applet to the left of the bottom panel, and the Notification Area applet to the right.  Now your bottom panel is almost identical to the Windows Taskbar.

Now if you want to make it sleek like Vista, open System->Synaptic Package Manager and install the emerald and compizconfig-settings-manager packages.  Go to Gnome-Look.org and download some themes.  Gnome themes can be installed by dragging the file to the System->Preferences->Appearance window.  Emerald themes can be installed by clicking the Import button in System->Preferences->Emerald Theme Manager.

You almost never *have* to use the terminal in Ubuntu.  Almost everything *can* be done using a GUI.  However, most of the advice given on this forum will use terminal commands because it's the only way to make sure the advice will apply to everyone.  Not everyone uses the same desktop environment, so descriptions that say "click here, now click here, now click here" won't apply to anyone not using the same desktop environment as the person giving the advice, and also takes a lot longer than "enter this command in the terminal".

---

### Post by ad_267 on 2009-04-25
What are you trying to do? You shouldn't have to use the terminal at all to change the appearance of Ubuntu, and you definitely shouldn't have to compile those applications. See [installing software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware").

If you tell us what applications you're trying to install and what you're trying to achieve then we can probably help you to do this a lot easier.

---

### Post by 3rdalbum on 2009-04-25
I *really* wouldn't go compiling a new version of Glib! That's a very low-level toolkit; get it wrong and your system breaks. Every other thing in your system has been compiled for a different version of glib as well. In short, don't touch it unless you absolutely must.

As for Gnomenu, is this what you're looking for? ([http://martinnotes.com/2008/12/14/gnomenu](http://martinnotes.com/2008/12/14/gnomenu)). Honestly, look for a Debian package before trying to compile, and don't blame Ubuntu if you don't know how to compile software (and you don't need to).

---

### Post by gta117 on 2009-04-26
Hey guys, thanks for the response! I was watching some soccer, so I got lost a little hahaha!!!!


Oh, I do not like the other linux distributions, and I am most familiar with Ubuntu. But I was told Ubuntu was the easiest to use too. Hahaha, it can be, but not with installing. 


Ok, I am trying to install gnomenu, but glib is screwing me up. For some reason, when I go to make install like the stupid (and they are vauge, stupid instructions) install rules say, I get the quote I posted above. Werid eh? 


Also, PLEASE check out the attachment. It has the problem Really spelled out. It shows the errors in the terminal AND what I tried to do, AND what was the result. 


Thank you guys!

-gta117

---

### Post by Peasantoid on 2009-04-26
There are Vista themes [of varying quality] available at [http://gnome-look.org/](http://gnome-look.org/).

---

### Post by ad_267 on 2009-04-26
It looks like there's a .deb package at [https://launchpad.net/gnomenu/trunk/1.6](https://launchpad.net/gnomenu/trunk/1.6).

---

### Post by gta117 on 2009-04-26
thanks for the reply, but... there is 1.7 out


I am trying to get 1.7. In fact, I have the file. I just uploaded it. Anyways, the instructions SUCK FOR IT. Seriously, someone was really unaware of people who are new when it comes to it....


-gta117

---

### Post by Peasantoid on 2009-04-26
Why do you need 1.7 so badly?

I recommend installing 1.6 and then upgrading it to 1.7 when you're able to compile it successfully.

---

### Post by gta117 on 2009-04-26
ok, I will take your advice, but now we have to figure out why I can not install anything still....

Because glib or something with the make file is interfering with it....


-gta117

---

### Post by Peasantoid on 2009-04-26
(never mind)

---

### Post by gta117 on 2009-04-26
yes, nothing man. Please consult the upload I had on the first page in the topic starter. It has ALL what I had in the terminal. (with me spacing out the stuff I typed to help you skim and read.)

its in open office format.


-gta117

---

### Post by gta117 on 2009-04-26
guys, I sure could use some help on this! I am so sorry, but for days I have been working on this. :( I can't be on here all night helping people in the mean time. :(

-gta117

---

### Post by cdwillis on 2009-04-26
Download the file from gnome-look
extract to your desktop
open a terminal
cd /home/YOURUSERNAME/Desktop/gnomenu
sudo make install

---

### Post by Dr_Willis on 2009-04-26
Most people in the forums will totally ignore such attachments

oddly enough. I cant even OPEN it here on a clean 9.04 install.

Summarize the problem in the forum thread. so that people elseware can search and discover the problem/fix later if they need to.


Ubuntu is GREAT for installing.   The repositories have most everything i need, and the package manager has features for both beginners and hard-core users.  

 The fact you are having problems compiling somthing has very little do do with Ubuntu. Your problem  IS giveing a good example of why a 'package manager system' is such a Important feature in a linux disrto.

---

### Post by Dr_Willis on 2009-04-26
downloaded the packages from the following site 

[https://launchpad.net/gnomenu/trunk/1.6](https://launchpad.net/gnomenu/trunk/1.6)

I also had to install the following 

**sudo apt-get install deskbar-applet python-xlib **

then installed the packages with

sudo dpkg -i gnomenu*


Everything Installed.  I just cant seem to find it in the 'add to panel' listing or anywhere else..  :P  Off to read the docs.

---

### Post by Dr_Willis on 2009-04-26
Deb packages dident seem to work, so i tried the source.. also failed.
i did NOT see any information on 'glib' problems.. Heres a summary of what i tried.

###################################
Notes on how i tried to install gnomenu - Just to see if i could...

Commands from the Command line - using the source. Not the debs.

 # needed packages according to the docs

   **sudo apt-get install python-xdg python-cairo python-gconf python-xlib deskbar-applet**

# needed for most compiling stuff   
  **sudo apt-get install build-essential** 


# Now to get the files and try to get it running

  [B]mkdir GnomenuWork
  cd GnomenuWork/
  wget [http://launchpad.net/gnomenu/trunk/1.8/+download/gnomenu-1.8.tar.gz](http://launchpad.net/gnomenu/trunk/1.8/+download/gnomenu-1.8.tar.gz)
  tar xzvf gnomenu-1.8.tar.gz 
  cd gnomenu/
  sudo make install[/B]
   
# It installed - no errors
# Try to run it

**GnoMenu.py **
###############################


It 'runs' , nothing appears. console 'blocked' then eventually a min or 2 later.. it returns. No errors no messages

I am using Ubuntu 9.04 by the way :)

---

### Post by Dr_Willis on 2009-04-26
AHA - it did work. :)   as soon as i checked the 'add to panel' listing again. it was there.  


So it does work.  its just seems Ugly and useless to me. :)



:lolflag:

---

### Post by HermanAB on 2009-04-26
Hmmm, you are trying to drive a square peg into a round hole with a sledge hammer.

If you really want a different 'look' then you should not use Ubuntu.  You should rather find a distribution that already looks the way you want!

For example Mandriva Linux with KDE4 looks much better than Vista.  All you need to do is download and install that one, you need not change anything, it has already been done for you.

---

### Post by gta117 on 2009-04-26
> **Dr_Willis said:**
> Most people in the forums will totally ignore such attachments

oddly enough. I cant even OPEN it here on a clean 9.04 install.

Summarize the problem in the forum thread. so that people elseware can search and discover the problem/fix later if they need to.


Ubuntu is GREAT for installing.   The repositories have most everything i need, and the package manager has features for both beginners and hard-core users.  

 The fact you are having problems compiling somthing has very little do do with Ubuntu. Your problem  IS giveing a good example of why a 'package manager system' is such a Important feature in a linux disrto.

[LEFT]
[LIST]
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ sudo make  
 cd /home/chivalry/Desktop/glib-1.2.8 && /home/chivalry/Desktop/glib-1.2.8/missing automake --gnu --include-deps Makefile  
 cd: 1: can't cd to /home/chivalry/Desktop/glib-1.2.8  
 make: *** [/home/chivalry/Desktop/glib-1.2.8/Makefile.in] Error 2  
[*]   	 	 	 	 	 	  &&&&&&&&&&&&&&&&&&&&&&
 chivalry@Chivalrys-Computer:~$ ?  
 bash: ?: command not found  
 chivalry@Chivalrys-Computer:~$ space  
 bash: space: command not found  
 chivalry@Chivalrys-Computer:~$ ok, so whats up with that?  
 bash: ok,: command not found  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ sudo make install  
 cd /home/chivalry/Desktop/glib-1.2.8 && /home/chivalry/Desktop/glib-1.2.8/missing automake --gnu --include-deps Makefile  
 cd: 1: can't cd to /home/chivalry/Desktop/glib-1.2.8  
 make: *** [/home/chivalry/Desktop/glib-1.2.8/Makefile.in] Error 2  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ sudo make uninstall  
 cd /home/chivalry/Desktop/glib-1.2.8 && /home/chivalry/Desktop/glib-1.2.8/missing automake --gnu --include-deps Makefile  
 cd: 1: can't cd to /home/chivalry/Desktop/glib-1.2.8  
 make: *** [/home/chivalry/Desktop/glib-1.2.8/Makefile.in] Error 2  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ lets put the folders on the desk?  
 bash: lets: command not found  
 chivalry@Chivalrys-Computer:~$  
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ make  
 make  all-recursive  
 make[1]: Entering directory `/home/chivalry'  
 Making all in .  
 make[2]: Entering directory `/home/chivalry'  
 make[2]: Leaving directory `/home/chivalry'  
 Making all in gmodule  
 make[2]: Entering directory `/home/chivalry/gmodule'  
 make[2]: Nothing to be done for `all'.  
 make[2]: Leaving directory `/home/chivalry/gmodule'  
 Making all in gthread  
 make[2]: Entering directory `/home/chivalry/gthread'  
 make[2]: Nothing to be done for `all'.  
 make[2]: Leaving directory `/home/chivalry/gthread'  
 Making all in docs  
 make[2]: Entering directory `/home/chivalry/docs'  
 make[2]: Nothing to be done for `all'.  
 make[2]: Leaving directory `/home/chivalry/docs'  
 Making all in tests  
 make[2]: Entering directory `/home/chivalry/tests'  
 make[2]: Nothing to be done for `all'.  
 make[2]: Leaving directory `/home/chivalry/tests'  
 make[1]: Leaving directory `/home/chivalry'  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ ok....  
 bash: ok....: command not found  
 chivalry@Chivalrys-Computer:~$ sudo make install  
[*]   	 	 	 	 	 	  Making install in .  
 make[1]: Entering directory `/home/chivalry'  
 make[2]: Entering directory `/home/chivalry'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ./libtool  --mode=install /usr/bin/install -c libglib.la /usr/local/lib/libglib.la  
 /usr/bin/install -c .libs/libglib-1.2.so.0.0.8 /usr/local/lib/libglib-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libglib-1.2.so.0 && ln -s libglib-1.2.so.0.0.8 libglib-1.2.so.0)  
 (cd /usr/local/lib && rm -f libglib.so && ln -s libglib-1.2.so.0.0.8 libglib.so)  
 /usr/bin/install -c .libs/libglib.lai /usr/local/lib/libglib.la  
 /usr/bin/install -c .libs/libglib.a /usr/local/lib/libglib.a  
 ranlib /usr/local/lib/libglib.a  
 chmod 644 /usr/local/lib/libglib.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/bin  
  /usr/bin/install -c  glib-config /usr/local/bin/glib-config  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib/glib/include  
  /usr/bin/install -c -m 644 glibconfig.h /usr/local/lib/glib/include/glibconfig.h  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/share/aclocal  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/glib.m4 /usr/local/share/aclocal/glib.m4  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/include  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/glib.h /usr/local/include/glib.h  
 make[2]: Leaving directory `/home/chivalry'  
 make[1]: Leaving directory `/home/chivalry'  
 Making install in gmodule  
 make[1]: Entering directory `/home/chivalry/gmodule'  
 make[2]: Entering directory `/home/chivalry/gmodule'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ../libtool  --mode=install /usr/bin/install -c -m 644 libgmodule.la /usr/local/lib/libgmodule.la 
 /usr/bin/install -c -m 644 .libs/libgmodule-1.2.so.0.0.8 /usr/local/lib/libgmodule-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libgmodule-1.2.so.0 && ln -s libgmodule-1.2.so.0.0.8 libgmodule-1.2.so.0)  
 (cd /usr/local/lib && rm -f libgmodule.so && ln -s libgmodule-1.2.so.0.0.8 libgmodule.so) 
 /usr/bin/install -c -m 644 .libs/libgmodule.lai /usr/local/lib/libgmodule.la  
 /usr/bin/install -c -m 644 .libs/libgmodule.a /usr/local/lib/libgmodule.a  
 ranlib /usr/local/lib/libgmodule.a  
 chmod 644 /usr/local/lib/libgmodule.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/include  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/gmodule/gmodule.h /usr/local/include/gmodule.h  
 make[2]: Leaving directory `/home/chivalry/gmodule'  
 make[1]: Leaving directory `/home/chivalry/gmodule'  
 Making install in gthread  
 make[1]: Entering directory `/home/chivalry/gthread'  
 make[2]: Entering directory `/home/chivalry/gthread'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ../libtool  --mode=install /usr/bin/install -c libgthread.la /usr/local/lib/libgthread.la  
 /usr/bin/install -c .libs/libgthread-1.2.so.0.0.8 /usr/local/lib/libgthread-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libgthread-1.2.so.0 && ln -s libgthread-1.2.so.0.0.8 libgthread-1.2.so.0)  
 (cd /usr/local/lib && rm -f libgthread.so && ln -s libgthread-1.2.so.0.0.8 libgthread.so) 
 /usr/bin/install -c .libs/libgthread.lai /usr/local/lib/libgthread.la  
 /usr/bin/install -c .libs/libgthread.a /usr/local/lib/libgthread.a  
 ranlib /usr/local/lib/libgthread.a  
 chmod 644 /usr/local/lib/libgthread.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 make[2]: Nothing to be done for `install-data-am'.  
 make[2]: Leaving directory `/home/chivalry/gthread'  
 make[1]: Leaving directory `/home/chivalry/gthread'  
 Making install in docs  
 make[1]: Entering directory `/home/chivalry/docs'  
 make[2]: Entering directory `/home/chivalry/docs'  
 make[2]: Nothing to be done for `install-exec-am'.  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/info  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/docs/glib.info /usr/local/info/glib.info  
 make  install-man1  
 make[3]: Entering directory `/home/chivalry/docs'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/man/man1  
  /usr/bin/install -c -m 644 glib-config.1 /usr/local/man/man1/glib-config.1  
 make[3]: Leaving directory `/home/chivalry/docs'  
 make[2]: Leaving directory `/home/chivalry/docs'  
 make[1]: Leaving directory `/home/chivalry/docs'  
 Making install in tests  
 make[1]: Entering directory `/home/chivalry/tests'  
 make[2]: Entering directory `/home/chivalry/tests'  
 make[2]: Nothing to be done for `install-exec-am'.  
 make[2]: Nothing to be done for `install-data-am'.  
 make[2]: Leaving directory `/home/chivalry/tests'  
 make[1]: Leaving directory `/home/chivalry/tests'  
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ nothing to be done? OMG! >_< Ok, lets uninstall it...  
 bash: Ok,: No such file or directory  
 chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ sudo make uninstall  
[*]   	 	 	 	 	 	  Making uninstall in .  
 make[1]: Entering directory `/home/chivalry'  
 list='libglib.la'; for p in $list; do \ 
 	  /bin/sh ./libtool  --mode=uninstall rm -f /usr/local/lib/$p; \  
 	done  
 rm -f /usr/local/lib/libglib.la /usr/local/lib/libglib-1.2.so.0.0.8 /usr/local/lib/libglib-1.2.so.0 /usr/local/lib/libglib.so /usr/local/lib/libglib.a  
 list='glib-config'; for p in $list; do \  
 	  rm -f /usr/local/bin/`echo $p|sed 's,x,x,'`; \  
 	done  
 list='glibconfig.h'; for p in $list; do \  
 	  rm -f /usr/local/lib/glib/include/$p; \  
 	done  
 list='glib.m4'; for p in $list; do \  
 	  rm -f /usr/local/share/aclocal/$p; \ 
 	done  
 list='glib.h'; for p in $list; do \  
 	  rm -f /usr/local/include/$p; \  
 	done  
 make[1]: Leaving directory `/home/chivalry'  
 Making uninstall in gmodule  
 make[1]: Entering directory `/home/chivalry/gmodule'  
 list='libgmodule.la libgplugin_a.la libgplugin_b.la'; for p in $list; do \  
 	  /bin/sh ../libtool  --mode=uninstall rm -f /usr/local/lib/$p; \  
 	done  
 rm -f /usr/local/lib/libgmodule.la /usr/local/lib/libgmodule-1.2.so.0.0.8 /usr/local/lib/libgmodule-1.2.so.0 /usr/local/lib/libgmodule.so /usr/local/lib/libgmodule.a  
 list='gmodule.h'; for p in $list; do \  
 	  rm -f /usr/local/include/$p; \  
 	done  
 make[1]: Leaving directory `/home/chivalry/gmodule'  
 Making uninstall in gthread  
 make[1]: Entering directory `/home/chivalry/gthread'  
 list='libgthread.la'; for p in $list; do \  
 	  /bin/sh ../libtool  --mode=uninstall rm -f /usr/local/lib/$p; \  
 	done  
 rm -f /usr/local/lib/libgthread.la /usr/local/lib/libgthread-1.2.so.0.0.8 /usr/local/lib/libgthread-1.2.so.0 /usr/local/lib/libgthread.so /usr/local/lib/libgthread.a  
 make[1]: Leaving directory `/home/chivalry/gthread'  
 Making uninstall in docs  
 make[1]: Entering directory `/home/chivalry/docs'  
 :  
 install-info(glib.info): no entry for file `glib'  
 list='glib.info'; \  
 	for file in $list; do \  
 	  (cd /usr/local/info && rm -f $file $file-[0-9] $file-[0-9][0-9]); \  
 	done  
 make  uninstall-man1  
 make[2]: Entering directory `/home/chivalry/docs'  
  rm -f /usr/local/man/man1/glib-config.1  
 make[2]: Leaving directory `/home/chivalry/docs'  
 make[1]: Leaving directory `/home/chivalry/docs'  
 Making uninstall in tests  
 make[1]: Entering directory `/home/chivalry/tests'  
 make[1]: Nothing to be done for `uninstall'.  
 make[1]: Leaving directory `/home/chivalry/tests'  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ you got to be kidding me! Well, lets ignore it and install what I wanted to install...  
 bash: you: command not found  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$ sudo make install '/home/chivalry/Desktop/My Documents/gnomenu/Makefile'  
 Making install in .  
 make[1]: Entering directory `/home/chivalry'  
 make[2]: Entering directory `/home/chivalry'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ./libtool  --mode=install /usr/bin/install -c libglib.la /usr/local/lib/libglib.la  
 /usr/bin/install -c .libs/libglib-1.2.so.0.0.8 /usr/local/lib/libglib-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libglib-1.2.so.0 && ln -s libglib-1.2.so.0.0.8 libglib-1.2.so.0)  
 (cd /usr/local/lib && rm -f libglib.so && ln -s libglib-1.2.so.0.0.8 libglib.so)  
 /usr/bin/install -c .libs/libglib.lai /usr/local/lib/libglib.la  
 /usr/bin/install -c .libs/libglib.a /usr/local/lib/libglib.a  
 ranlib /usr/local/lib/libglib.a  
 chmod 644 /usr/local/lib/libglib.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/bin  
  /usr/bin/install -c  glib-config /usr/local/bin/glib-config  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib/glib/include  
  /usr/bin/install -c -m 644 glibconfig.h /usr/local/lib/glib/include/glibconfig.h  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/share/aclocal  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/glib.m4 /usr/local/share/aclocal/glib.m4  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/include  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/glib.h /usr/local/include/glib.h  
 make[2]: Leaving directory `/home/chivalry'  
 make[1]: Leaving directory `/home/chivalry'  
 Making install in gmodule  
 make[1]: Entering directory `/home/chivalry/gmodule'  
 make[2]: Entering directory `/home/chivalry/gmodule'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ../libtool  --mode=install /usr/bin/install -c -m 644 libgmodule.la /usr/local/lib/libgmodule.la 
 /usr/bin/install -c -m 644 .libs/libgmodule-1.2.so.0.0.8 /usr/local/lib/libgmodule-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libgmodule-1.2.so.0 && ln -s libgmodule-1.2.so.0.0.8 libgmodule-1.2.so.0)  
 (cd /usr/local/lib && rm -f libgmodule.so && ln -s libgmodule-1.2.so.0.0.8 libgmodule.so) 
 /usr/bin/install -c -m 644 .libs/libgmodule.lai /usr/local/lib/libgmodule.la  
 /usr/bin/install -c -m 644 .libs/libgmodule.a /usr/local/lib/libgmodule.a  
 ranlib /usr/local/lib/libgmodule.a  
 chmod 644 /usr/local/lib/libgmodule.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/include  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/gmodule/gmodule.h /usr/local/include/gmodule.h  
 make[2]: Leaving directory `/home/chivalry/gmodule'  
 make[1]: Leaving directory `/home/chivalry/gmodule'  
 Making install in gthread  
 make[1]: Entering directory `/home/chivalry/gthread'  
 make[2]: Entering directory `/home/chivalry/gthread'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/lib  
 /bin/sh ../libtool  --mode=install /usr/bin/install -c libgthread.la /usr/local/lib/libgthread.la  
 /usr/bin/install -c .libs/libgthread-1.2.so.0.0.8 /usr/local/lib/libgthread-1.2.so.0.0.8  
 (cd /usr/local/lib && rm -f libgthread-1.2.so.0 && ln -s libgthread-1.2.so.0.0.8 libgthread-1.2.so.0)  
 (cd /usr/local/lib && rm -f libgthread.so && ln -s libgthread-1.2.so.0.0.8 libgthread.so) 
 /usr/bin/install -c .libs/libgthread.lai /usr/local/lib/libgthread.la  
 /usr/bin/install -c .libs/libgthread.a /usr/local/lib/libgthread.a  
 ranlib /usr/local/lib/libgthread.a  
 chmod 644 /usr/local/lib/libgthread.a  
 PATH="$PATH:/sbin" ldconfig -n /usr/local/lib  
 ---------------------------------------------------------------------- 
 Libraries have been installed in:  
    /usr/local/lib  
 

 If you ever happen to want to link against installed libraries  
 in a given directory, LIBDIR, you must either use libtool, and  
 specify the full pathname of the library, or use `-LLIBDIR'  
 flag during linking and do at least one of the following:  
    - add LIBDIR to the `LD_LIBRARY_PATH' environment variable  
      during execution  
    - add LIBDIR to the `LD_RUN_PATH' environment variable  
      during linking  
    - use the `-Wl,--rpath -Wl,LIBDIR' linker flag  
    - have your system administrator add LIBDIR to `/etc/ld.so.conf'  
 

 See any operating system documentation about shared libraries for  
 more information, such as the ld(1) and ld.so(8) manual pages.  
 ---------------------------------------------------------------------- 
 make[2]: Nothing to be done for `install-data-am'.  
 make[2]: Leaving directory `/home/chivalry/gthread'  
 make[1]: Leaving directory `/home/chivalry/gthread'  
 Making install in docs  
 make[1]: Entering directory `/home/chivalry/docs'  
 make[2]: Entering directory `/home/chivalry/docs'  
 make[2]: Nothing to be done for `install-exec-am'.  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/info  
  /usr/bin/install -c -m 644 /home/chivalry/Desktop/glib-1.2.8/docs/glib.info /usr/local/info/glib.info  
 make  install-man1  
 make[3]: Entering directory `/home/chivalry/docs'  
 /bin/sh /home/chivalry/Desktop/glib-1.2.8/mkinstalldirs /usr/local/man/man1  
  /usr/bin/install -c -m 644 glib-config.1 /usr/local/man/man1/glib-config.1  
 make[3]: Leaving directory `/home/chivalry/docs'  
 make[2]: Leaving directory `/home/chivalry/docs'  
 make[1]: Leaving directory `/home/chivalry/docs'  
 Making install in tests  
 make[1]: Entering directory `/home/chivalry/tests'  
 make[2]: Entering directory `/home/chivalry/tests'  
 make[2]: Nothing to be done for `install-exec-am'.  
 make[2]: Nothing to be done for `install-data-am'.  
 make[2]: Leaving directory `/home/chivalry/tests'  
 make[1]: Leaving directory `/home/chivalry/tests'  
 make: Nothing to be done for `/home/chivalry/Desktop/My Documents/gnomenu/Makefile'.  
 chivalry@Chivalrys-Computer:~$  
 chivalry@Chivalrys-Computer:~$  
 &&&&&&&&&&&&&&&&&&&&&&
[*]   	 	 	 	 	 	  chivalry@Chivalrys-Computer:~$ so, even when I want to install gnomenu, it will not let me with the make, which does often work for me. Wtf? Ubuntu, right now, I hate you!!!!  
 so, I am stuck in a tough spot guys. Seriously guys, Wtf? Ubuntu, right now, I hate you!
 bash: so,: command not found  
 chivalry@Chivalrys-Computer:~$ I need help!
 &&&&&&&&&&&&&&&&&&&&&&
[/LIST]
   	 	 	 	 	Man I hope this comes out good on the fourms to read! THis is what is in the odt file.

-gta117
[/LEFT]

---

### Post by gta117 on 2009-04-26
> **HermanAB said:**
> Hmmm, you are trying to drive a square peg into a round hole with a sledge hammer.

If you really want a different 'look' then you should not use Ubuntu.  You should rather find a distribution that already looks the way you want!

For example Mandriva Linux with KDE4 looks much better than Vista.  All you need to do is download and install that one, you need not change anything, it has already been done for you.


ubuntu is better. I also have worked with it the most. And, I have 2 others right now with it, who want to look changed, and 2 more to follow. Doing you guys a good favour right now. I posted my text doc on the forums. Works I guess with bulletins. :)


Cheers!

-gta117

---

### Post by Dr_Willis on 2009-04-26
You really COULD of edited out all the rambling commentary. so we can see the exact problems easier.  I cant see why you are even messing with glib.

if you wanted to add comments to  what you were doing you could of done these between the commands.

**# This is a comment The shell wont try to parse this line - thus giving cleaner output**

Im still not clear on what/why you need to mess with glib at all. but lets just go through the error messages

###########################################################################

chivalry@Chivalrys-Computer:~$ sudo make
      **cd /home/chivalry/Desktop/glib-1.2.8 && /home/chivalry/Desktop/glib-1.2.8/missing automake --gnu --include-deps Makefile**
      cd: 1: can't cd to /home/chivalry/Desktop/glib-1.2.8
      make: *** [/home/chivalry/Desktop/glib-1.2.8/Makefile.in] Error 2
    

*Typos on the command line.*

    * chivalry@Chivalrys-Computer:~$ sudo make install
      cd /home/chivalry/Desktop/glib-1.2.8 && /home/chivalry/Desktop/glib-1.2.8/missing automake --gnu --include-deps Makefile

[I]
again typos..[/I]
      
    * chivalry@Chivalrys-Computer:~$ sudo make uninstall
      cd /home/chivalry/Desktop/glib-1.2.8 && /home/chivalry/Desktop/glib-1.2.8/missing automake --gnu --include-deps Makefile
      cd: 1: can't cd to /home/chivalry/Desktop/glib-1.2.8
      make: *** [/home/chivalry/Desktop/glib-1.2.8/Makefile.in] Error 2
      &&&&&&&&&&&&&&&&&&&&&&
    

      chivalry@Chivalrys-Computer:~$ sudo make install


The Normal 'method' would be to extract the source to a directory, then cd into the directory, then use all the various 'make' commands as needed


      ----------------------------------------------------------------------
      Libraries have been installed in:
      /usr/local/lib

*So it seems to actually Installed for you?*



    * chivalry@Chivalrys-Computer:~$ nothing to be done? OMG! >_< Ok, lets uninstall it...


*Correct - IF the thing 'compiles' properly rerunning make wont force a recompile since it sees that it compiled properly in the first place.*


    

      &&&&&&&&&&&&&&&&&&&&&&
    * chivalry@Chivalrys-Computer:~$ so, even when I want to install gnomenu, it will not let me with the make, which does often work for me. Wtf? Ubuntu, right now, I hate you!!!!
      so, I am stuck in a tough spot guys. Seriously guys, Wtf? Ubuntu, right now, I hate you!
      bash: so,: command not found
      chivalry@Chivalrys-Computer:~$ I need help!
      &&&&&&&&&&&&&&&&&&&&&&

I think we are barking up the wrong tree.. and not only the wrong tree.. its in the wrong park. 


If you want 'realtime' help feel free to come to  the irc help channel. theres plenty of people there.

Pidgin can do irc. or you can install the xchat irc client.


**$ sudo apt-get install xchat**

run xchat, connect to the following

server irc.freenode.net
channel #ubuntu

---

### Post by cdwillis on 2009-04-26
Did you try the steps I typed out earlier? I don't know why you're messing with glib. 

Download the file from gnome-look.org to the desktop
right click it and extract here
open terminal
cd /home/chivarly/Desktop/gnomenu
sudo make install

That should be all you need. I can't tell if you're trolling or genuinely in need of help.

---

### Post by gta117 on 2009-04-26
sorry guys, I have been out of it lately, I should have realized to crop out the rubbish. 


ok, I will try it now (IRC). I am on now, thanks!


EDIT: No, anything with make WILL not work. Glib is possesed. It keeps using its make file. :(

-gta117

---

### Post by Dr_Willis on 2009-04-26
Little script to install gnomenu
good luck



```
#!/bin/bash

# save this script to some file like 'installit.bash' then run with
# bash installit.bash


echo "Silly Install Script for  the gnomenu thing"


echo "Installing the needed extra packages first"

sudo apt-get install python-xdg python-cairo python-gconf python-xlib deskbar-applet

# needed for most compiling stuff
sudo apt-get install build-essential


echo "Now to get the files and try to get it running"

mkdir GnomenuWork
cd GnomenuWork/
wget http://launchpad.net/gnomenu/trunk/1.8/+download/gnomenu-1.8.tar.gz

echo "Got the File, now to extract and install"
echo "the thing dosent really compile at all"

tar xzvf gnomenu-1.8.tar.gz
cd gnomenu/

sudo make install


echo "Done"




```

---

### Post by gta117 on 2009-04-26
Also, if you have a make file conflict, go to your home folder, look for makefile, and delete it. That works wonders man!



Thanks guys!


-gta117

---

