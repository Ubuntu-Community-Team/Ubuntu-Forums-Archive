---
title: "TORCS doesn't run!!!"
date: 2010-09-21
forum: Gaming &amp; Leisure
---

### Post by jfcaringi on 2010-09-21
Hello!

Please, I need some help:
When I try to play TORCS then got this messaje:
> 
jfc@Linx:~$ torcs
Visual Properties Report
------------------------
Compatibility mode, properties unknown.
/usr/games/torcs: línea 53:  6909 Fallo de segmentación  $LIBDIR/torcs-bin -l $LOCAL_CONF -L $LIBDIR -D $DATADIR $*
jfc@Linx:~$


before this error I was trying to modified el CHAMPIOSHIP file, but, I dont think so this will make the error,

I tried to reinstall, but it doesnt work: I get the same error message

Any idea?

--
SOLVED

I save a file inside the folder: /usr/share/games/torcs/config/raceman with the name of "champ (backup).xml", when I erase this file the problem goes!

Thanks for the clue!
--
Now, how can I change the status of this topic to SOLVED?

---

### Post by ucal on 2010-09-22
With my limited understanding of french, it looks like you've got a segmentation fault.  From the torcs faq on source forge:

> 4.3.1 Broken OpenGL/DRI drivers or '~' file.

/usr/local/bin/torcs: line 54: 31895 Segmentation fault
$LIBDIR/torcs-bin -l $LOCAL_CONF -L $LIBDIR -D $DATADIR $*

There are two known possibilities which cause such a crash:

    * You have buggy OpenGL/DRI driver, you should update to a recent version. Start TORCS with the "-s" option to disable multitexturing.
    * You have edited a TORCS XML file (e. g. endrace.xml) and your editor left a copy with an appended "~" (e. g. endrace.xml~). Remove those "~" files.

---

