---
title: "mplayer plugin"
date: 2006-12-19
forum: Desktop Environments
---

### Post by ubman on 2006-12-19
Ok i must be brain dead these days i'm trying to install mplayer-plugin
to seamonkey installed browser in my home directory so everything needed
is there,downloaded source tar from sourceforge, to my home directory.
extracted it in my home heres the the out put from my attempts

rick@rick-desktop:~$ cd mplayerplug-in
rick@rick-desktop:~/mplayerplug-in$ ./configure
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
rick@rick-desktop:~/mplayerplug-in$ ./whatoptions.sh 
Run configure with the following options
./configure



can someone be as so kind to show me the way to this so seamonkey 
will have the plugin Thanks Rick](*,)

---

### Post by meng on 2006-12-19
Why not install from repositories and save yourself the hassle? Multiverse repositories have to be enabled though.

---

### Post by ciscosurfer on 2006-12-19
> **ubman said:**
> Ok i must be brain dead these days i'm trying to install mplayer-plugin
to seamonkey installed browser in my home directory so everything needed
is there,downloaded source tar from sourceforge, to my home directory.
extracted it in my home heres the the out put from my attempts

rick@rick-desktop:~$ cd mplayerplug-in
rick@rick-desktop:~/mplayerplug-in$ ./configure
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking for C++ compiler default output file name... configure: error: C++ compiler cannot create executables
See `config.log' for more details.
rick@rick-desktop:~/mplayerplug-in$ ./whatoptions.sh 
Run configure with the following options
./configure



can someone be as so kind to show me the way to this so seamonkey 
will have the plugin Thanks Rick](*,)If you really want to compile from source, then you need to first install **build-essential** (found in the repositories).  I would also recommend using **checkinstall** (also found in the repositories) instead of issuing **make install**, as it will create a package for you and will allow you to easily manage it.

Btw, you can also install from mozilla-mplayer from the repositories and that will take care of it for you.  You'll need your Multiverse repo enabled.

As an aside, Automatix2 can do this for you as well (along with many other apps): [http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)

---

### Post by ubman on 2006-12-19
> **meng said:**
> Why not install from repositories and save yourself the hassle? Multiverse repositories have to be enabled though.

I see no seamonkey in synaptic!

---

### Post by ubman on 2006-12-19
> **ciscosurfer said:**
> If you really want to compile from source, then you need to first install **build-essential** (found in the repositories).  I would also recommend using **checkinstall** (also found in the repositories) instead of issuing **make install**, as it will create a package for you and will allow you to easily manage it.

Btw, you can also install from mozilla-mplayer from the repositories and that will take care of it for you.  You'll need your Multiverse repo enabled.

As an aside, Automatix2 can do this for you as well (along with many other apps): [http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)



Yes i know i have Automatix ----But i didn't clairify is that i downloaded
seamonkey from mozzilla installed it myself so thoses plugins don't work
for seamonkey.:-|  Hence the need for the source mplayerplugin:)

---

### Post by ciscosurfer on 2006-12-19
> **ubman said:**
> Yes i know i have Automatix ----But i didn't clairify is that i downloaded
seamonkey from mozzilla installed it myself so thoses plugins don't work
for seamonkey.:-|  Hence the need for the source mplayerplugin:)Okay.  Then use my instructions from before to install the plugin to the seamonkey directory.  In the install file it will tell you how to tell ./configure where you want to place the files.

---

### Post by kerry_s on 2006-12-19
I run seamonkey from home to, copy /usr/lib/mozilla/plugins to /home/(you)/.mozilla

Or you can use a symlink->

ln -s /usr/lib/mozilla/plugins /home/(you)/.mozilla/plugins

Replace (you) with the account name.

Grab multizilla extension it's great-> [http://multizilla.mozdev.org/installation/installation.html](http://multizilla.mozdev.org/installation/installation.html)

---

### Post by ubman on 2006-12-19
> **ciscosurfer said:**
> Okay.  Then use my instructions from before to install the plugin to the seamonkey directory.  In the install file it will tell you how to tell ./configure where you want to place the files.

Thanks I thought i was following the instructions from the install file
Still no joy](*,)

---

### Post by ubman on 2006-12-19
> **kerry_s said:**
> I run seamonkey from home to, copy /usr/lib/mozilla/plugins to /home/(you)/.mozilla

Or you can use a symlink->

ln -s /usr/lib/mozilla/plugins /home/(you)/.mozilla/plugins

Replace (you) with the account name.

Grab multizilla extension it's great-> [http://multizilla.mozdev.org/installation/installation.html](http://multizilla.mozdev.org/installation/installation.html)

No joy Here Ethier?:-k

---

### Post by ubman on 2006-12-19
Ok reinstalled build-essential Getting closer:D 

rick@rick-desktop:~$ cd mplayerplug-in
rick@rick-desktop:~/mplayerplug-in$ ./configure
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
configure: Determining mozilla/firefox packages to build against
checking for MOZPLUG... yes
checking for GTK... yes
checking for GTK24... yes
checking for GTHREAD... yes
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for egrep... grep -E
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
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking X11/Xlib.h usability... yes
checking X11/Xlib.h presence... yes
checking for X11/Xlib.h... yes
checking X11/Intrinsic.h usability... yes
checking X11/Intrinsic.h presence... yes
checking for X11/Intrinsic.h... yes
checking X11/StringDefs.h usability... yes
checking X11/StringDefs.h presence... yes
checking for X11/StringDefs.h... yes
checking for sys/stat.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for an ANSI C-conforming const... yes
checking whether time.h and sys/time.h may both be included... yes
checking for pid_t... yes
checking for size_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for memset... yes
checking for strcasecmp... yes
checking for strchr... yes
checking for strdup... yes
checking for strncasecmp... yes
checking for strstr... yes
checking for strrchr... yes
checking for snprintf... yes
checking for mkfifo... yes
checking for dup2... yes
checking for gettimeofday... yes
checking for strerror... yes
checking for strtol... yes
checking for mkdir... yes
checking for setlocale... yes
checking for memmem... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for sys/wait.h that is POSIX.1 compatible... yes
checking return type of signal handlers... void
checking X11/xpm.h usability... no
checking X11/xpm.h presence... no
checking for X11/xpm.h... no
checking for DPMSQueryExtension in -lXdpms... no
checking for X11/extensions/dpms.h... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating po/Makefile
config.status: creating install.sh
config.status: creating uninstall.sh
config.status: creating config.h
rick@rick-desktop:~/mplayerplug-in$ ./whatoptions.sh 
Run configure with the following options

./configure
rick@rick-desktop:~/mplayerplug-in$ make
g++ -c -o plugin.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/mozilla/java -I/usr/include/mozilla/plugin -I/usr/include/mozilla -I/usr/include/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr   -I/usr/include/mozilla -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   Source/plugin.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIServiceManager.h:40: warning: ‘class nsIServiceManager’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIComponentManager.h:27: warning: ‘class nsIComponentManager’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsCOMPtr.h:332: warning: ‘class nsCOMPtr_helper’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsCOMPtr.h: In instantiation of ‘nsDerivedSafe<nsISupports>’:
/usr/include/mozilla/nsCOMPtr.h:1392:   instantiated from here
/usr/include/mozilla/nsCOMPtr.h:197: warning: ‘class nsDerivedSafe<nsISupports>’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIFactory.h:31: warning: ‘class nsIFactory’ has virtual functions but non-virtual destructor
/usr/include/mozilla/xpcom/nsIComponentManagerObsolete.h:33: warning: ‘class nsIComponentManagerObsolete’ has virtual functions but non-virtual destructor
/usr/include/mozilla/xpcom/nsComponentManagerUtils.h:44: warning: ‘class nsCreateInstanceByCID’ has virtual functions but non-virtual destructor
/usr/include/mozilla/xpcom/nsComponentManagerUtils.h:63: warning: ‘class nsCreateInstanceByContractID’ has virtual functions but non-virtual destructor
/usr/include/mozilla/xpcom/nsIServiceManagerObsolete.h:77: warning: ‘class nsIServiceManagerObsolete’ has virtual functions but non-virtual destructor
/usr/include/mozilla/xpcom/nsIServiceManagerUtils.h:48: warning: ‘class nsGetServiceByCID’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsCOMPtr.h: In instantiation of ‘nsDerivedSafe<nsIServiceManager>’:
/usr/include/mozilla/xpcom/nsIServiceManagerUtils.h:48:   instantiated from here
/usr/include/mozilla/nsCOMPtr.h:197: warning: ‘class nsDerivedSafe<nsIServiceManager>’ has virtual functions but non-virtual destructor
/usr/include/mozilla/xpcom/nsIServiceManagerUtils.h: In function ‘const nsGetServiceByCID do_GetService(const nsCID&, nsresult*)’:
/usr/include/mozilla/xpcom/nsIServiceManagerUtils.h:70: note: synthesized method ‘nsGetServiceByCID::nsGetServiceByCID(const nsGetServiceByCID&)’ first required here 
/usr/include/mozilla/xpcom/nsIServiceManagerUtils.h: At global scope:
/usr/include/mozilla/xpcom/nsIServiceManagerUtils.h:81: warning: ‘class nsGetServiceByContractID’ has virtual functions but non-virtual destructor
/usr/include/mozilla/xpcom/nsIServiceManagerUtils.h:114: warning: ‘class nsGetServiceFromCategory’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIMemory.h:54: warning: ‘class nsIMemory’ has virtual functions but non-virtual destructor
Source/plugin.cpp: In function ‘NPError NS_PluginInitialize()’:
Source/plugin.cpp:101: warning: dereferencing type-punned pointer will break strict-aliasing rules
g++ -c -o nsScriptablePeer.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/mozilla/java -I/usr/include/mozilla/plugin -I/usr/include/mozilla -I/usr/include/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr   -I/usr/include/mozilla -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  Source/nsScriptablePeer.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
g++ -c -o npp_gate.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/mozilla/java -I/usr/include/mozilla/plugin -I/usr/include/mozilla -I/usr/include/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr   -I/usr/include/mozilla -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  plugingate/npp_gate.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
g++ -c -o np_entry.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/mozilla/java -I/usr/include/mozilla/plugin -I/usr/include/mozilla -I/usr/include/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr   -I/usr/include/mozilla -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  plugingate/np_entry.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
g++ -c -o npn_gate.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/mozilla/java -I/usr/include/mozilla/plugin -I/usr/include/mozilla -I/usr/include/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr   -I/usr/include/mozilla -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  plugingate/npn_gate.cpp
g++ -c -o plugin-support.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/mozilla/java -I/usr/include/mozilla/plugin -I/usr/include/mozilla -I/usr/include/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr   -I/usr/include/mozilla -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   Source/plugin-support.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
g++ -c -o plugin-setup.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/mozilla/java -I/usr/include/mozilla/plugin -I/usr/include/mozilla -I/usr/include/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr   -I/usr/include/mozilla -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   -DSTD Source/plugin-setup.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
g++ -c -o plugin-list.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/mozilla/java -I/usr/include/mozilla/plugin -I/usr/include/mozilla -I/usr/include/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr   -I/usr/include/mozilla -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED   Source/plugin-list.cpp
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
g++ -c -o plugin-ui.o -Wall -g -O2   -g -O2  -DXP_UNIX -DMOZ_X11 -I/usr/include/mozilla/java -I/usr/include/mozilla/plugin -I/usr/include/mozilla -I/usr/include/mozilla/xpcom -I/usr/include/mozilla/string -I/usr/include/mozilla/nspr   -I/usr/include/mozilla -Iinclude -fPIC  -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -DGTK_ENABLED  Source/plugin-ui.cpp
Source/plugin-ui.cpp:6:21: error: X11/xpm.h: No such file or directory
Source/plugin-ui.cpp:48:2: error: #error libXpm has not been found. Compilation cannot continue
include/pluginbase.h:55: warning: ‘class nsPluginInstanceBase’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsISupportsBase.h:80: warning: ‘class nsISupports’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIProgrammingLanguage.h:32: warning: ‘class nsIProgrammingLanguage’ has virtual functions but non-virtual destructor
/usr/include/mozilla/nsIClassInfo.h:33: warning: ‘class nsIClassInfo’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:25: warning: ‘class nsIScriptableWMPPlugin’ has virtual functions but non-virtual destructor
Source/nsIScriptableMplayerPlugin.h:120: warning: ‘class nsIScriptableMplayerPlugin’ has virtual functions but non-virtual destructor
Source/nsScriptablePeer.h:56: warning: ‘class nsClassInfoMixin’ has virtual functions but non-virtual destructor
make: *** [plugin-ui.o] Error 1
rick@rick-desktop:~/mplayerplug-in$ 


I don't understand the error message?

---

### Post by kerry_s on 2006-12-20
> **ubman said:**
> No joy Here Ethier?:-k

Dude your making it harder than it is.

in terminal->

sudo gedit /etc/apt/sources.list

make your lines look like this
```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse 

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse 

deb http://www.debian-multimedia.org/ sid main 
```

(I'm assuming your using dapper)

sudo apt-get update

sudo apt-get install mozilla-mplayer
 

then do the steps ealier when the plugin is installed

 copy /usr/lib/mozilla/plugins to /home/(you)/.mozilla

Or you can use a symlink->

ln -s /usr/lib/mozilla/plugins /home/(you)/.mozilla/plugins

Replace (you) with the account name.

I would explain the gui way, but i don't have the dumbed down synaptic in gnome.

---

### Post by ubman on 2006-12-20
> **kerry_s said:**
> Dude your making it harder than it is.

in terminal->

sudo gedit /etc/apt/sources.list

make your lines look like this
```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted universe multiverse 

deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse 

deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse 

deb http://security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse 

deb http://www.debian-multimedia.org/ sid main 
```

(I'm assuming your using dapper)

sudo apt-get update

sudo apt-get install mozilla-mplayer
 

then do the steps ealier when the plugin is installed

 copy /usr/lib/mozilla/plugins to /home/(you)/.mozilla

Or you can use a symlink->

ln -s /usr/lib/mozilla/plugins /home/(you)/.mozilla/plugins

Replace (you) with the account name.

I would explain the gui way, but i don't have the dumbed down synaptic in gnome.



I'm sorry i'm no guru.
Not Dapper Edgy I have the mplayer plugin i tried your two methods

 copy /usr/lib/mozilla/plugins to /home/rick/.mozilla

ln -s /usr/lib/mozilla/plugins /home/(you)/.mozilla/plugins This one says
link already exsits
again sorry for my bother.

rick@rick-desktop:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-mplayer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rick@rick-desktop:~$

---

### Post by kerry_s on 2006-12-20
Then open seamonkey & click "help> about plug-ins" to see if it's detected.

I'm betting you just didn't install the codecs to actually play content->

make sure you have this line in /etc/apt/sources.list

deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid main

Then->

sudo apt-get update

sudo apt-get install w32codecs libdvdcss2


plugins page looks like this->

---

