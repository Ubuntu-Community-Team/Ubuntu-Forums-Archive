---
title: "Simple C++ IDE for Kubuntu?"
date: 2005-10-04
forum: Desktop Environments
---

### Post by carlos1 on 2005-10-04
I used Dev-C++ in ..cough.. Windows, is there a similar simple C++ IDE for KDE?
I can use Anjuta but it has an UGLY Gnome interface. Kdevelop refuses to see my KDElibs docs. Is there something like Dev-C++ for Linux?

---

### Post by Roptaty on 2005-10-04
KDevelop is a good alternative. :)

---

### Post by carlos1 on 2005-10-05
I tried KDevelop but for some reason it doesn't find theKDElibs and I don't know where to point it exactly. 
At this point I can stick with Anjuta since I'm not doing any GUI stuff, it's all backend.

---

### Post by Roptaty on 2005-10-05
Have you installed the kdelibs4-doc package?

---

### Post by Tilex on 2005-10-05
Wouldn't you want to give [Eclipse]("http://eclipse.org") a try?  That's what I use for all my C++-related projects...

---

### Post by drgreborn on 2005-10-05
Yeah eclips eis a good choice. Just get yourself a java jre and teh eclipse itself. Then go to help->software updates->find and install->serach for new features->add a new remote and enter "http://download.eclipse.org/tools/cdt/releases/eclipse3.1" -> then just install cdt and your good to go.

---

### Post by nrwilk on 2005-10-05
[QUOTE=drgreborn]Yeah eclips eis a good choice. Just get yourself a java jre and teh eclipse itself. Then go to help->software updates->find and install->serach for new features->add a new remote and enter "http://download.eclipse.org/tools/cdt/releases/eclipse3.1" -> then just install cdt and your good to go.[/QUOTE]

I tried this, but once the download finishes Eclipse just hangs indefinitely.  I've tried it several times.  Same each time.


Also,
When I try to compile some things that I downloaded, I get an error message that says that my computer cannot compile simple C++ programs.  What do I look for to figure out what I need?

---

### Post by abhaysahai on 2005-10-05
For KDE, KDevelop is the default IDE. 
Please post the exact error you are getting in Kdevelop. 
It is one of the most advanced and well deveoped IDE in open source world.

---

### Post by brentoboy on 2005-10-05
[QUOTE=Fealos]I tried this, but once the download finishes Eclipse just hangs indefinitely.  I've tried it several times.  Same each time.
[/QUOTE]

If you are in breezy, give eclipse a week or so to stablize.  I have noticed frequent changes to eclise as of late in the repositories, and I have had several update issues with eclispe for the last week or so.  I wouldnt be shocked to hear that there is an unresolved error in it - it has so many interrelated components to keep up with, some of them might not be correctly synced with the rest.

Dont give up on eclipse yet, and dont knock your brains out trying to make it work today.  Unless you are still in hoarty - which should be stable.

---

### Post by Tilex on 2005-10-05
> When I try to compile some things that I downloaded, I get an error message that says that my computer cannot compile simple C++ programs. What do I look for to figure out what I need?

You might want to add the gcc compiler..you have to go in your Package Manager (KPackage) et find gcc...
Or, just type this in a shell in order to install the essentials for compiling:
```
sudo apt-get install build-essentials
```

---

### Post by drgreborn on 2005-10-05
First make sure that you have all the tools need to compile a c/c++ program. do a apt-get as stated by Tilex. Or you can always go to the synaptic and install the required things by doing search and entering C++ and install what you would need. 
Primarily you would need three things, GCC, MAKE and Binutils. That should get you started. Hope this helps cheers.

---

### Post by daller on 2005-10-06
Trying to open KDevDesigner, i get a KDE error, an this backtrace:

---------------------------------------

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1231853344 (LWP 9684)]
[KCrash handler]
#4  0xb6c37ef1 in XCreateGC (dpy=0x0, d=0, valuemask=0, values=0x0)
    at ../../src/CrGC.c:76
#5  0xb707f8bb in qsincos () from /usr/lib/libqt-mt.so.3
#6  0xb707fee0 in qsincos () from /usr/lib/libqt-mt.so.3
#7  0xb7080301 in QPainter::updatePen () from /usr/lib/libqt-mt.so.3
#8  0xb7138d8f in QPainter::setPen () from /usr/lib/libqt-mt.so.3
#9  0xb726cd54 in QSplashScreen::drawContents () from /usr/lib/libqt-mt.so.3
#10 0xb726c910 in QSplashScreen::drawContents () from /usr/lib/libqt-mt.so.3
#11 0xb726c969 in QSplashScreen::repaint () from /usr/lib/libqt-mt.so.3
#12 0xb726caff in QSplashScreen::setPixmap () from /usr/lib/libqt-mt.so.3
#13 0xb726cba8 in QSplashScreen::QSplashScreen () from /usr/lib/libqt-mt.so.3
#14 0x0804eab4 in ?? ()
#15 0x080f79a8 in ?? ()
#16 0xbfa32aac in ?? ()
#17 0x00000000 in ?? ()
#18 0x00000000 in ?? ()
#19 0x00000000 in ?? ()
#20 0x00000001 in ?? ()
#21 0x0804fed8 in vtable for QGList ()
#22 0x00000000 in ?? ()
#23 0x00000000 in ?? ()
#24 0x0804fe44 in vtable for QGList ()
#25 0xb7f34838 in ?? () from /lib/ld-linux.so.2
#26 0x00000000 in ?? ()
#27 0xb7f1e1ac in ?? ()
#28 0xbfa32a28 in ?? ()
#29 0xb7f267c9 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#30 0xb699fea2 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#31 0x0804e7b1 in ?? ()

---------------------------------------

Any ideas?

---

### Post by jeffjj on 2005-10-06
> Wouldn't you want to give Eclipse a try? That's what I use for all my C++-related projects...
Have you always used Eclipse? I tried using it for GTK+ programming but it was not very good under the 2.1 release. Has it improved? I am more of a Java developer so I am really used to all of Eclipse's power use functionality. I have been meaning to give the C/C++ 3.0 version a try.

---

