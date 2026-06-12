---
title: "Compile Issues"
date: 2009-02-09
forum: General Help
---

### Post by Chris_Foster on 2009-02-09
I set up a sauerbraten server a while ago (a first person shooter), and it went fine for a while. But it got boring, so I decided to bring it up a notch. I found this mod: [http://hopmod.e-topic.info](http://hopmod.e-topic.info) which seems to be a VERY useful mod to mess with. So I follow the install instructions here: [http://hopmod.e-topic.info/index.php5?title=Installation](http://hopmod.e-topic.info/index.php5?title=Installation)

It downloads fine, but when it comes to the point of compiling it, im hopelessly confused.
The page tells me to go into the /src/ directors and run make. I did. It failed. Heres the output:

```

kira@Gemini://home/kira/hopmod/src$ make
cd enet; ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for ranlib... ranlib
checking for gethostbyaddr_r... yes
checking for gethostbyname_r... yes
checking for poll... yes
checking for fcntl... yes
checking for inet_pton... yes
checking for inet_ntop... yes
checking for struct msghdr.msg_flags... yes
checking for socklen_t... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether to use CRC32... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating include/enet/Makefile
config.status: executing depfiles commands
make    -C enet/ all
make[1]: Entering directory `/home/kira/hopmod/src/enet'
Making all in include
make[2]: Entering directory `/home/kira/hopmod/src/enet/include'
make[3]: Entering directory `/home/kira/hopmod/src/enet'
make[3]: Leaving directory `/home/kira/hopmod/src/enet'
Making all in enet
make[3]: Entering directory `/home/kira/hopmod/src/enet/include/enet'
make[4]: Entering directory `/home/kira/hopmod/src/enet'
make[4]: Leaving directory `/home/kira/hopmod/src/enet'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/kira/hopmod/src/enet/include/enet'
make[3]: Entering directory `/home/kira/hopmod/src/enet/include'
make[4]: Entering directory `/home/kira/hopmod/src/enet'
make[4]: Leaving directory `/home/kira/hopmod/src/enet'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/kira/hopmod/src/enet/include'
make[2]: Leaving directory `/home/kira/hopmod/src/enet/include'
make[2]: Entering directory `/home/kira/hopmod/src/enet'
gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"9-15-2008\" -DPACKAGE_STRING=\"libenet\ 9-15-2008\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"9-15-2008\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -Iinclude/    -g -O2 -MT host.o -MD -MP -MF .deps/host.Tpo -c -o host.o host.c
mv -f .deps/host.Tpo .deps/host.Po
gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"9-15-2008\" -DPACKAGE_STRING=\"libenet\ 9-15-2008\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"9-15-2008\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -Iinclude/    -g -O2 -MT list.o -MD -MP -MF .deps/list.Tpo -c -o list.o list.c
mv -f .deps/list.Tpo .deps/list.Po
gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"9-15-2008\" -DPACKAGE_STRING=\"libenet\ 9-15-2008\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"9-15-2008\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -Iinclude/    -g -O2 -MT callbacks.o -MD -MP -MF .deps/callbacks.Tpo -c -o callbacks.o callbacks.c
mv -f .deps/callbacks.Tpo .deps/callbacks.Po
gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"9-15-2008\" -DPACKAGE_STRING=\"libenet\ 9-15-2008\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"9-15-2008\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -Iinclude/    -g -O2 -MT packet.o -MD -MP -MF .deps/packet.Tpo -c -o packet.o packet.c
mv -f .deps/packet.Tpo .deps/packet.Po
gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"9-15-2008\" -DPACKAGE_STRING=\"libenet\ 9-15-2008\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"9-15-2008\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -Iinclude/    -g -O2 -MT peer.o -MD -MP -MF .deps/peer.Tpo -c -o peer.o peer.c
mv -f .deps/peer.Tpo .deps/peer.Po
gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"9-15-2008\" -DPACKAGE_STRING=\"libenet\ 9-15-2008\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"9-15-2008\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -Iinclude/    -g -O2 -MT protocol.o -MD -MP -MF .deps/protocol.Tpo -c -o protocol.o protocol.c
mv -f .deps/protocol.Tpo .deps/protocol.Po
gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"9-15-2008\" -DPACKAGE_STRING=\"libenet\ 9-15-2008\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"9-15-2008\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -Iinclude/    -g -O2 -MT unix.o -MD -MP -MF .deps/unix.Tpo -c -o unix.o unix.c
mv -f .deps/unix.Tpo .deps/unix.Po
gcc -DPACKAGE_NAME=\"libenet\" -DPACKAGE_TARNAME=\"libenet\" -DPACKAGE_VERSION=\"9-15-2008\" -DPACKAGE_STRING=\"libenet\ 9-15-2008\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"libenet.a\" -DVERSION=\"9-15-2008\" -DHAS_GETHOSTBYADDR_R=1 -DHAS_GETHOSTBYNAME_R=1 -DHAS_POLL=1 -DHAS_FCNTL=1 -DHAS_INET_PTON=1 -DHAS_INET_NTOP=1 -DHAS_MSGHDR_FLAGS=1 -DHAS_SOCKLEN_T=1 -I. -Iinclude/    -g -O2 -MT win32.o -MD -MP -MF .deps/win32.Tpo -c -o win32.o win32.c
mv -f .deps/win32.Tpo .deps/win32.Po
rm -f libenet.a
ar cru libenet.a host.o list.o callbacks.o packet.o peer.o protocol.o unix.o win32.o
ranlib libenet.a
make[2]: Leaving directory `/home/kira/hopmod/src/enet'
make[1]: Leaving directory `/home/kira/hopmod/src/enet'
g++ -Wall -fsigned-char -O2 -g -I/usr/local/include -Ishared -Iengine -Ifpsgame -Ienet/include -Ifpsgame/hopmod/libcubescript/include -DSTANDALONE -DUSE_SQLITE3 -DUSE_GEOIP -DUSE_SCRIPT_SOCKET -L/usr/local/lib -rpath=/usr/local/lib -DSTANDALONE -c -o shared/tools-standalone.o shared/tools.cpp
g++: unrecognized option '-rpath=/usr/local/lib'
In file included from shared/tools.cpp:3:
shared/pch.h:52:18: error: zlib.h: No such file or directory
In file included from shared/tools.cpp:4:
shared/tools.h:649: error: ‘gzFile’ does not name a type
shared/tools.cpp:183: error: ‘gzFile’ does not name a type
make: *** [shared/tools-standalone.o] Error 1


```

I really hope someone can shed some light on this, cause id love to contribute to sauerbratens community

---

### Post by braingram on 2009-02-09
It looks like there may be a problem in the makefile. Specifically, try changing this line (#30):
```

LDFLAGS= -L/usr/local/lib -rpath=/usr/local/lib

```
to
```

LDFLAGS= -L/usr/local/lib -Wl,-rpath,/usr/local/lib

```
It looks like -rpath is actually a linker option and you need the -Wl option to have the compiler pass it along to the linker. see this:
[http://gcc.gnu.org/ml/gcc-help/2003-07/msg00021.html](http://gcc.gnu.org/ml/gcc-help/2003-07/msg00021.html)

---

