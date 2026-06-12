---
title: "g++ no_dead_strip_inits_and_terms"
date: 2008-12-23
forum: General Help
---

### Post by jlcordeiro on 2008-12-23
I'm trying to compile PokerTH 0.6.3, and Im getting stuck with

> g++ -Wl,--no-undefined -no_dead_strip_inits_and_terms -o bin/pokerth_server obj/pokerth_server.o obj/nonqttoolswrapper.o obj/nonqthelper.o obj/net_helper_server.o obj/loghelper_server.o obj/daemon.o obj/convhelper.o    -Llib -L/usr/lib -lpokerth_lib -lboost_thread-mt -lboost_filesystem-mt -lboost_program_options-mt -lboost_iostreams-mt -lcurl -lgnutls-openssl -lgcrypt -lpthread
g++: unrecognized option '-no_dead_strip_inits_and_terms'


I've been searching around, but i couldnt find any help.

---

### Post by StOoZ on 2008-12-23
did you get it from a tar.gz file?
if so , extract it , and then go to its directory , and , type :
./configure    (only if it has such file...)
make
make install


the best thing to do is to read the INSTALLTION , or README file , which is most probably available within that package.

---

### Post by jlcordeiro on 2008-12-23
Thats what I did:

qmake pokerth.pro
make

and after make that error comes up.

---

### Post by Pobega on 2008-12-23
You could always open the Makefile and manually take out all instances of *'-no_dead_strip_inits_and_terms'*, hopefully then it will compile correctly.

**Edit:** Actually, after a quick Google it seems that this option is intended for GCC on Darwin systems; Anyway, you could just download a precompiled version or a simple autoinstaller[1] -- No need to compile from source.

[1] [http://www.pokerth.net/content/view/16/60/](http://www.pokerth.net/content/view/16/60/)

---

