---
title: "Dc++"
date: 2005-03-01
forum: Desktop Environments
---

### Post by danip on 2005-03-01
I currently run dc++ through wine because dcgui runs bad I dont really care for the client.  The emulation is good except that whenever tool tips appear the never go away.  Even if i minimize it they are still there on my desktop.  Is there anyone here that has access to a windows box that could recompile the dc++ source without tooltips?

---

### Post by Pluk on 2005-03-01
Have you ever looked at dcgui-qt? Its a good Direct Connect client with a decent gui.

---

### Post by danip on 2005-03-01
i mentioned that in my post.

---

### Post by danip on 2005-03-01
> because dcgui runs bad

yes.

---

### Post by Pluk on 2005-03-01
dcgui and dcgui-qt are different programs, i dislike dcgui too. dcgui-qt is also known as valknut nowadays.

---

### Post by danip on 2005-03-01
I have used both programs.  Dcgui-qt just runs like crap on my system for some reason.  Dcgui just doesnt work period.  Starts up but cant connect to anything at all.

---

### Post by danip on 2005-03-01
i found this program dont know if its any good because I cannot get it to install

[http://linuxdcpp.berlios.de/articles.php?um=index](http://linuxdcpp.berlios.de/articles.php?um=index)

here are the errors iam getting.

```
root@blackbetty:/home/steve/linuxdcpp # scons
scons: Reading SConscript files ...
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C header file sys/poll.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
Checking for C header file asm/atomic.h... yes
Checking for PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP in pthread.h... ok
scons: done reading SConscript files.
scons: Building targets ...
g++ -DXTHREADS -Wl,--export-dynamic -pthread -pthread -DHAVE_ASM_ATOMIC_H -D_GNU_SOURCE -DHAVE_DECL_PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP -I. -DENABLE_BINRELOC -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c -o build/client/ADLSearch.o client/ADLSearch.cpp client/FinishedManager.cpp client/Socket.cpp client/AdcCommand.cpp client/HashManager.cpp client/StringDefs.cpp client/AdcHub.cpp client/HttpConnection.cpp client/StringTokenizer.cpp client/BZUtils.cpp client/HubManager.cpp client/Text.cpp client/BufferedSocket.cpp client/LogManager.cpp client/Thread.cpp client/Client.cpp client/NmdcHub.cpp client/TigerHash.cpp client/ClientManager.cpp client/QueueManager.cpp client/TimerManager.cpp client/ConnectionManager.cpp client/ResourceManager.cpp client/UploadManager.cpp client/CryptoManager.cpp client/SFVReader.cpp client/User.cpp client/DCPlusPlus.cpp client/SearchManager.cpp client/UserConnection.cpp client/DirectoryListing.cpp client/ServerSocket.cpp client/Util.cpp client/DownloadManager.cpp client/SettingsManager.cpp client/ZUtils.cpp client/Encoder.cpp client/ShareManager.cpp client/stdinc.cpp client/Exception.cpp client/SimpleXML.cpp
g++: cannot specify -o with -c or -S and multiple compilations
scons: *** [build/client/ADLSearch.o] Error 1
scons: building terminated because of errors.

```

I am trying to build the cvs version

---

### Post by Pluk on 2005-03-01
Do you have g++-3.4 installed?

Just checked it and it compiles ok. nice program too ..

---

### Post by ow50 on 2005-03-02
I tried dcpp from cvs as well.
```

scons: Reading SConscript files ...
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C header file sys/poll.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
Checking for C header file asm/atomic.h... yes
Checking for PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP in pthread.h... ok
scons: done reading SConscript files.
scons: Building targets ...
g++-3.4 -DXTHREADS -Wl,--export-dynamic -pthread -pthread -DHAVE_ASM_ATOMIC_H -D_GNU_SOURCE -DHAVE_DECL_PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP -I. -DENABLE_BINRELOC -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c -o build/client/ADLSearch.o client/ADLSearch.cpp client/FinishedManager.cpp client/Socket.cpp client/AdcCommand.cpp client/HashManager.cpp client/StringDefs.cpp client/AdcHub.cpp client/HttpConnection.cpp client/StringTokenizer.cpp client/BZUtils.cpp client/HubManager.cpp client/Text.cpp client/BufferedSocket.cpp client/LogManager.cpp client/Thread.cpp client/Client.cpp client/NmdcHub.cpp client/TigerHash.cpp client/ClientManager.cpp client/QueueManager.cpp client/TimerManager.cpp client/ConnectionManager.cpp client/ResourceManager.cpp client/UploadManager.cpp client/CryptoManager.cpp client/SFVReader.cpp client/User.cpp client/DCPlusPlus.cpp client/SearchManager.cpp client/UserConnection.cpp client/DirectoryListing.cpp client/ServerSocket.cpp client/Util.cpp client/DownloadManager.cpp client/SettingsManager.cpp client/ZUtils.cpp client/Encoder.cpp client/ShareManager.cpp client/stdinc.cpp client/Exception.cpp client/SimpleXML.cpp
g++-3.4: --export-dynamic: linker input file unused because linking not done
cc1plus: error: unrecognized command line option "--export-dynamic"
scons: *** [build/client/ADLSearch.o] Error 1
scons: building terminated because of errors.

```

Any ideas?

---

### Post by danip on 2005-03-02
```
steve@blackbetty ~/linuxdcpp $ sudo scons
scons: Reading SConscript files ...
Checking for pkg-config... ok
Checking for gtk+-2.0 >= 2.4... ok
Checking for gthread-2.0 >= 2.4... ok
Checking for libglade-2.0 >= 2.4... ok
Checking for C header file time.h... yes
Checking for C header file signal.h... yes
Checking for C header file unistd.h... yes
Checking for C header file sys/poll.h... yes
Checking for main() in C library pthread... yes
Checking for main() in C library z... yes
Checking for main() in C library bz2... yes
Checking for C header file asm/atomic.h... yes
Checking for PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP in pthread.h... ok
scons: done reading SConscript files.
scons: Building targets ...
g++-3.4 -DXTHREADS -Wl,--export-dynamic -pthread -pthread -DHAVE_ASM_ATOMIC_H -D_GNU_SOURCE -DHAVE_DECL_PTHREAD_RECURSIVE_MUTEX_INITIALIZER_NP -I. -DENABLE_BINRELOC -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/X11R6/include -I/usr/include/atk-1.0 -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -c -o build/client/ADLSearch.o client/ADLSearch.cpp client/FinishedManager.cpp client/Socket.cpp client/AdcCommand.cpp client/HashManager.cpp client/StringDefs.cpp client/AdcHub.cpp client/HttpConnection.cpp client/StringTokenizer.cpp client/BZUtils.cpp client/HubManager.cpp client/Text.cpp client/BufferedSocket.cpp client/LogManager.cpp client/Thread.cpp client/Client.cpp client/NmdcHub.cpp client/TigerHash.cpp client/ClientManager.cpp client/QueueManager.cpp client/TimerManager.cpp client/ConnectionManager.cpp client/ResourceManager.cpp client/UploadManager.cpp client/CryptoManager.cpp client/SFVReader.cpp client/User.cpp client/DCPlusPlus.cpp client/SearchManager.cpp client/UserConnection.cpp client/DirectoryListing.cpp client/ServerSocket.cpp client/Util.cpp client/DownloadManager.cpp client/SettingsManager.cpp client/ZUtils.cpp client/Encoder.cpp client/ShareManager.cpp client/stdinc.cpp client/Exception.cpp client/SimpleXML.cpp
g++-3.4: --export-dynamic: linker input file unused because linking not done
cc1plus: error: unrecognized command line option "--export-dynamic"
scons: *** [build/client/ADLSearch.o] Error 1
scons: building terminated because of errors.

```

Yeah I just installed that still get this error.

---

### Post by danip on 2005-03-03
bump

---

### Post by destino on 2005-03-05
I had the same problem as you so I downloaded a newer version of scons (scons_0.96.1-0.1_all.deb) from [http://www.scons.org/](http://www.scons.org/) and removed the old version I had installed (scons_0.95-1_all.deb) and after that I could finish the install of DC++.

---

### Post by danip on 2005-03-05
awesome it worked.  Progam is a little buggy...guess its unfinished cvs though

---

