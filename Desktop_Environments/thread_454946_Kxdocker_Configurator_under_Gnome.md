---
title: "Kxdocker Configurator under Gnome"
date: 2007-05-26
forum: Desktop Environments
---

### Post by pferrel on 2007-05-26
I have gotten Kxdocker running on my Fiesty Gnome machine but the deb does not come with the configurator.  Unfortunately I can't figure out how to compile it.  I get the following errors:

pferrel@pat-x1000:~/Desktop/kxdocker/kxdocker-configurator-1.0.2$ make
make  all-recursive
make[1]: Entering directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2'
Making all in addons
make[2]: Entering directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/addons'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/addons'
Making all in doc
make[2]: Entering directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/doc'
Making all in .
make[3]: Entering directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/doc'
Making all in en
make[3]: Entering directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/doc/en'
make[2]: Leaving directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/doc'
Making all in po
make[2]: Entering directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/po'
Making all in src
make[2]: Entering directory `/home/pferrel/.Trash/kxdocker-configurator-1 (4th copy).0.2/src'
if /bin/bash ../libtool --silent --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.  -I/usr/include  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -MT xeplugin_configurator.lo -MD -MP -MF ".deps/xeplugin_configurator.Tpo" -c -o xeplugin_configurator.lo xeplugin_configurator.cpp; \
        then mv -f ".deps/xeplugin_configurator.Tpo" ".deps/xeplugin_configurator.Plo"; else rm -f ".deps/xeplugin_configurator.Tpo"; exit 1; fi
./xeplugin_cfgicon.h:50: error: ISO C++ forbids declaration of 'XSGObjectIcon' with no type
./xeplugin_cfgicon.h:50: error: expected ';' before '*' token
./xeplugin_cfgicon.h:62: error: 'XSGObjectIcon' has not been declared
./xeplugin_cfgicon.h:112: error: 'XSGObjectIcon' has not been declared
xeplugin_configurator.cpp: In constructor 'XEPlugin_Configurator::XEPlugin_Configurator(QWidget*, const char*)':
xeplugin_configurator.cpp:83: error: 'XEObject' has not been declared
xeplugin_configurator.cpp: In destructor 'virtual XEPlugin_Configurator::~XEPlugin_Configurator()':
xeplugin_configurator.cpp:100: error: 'XEObject' has not been declared
xeplugin_configurator.cpp: In member function 'void XEPlugin_Configurator::cfg_default()':
...

I am using the standard gcc 4.1.2

Anyone able to get this to compile with a clean new Fiesty install?

---

### Post by jamarsa on 2007-07-08
I just had the same problem compiling, and was due to a duplicate libkxdocker.h in /usr/include/kde, perhaps due to having the binary version of kxdocker installed prevoiusly. Just deleted it and kept the one installed in /usr/include.


Hope it helps you, although a bit late. Sorry, I didn't look for answers to this same problem until today.

---

