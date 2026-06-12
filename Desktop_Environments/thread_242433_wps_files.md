---
title: "wps files"
date: 2006-08-23
forum: Desktop Environments
---

### Post by loserboy on 2006-08-23
i'm trying to get my gf to switch from ms to ubuntu, she wants to use it, but she needs to be able to open .wps files (i think its works 6.0 files).

the problem is she doesnt even have the software to do it on windows, its her  teacher who e-mails her uses that format, so she needs to convert it or view it.

ive done some searching but havent come up with anything, so does anyone know of anything.

thanks

---

### Post by BLTicklemonster on 2006-09-21
Leave it to Microsoft to do something like that. We have people who send us stuff in wps all the time, and I keep wondering why the heck don't they just copy and post the contents into the email body?

In the meantime, this is as close as I have been able to get: [http://libwps.sourceforge.net/](http://libwps.sourceforge.net/) and I have no idea how to compile anything, so I guess I'll email my daughter's cheerleading coach and ask her to copy and paste. 

Good luck.

---

### Post by dgermann on 2006-09-21
Hi--

I had the same problem a couple weeks ago.

What I eventually did was to go to the Microsoft site and download two files, install them to a WinXP box I have, and then copy and paste (special) over into OOo so I could read it in my linux boxes.

Not very ideal, but it worked.

:- Doug.

---

### Post by BLTicklemonster on 2006-09-21
So far, I have gotten this far:

compiled libwpd-0.8.6 but had to get libgsf dev from synaptic first. Tried to compile writerperfect-0.7.1 (because I was naive and thought libpwd would magically do something in open office, silly me) and it turns out that it needs libwpd-0.8.0 to compile, so I'm compiling that one right now... whereupon I get a recursive error:

> ticklemonster@ticklemonster:~/Desktop/writerperfect-0.7.1$ make install
Making install in build
make[1]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build'
Making install in win32
make[2]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build/win32'
make[3]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build/win32'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build/win32'
make[2]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build/win32'
make[2]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build'
make[3]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build'
make[2]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build'
make[1]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/build'
Making install in filter
make[1]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/filter'
make[2]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/filter'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/filter'
make[1]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/filter'
Making install in ooo
make[1]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/ooo'
make[2]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/ooo'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/ooo'make[1]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/ooo'Making install in packaging
make[1]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging'
Making install in NSIS
make[2]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging/NSIS'
make[3]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging/NSIS'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging/NSIS'
make[2]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging/NSIS'
make[2]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging'
make[3]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging'
make[2]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging'
make[1]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/packaging'
Making install in wpd2sxw
make[1]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/wpd2sxw'
make[2]: Entering directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/wpd2sxw'
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"
  /bin/sh ../libtool --mode=install /usr/bin/install -c 'wpd2sxw' '/usr/local/bin/wpd2sxw'
/usr/bin/install -c wpd2sxw /usr/local/bin/wpd2sxw
/usr/bin/install: cannot create regular file `/usr/local/bin/wpd2sxw': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/wpd2sxw'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/ticklemonster/Desktop/writerperfect-0.7.1/wpd2sxw'
make: *** [install-recursive] Error 1


So me being of little patience, I give up.

Anyone want to follow this through and help, please have at it!

---

### Post by BLTicklemonster on 2006-09-21
> **dgermann said:**
> Hi--

I had the same problem a couple weeks ago.

What I eventually did was to go to the Microsoft site and download two files, install them to a WinXP box I have, and then copy and paste (special) over into OOo so I could read it in my linux boxes.

Not very ideal, but it worked.

:- Doug.

Cool, can you be more specific? I have a partition that is fat32 that I can share around with... but I don't have works. You need works, don't you?

---

### Post by skymt on 2006-09-21
> **BLTicklemonster said:**
> So me being of little patience, I give up.

Anyone want to follow this through and help, please have at it!

Do what he did, but use "*sudo* make me a sand^W^Winstall". ;)  Or, even better, "sudo checkinstall".

---

### Post by BLTicklemonster on 2006-09-21
> **skymt said:**
> Do what he did, but use "*sudo* make me a sand^W^Winstall". ;)  Or, even better, "sudo checkinstall".

"*sudo* make me a sand^W^Winstall" ?

Um, I'll try the checkinstall, but I think it may have something to do with the later version I installed earlier.


> ticklemonster@ticklemonster:~/libwpd-0.8.0$ sudo make install
Password: billgatesisgay
Making install in src
make[1]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src'
Making install in lib
make[2]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/lib'
make[3]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/lib'
/bin/sh ../../mkinstalldirs /usr/local/lib
 /bin/sh ../../libtool --mode=install /usr/bin/install -c  libwpd-0.8.la /usr/local/lib/libwpd-0.8.la
/usr/bin/install -c .libs/libwpd-0.8.so.8.0.0 /usr/local/lib/libwpd-0.8.so.8.0.0(cd /usr/local/lib && rm -f libwpd-0.8.so.8 && ln -s libwpd-0.8.so.8.0.0 libwpd-0.8.so.8)
(cd /usr/local/lib && rm -f libwpd-0.8.so && ln -s libwpd-0.8.so.8.0.0 libwpd-0.8.so)
/usr/bin/install -c .libs/libwpd-0.8.lai /usr/local/lib/libwpd-0.8.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /bin/sh ../../libtool --mode=install /usr/bin/install -c  libwpd-stream-0.8.la /usr/local/lib/libwpd-stream-0.8.la
/usr/bin/install -c .libs/libwpd-stream-0.8.so.8.0.0 /usr/local/lib/libwpd-stream-0.8.so.8.0.0
(cd /usr/local/lib && rm -f libwpd-stream-0.8.so.8 && ln -s libwpd-stream-0.8.so.8.0.0 libwpd-stream-0.8.so.8)
(cd /usr/local/lib && rm -f libwpd-stream-0.8.so && ln -s libwpd-stream-0.8.so.8.0.0 libwpd-stream-0.8.so)
/usr/bin/install -c .libs/libwpd-stream-0.8.lai /usr/local/lib/libwpd-stream-0.8.la
PATH="$PATH:/sbin" ldconfig -n /usr/local/lib
----------------------------------------------------------------------
Libraries have been installed in:
   /usr/local/lib

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
/bin/sh ../../mkinstalldirs /usr/local/include/libwpd-0.8/libwpd
 /usr/bin/install -c -m 644 libwpd.h /usr/local/include/libwpd-0.8/libwpd/libwpd.h
 /usr/bin/install -c -m 644 libwpd_types.h /usr/local/include/libwpd-0.8/libwpd/libwpd_types.h
 /usr/bin/install -c -m 644 WPXStream.h /usr/local/include/libwpd-0.8/libwpd/WPXStream.h
 /usr/bin/install -c -m 644 WPXProperty.h /usr/local/include/libwpd-0.8/libwpd/WPXProperty.h
 /usr/bin/install -c -m 644 WPXPropertyList.h /usr/local/include/libwpd-0.8/libwpd/WPXPropertyList.h
 /usr/bin/install -c -m 644 WPXString.h /usr/local/include/libwpd-0.8/libwpd/WPXString.h
 /usr/bin/install -c -m 644 WPXPropertyListVector.h /usr/local/include/libwpd-0.8/libwpd/WPXPropertyListVector.h
 /usr/bin/install -c -m 644 WPDocument.h /usr/local/include/libwpd-0.8/libwpd/WPDocument.h
 /usr/bin/install -c -m 644 WPXHLListenerImpl.h /usr/local/include/libwpd-0.8/libwpd/WPXHLListenerImpl.h
/bin/sh ../../mkinstalldirs /usr/local/include/libwpd-0.8/libwpd
 /usr/bin/install -c -m 644 GSFStream.h /usr/local/include/libwpd-0.8/libwpd/GSFStream.h
make[3]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/lib'
make[2]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/lib'
Making install in conv
make[2]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/conv'
Making install in raw
make[3]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/conv/raw'
make[4]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/conv/raw'
/bin/sh ../../../mkinstalldirs /usr/local/bin
  /bin/sh ../../../libtool --mode=install /usr/bin/install -c wpd2raw /usr/local/bin/wpd2raw
/usr/bin/install -c .libs/wpd2raw /usr/local/bin/wpd2raw
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/conv/raw'
make[3]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/conv/raw'
Making install in html
make[3]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/conv/html'
make[4]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/conv/html'
/bin/sh ../../../mkinstalldirs /usr/local/bin
  /bin/sh ../../../libtool --mode=install /usr/bin/install -c wpd2html /usr/local/bin/wpd2html
/usr/bin/install -c .libs/wpd2html /usr/local/bin/wpd2html
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/conv/html'
make[3]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/conv/html'
Making install in text
make[3]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/conv/text'
make[4]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/conv/text'
/bin/sh ../../../mkinstalldirs /usr/local/bin
  /bin/sh ../../../libtool --mode=install /usr/bin/install -c wpd2text /usr/local/bin/wpd2text
/usr/bin/install -c .libs/wpd2text /usr/local/bin/wpd2text
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/conv/text'
make[3]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/conv/text'
make[3]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/conv'
make[4]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src/conv'
make[4]: Nothing to be done for `install-exec-am'.
make[4]: Nothing to be done for `install-data-am'.
make[4]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/conv'
make[3]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/conv'
make[2]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src/conv'
make[2]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src'
make[3]: Entering directory `/home/ticklemonster/libwpd-0.8.0/src'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src'
make[2]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src'
make[1]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/src'
Making install in build
make[1]: Entering directory `/home/ticklemonster/libwpd-0.8.0/build'
Making install in win32
make[2]: Entering directory `/home/ticklemonster/libwpd-0.8.0/build/win32'
make[3]: Entering directory `/home/ticklemonster/libwpd-0.8.0/build/win32'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/build/win32'
make[2]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/build/win32'
make[2]: Entering directory `/home/ticklemonster/libwpd-0.8.0/build'
make[3]: Entering directory `/home/ticklemonster/libwpd-0.8.0/build'
make[3]: Nothing to be done for `install-exec-am'.
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/build'
make[2]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/build'
make[1]: Leaving directory `/home/ticklemonster/libwpd-0.8.0/build'
make[1]: Entering directory `/home/ticklemonster/libwpd-0.8.0'
make[2]: Entering directory `/home/ticklemonster/libwpd-0.8.0'
make[2]: Nothing to be done for `install-exec-am'.
/bin/sh ./mkinstalldirs /usr/local/lib/pkgconfig
 /usr/bin/install -c -m 644 libwpd-0.8.pc /usr/local/lib/pkgconfig/libwpd-0.8.pc /usr/bin/install -c -m 644 libwpd-stream-0.8.pc /usr/local/lib/pkgconfig/libwpd-stream-0.8.pc
make[2]: Leaving directory `/home/ticklemonster/libwpd-0.8.0'
make[1]: Leaving directory `/home/ticklemonster/libwpd-0.8.0'
ticklemonster@ticklemonster:~/libwpd-0.8.0$
ticklemonster@ticklemonster:~/libwpd-0.8.0$ sudo checkinstall
sudo: checkinstall: command not found



Well, anyway, after that, I decided to give it a go, because it didn't have any snappy remarks:

> ticklemonster@ticklemonster:~$ cd /home/ticklemonster
ticklemonster@ticklemonster:~$ wpd2sxw extracheerlist06.wps extracheerlist06.sxwERROR: We have no confidence that you are giving us a valid WordPerfect document.  

ERROR : Couldn't write document content
ticklemonster@ticklemonster:~$




so it looks like it installed, but it won't read my wps document! lmao! woot woot ding ding ding! :-({|=

---

### Post by bbarrons on 2006-09-23
My wife has the same problem at work. One of her coworkers refuses to use anything other than works 6.0. Even ms office cant read those files correctly. I was able to find a windows program that converts works to a doc file. I did a google to find it. Its on her computer at work so I cant help with the file name. I know this is not a linux solution but it is all I have got.
Bill

---

### Post by loserboy on 2006-10-23
oh sorry i havent been watching this thread for a while,  thanks for all the work you put into it guys,  lol fortunately this semester her teacher switched to using .doc files.  Convinced my gf to to try OOo now she loves it.

thanks again... hopefully stupid teacher won't switch back

---

### Post by ankara on 2007-03-03
> **bbarrons said:**
> My wife has the same problem at work. One of her coworkers refuses to use anything other than works 6.0. Even ms office cant read those files correctly. I was able to find a windows program that converts works to a doc file. I did a google to find it. Its on her computer at work so I cant help with the file name. I know this is not a linux solution but it is all I have got.
Bill

[here](http://libwps.sourceforge.net/) is a project which will address this problem. 
its still not production version but the basic functionality should help most people wishing to use OO and works. Also [this news feed should be of interest to ubuntu users](http://sourceforge.net/forum/forum.php?forum_id=666350)




HTH

---

### Post by Zeenomorph on 2008-01-24
I came accross this problem and found that simply renaming the file from .wps to .rtf worked fine.

---

