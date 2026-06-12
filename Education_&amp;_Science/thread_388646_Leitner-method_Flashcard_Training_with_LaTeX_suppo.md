---
title: "Leitner-method Flashcard Training with LaTeX support"
date: 2007-03-19
forum: Education &amp; Science
---

### Post by tomcalloway on 2007-03-19
I would like to know if anyone has interest in working with me to create an Ubuntu package that works for the KSalomon software (or at least can explain how to successfully compile it from source):  [http://ksalomon.sourceforge.net/download.php](http://ksalomon.sourceforge.net/download.php)

It seems there are some problems with dependencies and installation from source and from the posted debian sarge package.

This seems like really great software, since it allows LaTeX and also uses the .kvtml (KVocTrain) format.  My goal is to integrate it with hierarchical notetaking software like KnowIt and BasKet.  I already created a utility that converts KnowIt files into .kvtml format.

---

### Post by ysop on 2007-04-01
First of all, this is a nice idea. Since i have to learn mathematic equations and definitions, i would really like to test it. And ive got really no idea, which program offers Flashcard Training with Latex.

Seems that you really need some help on that one,
i tried to install it, but i need kdelibs4...
and i have kdelibs4c2a ...or maybe i need some help ;)

Sad but true, im just a user and cant help you,
but good luck.

---

### Post by WW on 2007-04-01
I tried compiling the "stable" 1.6-beta version from source.  I am running dapper.  To get ./configure to work, I had to install the packages **kdelibs4-dev** and **automake1.7**.  I already have many other development packages installed (e.g.qt3 stuff), so someone else might have to install additional packages before ./configure is successful.

Unfortunately, when I tried to compile the program with the **make** command, I eventually got this error:
```

if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT ksalomon.o -MD -MP -MF ".deps/ksalomon.Tpo" \
          -c -o ksalomon.o `test -f 'ksalomon.cpp' || echo './'`ksalomon.cpp; \
        then mv -f ".deps/ksalomon.Tpo" ".deps/ksalomon.Po"; \
        else rm -f ".deps/ksalomon.Tpo"; exit 1; \
        fi
/usr/include/kde/kio/jobclasses.h:347: error: expected unqualified-id before &#8216;{&#8217; token
make[3]: *** [ksalomon.o] Error 1

```
I didn't see an obvious cause of the error in jobclasses.h.  If you can get this far and you get the same error, you could try reporting it to the author of ksalomon.

I also tried the "snapshot" version.  The **make** command again eventually failed, with this error:
```

source='abfragedialog.cpp' object='abfragedialog.o' libtool=no \
        depfile='.deps/abfragedialog.Po' tmpdepfile='.deps/abfragedialog.TPo' \
        depmode=gcc3 /bin/sh ../admin/depcomp \
        g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -c -o abfragedialog.o `test -f 'abfragedialog.cpp' || echo './'`abfragedialog.cpp
In file included from abfragedialog.cpp:48:
vocabelwidget.h:23:20: error: qarray.h: No such file or directory
abfragedialog.cpp: In member function &#8216;virtual int orderliste::compareItems(void*, void*)&#8217;:
abfragedialog.cpp:163: warning: unused variable &#8216;t&#8217;
make[3]: *** [abfragedialog.o] Error 1

```

---

### Post by ysop on 2007-04-03
Im running on dapper (Kubuntu and Ubuntu) system and i get
exactly the same errors, while compiling the 0.1.6 and the 0.1.7.pre4 version.

I am going to contact the developer and hope he got time to fix this problem.
Maybe he can join us here, otherwise i will post his reply.

p.s. mail was send

---

### Post by micha105 on 2007-04-03
Hello, 
I'm the developer of ksalomon..

So possibly I released 0.1.7-beta to soon, I've uploaded the files to sourceforge 6 hours ago..


About the compile error with 0.1.6-beta: Strange. Tom already sent me the file jobclasses.h, seems not to be suspicious.

0.1.7-beta: 
The file qarray.h is not found, it belongs to the Qt include headers.
Does it work if you run configure with the options 

--with-qt-includes=qtincludespath --with-qt-libraries=qtlibrariespath


Please replace qtincludespath and qtlibrariespath with the appropriate paths.

You can look for the qtincludespath by entering locate qarray.h

micha@laptop ~ $ locate qarray.h
/usr/qt/3/doc/html/qarray.html
/usr/qt/3/include/qarray.h

->I'd have to replace qtincludespath with /usr/qt/3/include

For the qtlibrariespath you could try to locate either libqt.so or libqt-mt.so .

Michael

---

### Post by amerikkanu on 2007-04-07
hello all,

and thanks tomcalloway for taking the initiative on this and to the friendly developer, michael, for being so responsive.

this is just to confirm that i also got the same error message as others above (after having located and specified the includespath and the librariespath).  my system does not have the qarray.h header file, though i've installed every qt3* package on ubuntu.  (nothing is returned when i run "locate qarray.h", so making bottoms out with that error.  not sure what else to do since from googling i expected that file to be part of the qt3-tools package.  am happy to keep troubleshooting, just need a little direction...

---

### Post by micha105 on 2007-04-09
> **amerikkanu said:**
> hello all,

and thanks tomcalloway for taking the initiative on this and to the friendly developer, michael, for being so responsive.

this is just to confirm that i also got the same error message as others above (after having located and specified the includespath and the librariespath).  my system does not have the qarray.h header file, though i've installed every qt3* package on ubuntu.  (nothing is returned when i run "locate qarray.h", so making bottoms out with that error.  not sure what else to do since from googling i expected that file to be part of the qt3-tools package.  am happy to keep troubleshooting, just need a little direction...

Thanks for the hint, Qt has renamed qarray into qmemarray.
I have uploaded a new development snapshot (0.1.8-pre2) which should work,
could someone please give me feedback whether it compiles ?

[ksalomon.sourceforge.net/download.php]("ksalomon.sourceforge.net/download.php")

Michael

---

### Post by amerikkanu on 2007-04-13
Hey guys, this new version works!  Try it out!  I just compiled (without specifying specific paths) and installed it.  I have yet to play around with it, but I'm assuming it's fully functional.  One thing to note is that, if your system is like mine, typing 'ksalomon' in the terminal won't engage the binary.  But you can find it in /usr/local/kde/bin.

Kudos again for the developer, Michael.  He was even kind enough to offer to look over the output from my compiling attempts.  Hats off, it works!

---

