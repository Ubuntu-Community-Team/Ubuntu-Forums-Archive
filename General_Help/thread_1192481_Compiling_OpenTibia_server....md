---
title: "Compiling OpenTibia server..."
date: 2009-06-20
forum: General Help
---

### Post by pontuz on 2009-06-20
Hello.
I was following this guide: [http://otfans.net/wiki/index.php/Compiling_OTServ_under_Ubuntu](http://otfans.net/wiki/index.php/Compiling_OTServ_under_Ubuntu)
..and i did exactly what i was told to. The compilation went well (i think) but how do i start the server?

I know I start it by typing ./otserv in the directory it was installed, but it says that there is no such file or directory!

Edit:
This is what i did:

```
pontus@Pontus-PC:~/otserv/otserv-062-src$ ./autogen.sh
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force 
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
configure.ac:6: installing `./install-sh'
configure.ac:6: installing `./missing'
Makefile.am: installing `./depcomp'
autoreconf: Leaving directory `.'
pontus@Pontus-PC:~/otserv/otserv-062-src$ ./configure --enable-sqlite
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
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
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking netinet/in.h usability... yes
checking netinet/in.h presence... yes
checking for netinet/in.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdint.h... (cached) yes
checking for stdlib.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/timeb.h usability... yes
checking sys/timeb.h presence... yes
checking for sys/timeb.h... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... no
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for int16_t... yes
checking for int32_t... yes
checking for int64_t... yes
checking for size_t... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for uint16_t... yes
checking for uint32_t... yes
checking for uint64_t... yes
checking for uint8_t... yes
checking for ptrdiff_t... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for working memcmp... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... yes
checking for floor... yes
checking for ftime... yes
checking for gethostbyname... yes
checking for gethostname... yes
checking for memset... yes
checking for pow... yes
checking for sqrt... yes
checking for strcasecmp... yes
checking for strncasecmp... yes
checking for strstr... yes
checking for strtol... yes
checking for xml2-config... /usr/bin/xml2-config
checking for libxml - version >= 2.6.5... yes (version 2.6.32)
checking gmp.h usability... yes
checking gmp.h presence... yes
checking for gmp.h... yes
checking for __gmpz_init2 in -lgmp... yes
checking for main in -lboost_thread-gcc-mt... no
checking for main in -lboost_thread-mt... yes
checking for main in -lboost_regex-gcc-mt... no
checking for main in -lboost_regex-mt... yes
checking for main in -lboost_system-gcc-mt... no
checking for main in -lboost_system-mt... yes
checking for main in -lboost_date_time-gcc-mt... no
checking for main in -lboost_date_time-mt... yes
checking boost/asio.hpp usability... yes
checking boost/asio.hpp presence... yes
checking for boost/asio.hpp... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LUA... yes
checking sqlite3.h usability... yes
checking sqlite3.h presence... yes
checking for sqlite3.h... yes
checking for main in -lsqlite3... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
pontus@Pontus-PC:~/otserv/otserv-062-src$ make
make  all-am
make[1]: Entering directory `/home/pontus/otserv/otserv-062-src'
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT databasesqlite.o -MD -MP -MF .deps/databasesqlite.Tpo -c -o databasesqlite.o databasesqlite.cpp
mv -f .deps/databasesqlite.Tpo .deps/databasesqlite.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT account.o -MD -MP -MF .deps/account.Tpo -c -o account.o account.cpp
mv -f .deps/account.Tpo .deps/account.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT container.o -MD -MP -MF .deps/container.Tpo -c -o container.o container.cpp
mv -f .deps/container.Tpo .deps/container.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT creature.o -MD -MP -MF .deps/creature.Tpo -c -o creature.o creature.cpp
mv -f .deps/creature.Tpo .deps/creature.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT game.o -MD -MP -MF .deps/game.Tpo -c -o game.o game.cpp
mv -f .deps/game.Tpo .deps/game.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT ioaccount.o -MD -MP -MF .deps/ioaccount.Tpo -c -o ioaccount.o ioaccount.cpp
mv -f .deps/ioaccount.Tpo .deps/ioaccount.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT iomapxml.o -MD -MP -MF .deps/iomapxml.Tpo -c -o iomapxml.o iomapxml.cpp
mv -f .deps/iomapxml.Tpo .deps/iomapxml.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT ioplayer.o -MD -MP -MF .deps/ioplayer.Tpo -c -o ioplayer.o ioplayer.cpp
mv -f .deps/ioplayer.Tpo .deps/ioplayer.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT database.o -MD -MP -MF .deps/database.Tpo -c -o database.o database.cpp
mv -f .deps/database.Tpo .deps/database.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT item.o -MD -MP -MF .deps/item.Tpo -c -o item.o item.cpp
mv -f .deps/item.Tpo .deps/item.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT items.o -MD -MP -MF .deps/items.Tpo -c -o items.o items.cpp
mv -f .deps/items.Tpo .deps/items.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT luascript.o -MD -MP -MF .deps/luascript.Tpo -c -o luascript.o luascript.cpp
mv -f .deps/luascript.Tpo .deps/luascript.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT map.o -MD -MP -MF .deps/map.Tpo -c -o map.o map.cpp
mv -f .deps/map.Tpo .deps/map.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT monster.o -MD -MP -MF .deps/monster.Tpo -c -o monster.o monster.cpp
mv -f .deps/monster.Tpo .deps/monster.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT networkmessage.o -MD -MP -MF .deps/networkmessage.Tpo -c -o networkmessage.o networkmessage.cpp
mv -f .deps/networkmessage.Tpo .deps/networkmessage.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT npc.o -MD -MP -MF .deps/npc.Tpo -c -o npc.o npc.cpp
mv -f .deps/npc.Tpo .deps/npc.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT otserv.o -MD -MP -MF .deps/otserv.Tpo -c -o otserv.o otserv.cpp
mv -f .deps/otserv.Tpo .deps/otserv.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT player.o -MD -MP -MF .deps/player.Tpo -c -o player.o player.cpp
mv -f .deps/player.Tpo .deps/player.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT position.o -MD -MP -MF .deps/position.Tpo -c -o position.o position.cpp
mv -f .deps/position.Tpo .deps/position.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT protocolgame.o -MD -MP -MF .deps/protocolgame.Tpo -c -o protocolgame.o protocolgame.cpp
mv -f .deps/protocolgame.Tpo .deps/protocolgame.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT spells.o -MD -MP -MF .deps/spells.Tpo -c -o spells.o spells.cpp
mv -f .deps/spells.Tpo .deps/spells.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT status.o -MD -MP -MF .deps/status.Tpo -c -o status.o status.cpp
mv -f .deps/status.Tpo .deps/status.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT thing.o -MD -MP -MF .deps/thing.Tpo -c -o thing.o thing.cpp
mv -f .deps/thing.Tpo .deps/thing.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT tile.o -MD -MP -MF .deps/tile.Tpo -c -o tile.o tile.cpp
mv -f .deps/tile.Tpo .deps/tile.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT tools.o -MD -MP -MF .deps/tools.Tpo -c -o tools.o tools.cpp
tools.cpp: In function ‘uint32_t rand24b()’:
tools.cpp:224: warning: suggest parentheses around arithmetic in operand of ^
mv -f .deps/tools.Tpo .deps/tools.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT spawn.o -MD -MP -MF .deps/spawn.Tpo -c -o spawn.o spawn.cpp
mv -f .deps/spawn.Tpo .deps/spawn.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT actions.o -MD -MP -MF .deps/actions.Tpo -c -o actions.o actions.cpp
mv -f .deps/actions.Tpo .deps/actions.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT commands.o -MD -MP -MF .deps/commands.Tpo -c -o commands.o commands.cpp
mv -f .deps/commands.Tpo .deps/commands.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT depot.o -MD -MP -MF .deps/depot.Tpo -c -o depot.o depot.cpp
mv -f .deps/depot.Tpo .deps/depot.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT md5.o -MD -MP -MF .deps/md5.Tpo -c -o md5.o md5.cpp
mv -f .deps/md5.Tpo .deps/md5.Po
g++ -DHAVE_CONFIG_H -I.    -I/usr/include/libxml2  -I/usr/include/lua5.1     -D__USE_SQLITE__     -D_THREAD_SAFE -D_REENTRANT -Wall -g -O2 -MT fileloader.o -MD -MP -MF .deps/fileloader.Tpo -c -o fileloader.o fileloader.cpp
fileloader.cpp: In member function ‘bool FileLoader::openFile(const char*, bool, bool)’:
fileloader.cpp:75: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result
fileloader.cpp: In member function ‘long int FileLoader::loadCacheBlock(long unsigned int)’:
fileloader.cpp:509: error: ‘abs’ is not a member of ‘std’
make[1]: *** [fileloader.o] Error 1
make[1]: Leaving directory `/home/pontus/otserv/otserv-062-src'
make: *** [all] Error 2

```

---

### Post by Wha! on 2009-06-20
Maby it did not compile right. I donno :/

---

### Post by DEMWilson on 2009-10-06
> fileloader.cpp:75: warning: ignoring return value of &#8216;size_t fread(void*, size_t, size_t, FILE*)&#8217;, declared with attribute warn_unused_result
fileloader.cpp: In member function &#8216;long int FileLoader::loadCacheBlock(long unsigned int)&#8217;:
fileloader.cpp:509: error: &#8216;abs&#8217; is not a member of &#8216;std&#8217;
make[1]: *** [fileloader.o] Error 1
make[1]: Leaving directory `/home/pontus/otserv/otserv-062-src'
make: *** [all] Error 2

Open *fileloader.cpp* and then go to line 509
delete the part that has std::
It'll look something like this
```
std::abs(
```

so when you remove the std it should look like this
```
abs(
```

It's just some minor problems when compiling on linux, I thought I had posted a fix for it but I guess I haven't.
I'll post it if it's still a problem.

~OsoSangre

---

