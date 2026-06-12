---
title: "Problem with Battle for Wesnoth"
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by bamesah on 2007-06-17
Hi guys,

After I tried to uninstall Battle for Wesnoth 1.2.3 and install 1.2.5 , I reinstalled 1.2.3 again,

from that time whenever i try to press Get add-ons or go to the [http://wolff.to/campaigns/list.html](http://wolff.to/campaigns/list.html) to get add-ons manually , it doesn't work gives Remote Host disoconected, In the wesnoth forums they say that this is because of the load on the server but that can't be because it used to work with me without any problem b4 re-installation



Is there any solution to this??

If no solution, when I download the source for Battle for Wesnoth 1.2.5
I use 
./configure

when i write in the terminal:

make

it starts repeating this:

make[2]: Entering directory `/home/badr/wesnoth-1.2.5/src'
depbase=`echo filesystem.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
        g++ -DHAVE_CONFIG_H -I. -I..   -I/usr/include/freetype2 -I ./sdl_ttf -I../intl -I../intl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DWESNOTH_PATH=\"/usr/local/share/wesnoth\" -DLOCALEDIR=\"translations\" -DHAS_RELATIVE_LOCALEDIR=1 -DFIFODIR=\"/usr/local/var/run/wesnothd\" -DHAVE_FRIBIDI -I/usr/include -O2 -W -Wall -ansi  -D_X11    -MT filesystem.o -MD -MP -MF $depbase.Tpo -c -o filesystem.o filesystem.cpp &&\
        mv -f $depbase.Tpo $depbase.Po
depbase=`echo game_config.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
        g++ -DHAVE_CONFIG_H -I. -I..   -I/usr/include/freetype2 -I ./sdl_ttf -I../intl -I../intl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DWESNOTH_PATH=\"/usr/local/share/wesnoth\" -DLOCALEDIR=\"translations\" -DHAS_RELATIVE_LOCALEDIR=1 -DFIFODIR=\"/usr/local/var/run/wesnothd\" -DHAVE_FRIBIDI -I/usr/include -O2 -W -Wall -ansi  -D_X11    -MT game_config.o -MD -MP -MF $depbase.Tpo -c -o game_config.o game_config.cpp &&\
        mv -f $depbase.Tpo $depbase.Po
depbase=`echo serialization/preprocessor.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
        g++ -DHAVE_CONFIG_H -I. -I..   -I/usr/include/freetype2 -I ./sdl_ttf -I../intl -I../intl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DWESNOTH_PATH=\"/usr/local/share/wesnoth\" -DLOCALEDIR=\"translations\" -DHAS_RELATIVE_LOCALEDIR=1 -DFIFODIR=\"/usr/local/var/run/wesnothd\" -DHAVE_FRIBIDI -I/usr/include -O2 -W -Wall -ansi  -D_X11    -MT serialization/preprocessor.o -MD -MP -MF $depbase.Tpo -c -o serialization/preprocessor.o serialization/preprocessor.cpp &&\
        mv -f $depbase.Tpo $depbase.Po
depbase=`echo zipios++/xcoll.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
        g++ -DHAVE_CONFIG_H -I. -I..   -I/usr/include/freetype2 -I ./sdl_ttf -I../intl -I../intl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -DWESNOTH_PATH=\"/usr/local/share/wesnoth\" -DLOCALEDIR=\"translations\" -DHAS_RELATIVE_LOCALEDIR=1 -DFIFODIR=\"/usr/local/var/run/wesnothd\" -DHAVE_FRIBIDI -I/usr/include -O2 -W -Wall -ansi  -D_X11    -MT zipios++/xcoll.o -MD -MP -MF $depbase.Tpo -c -o zipios++/xcoll.o zipios++/xcoll.cpp &&\
        mv -f $depbase.Tpo $depbase.Po

I don't know what is the problem??

---

### Post by EdThaSlayer on 2007-06-17
First of all
> In the wesnoth forums they say that this is because of the load on the server but that can't be because it used to work with me without any problem b4 re-installation
Not being able to reach a website is an internet problem, not a game problem. :)
So the wesnoth guys were right. 

Second, you might not have all the libraries needed to install this latest version of battle of wesnoth. The make doesn't seem to be failing as it takes time to compile Battle of Wesnoth. THe reason I say this is because I don't see "filesystem.o filesystem.cpp &&\" ,"-o game_config.o game_config.cpp &&\", and "$depbase.Tpo -c -o serialization/preprocessor.o serialization/preprocessor.cpp &&\" being repeated over and over again. Just let it compile, and if there is an error(where it actually says there is an error. Then post that error. :)  (Because of the time it takes to compile I always prefer to use the one in the repositories).
Look closer :)

> 
make[2]: Entering directory `/home/badr/wesnoth-1.2.5/src'
depbase=`echo filesystem.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/freetype2 -I ./sdl_ttf -I../intl -I../intl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWESNOTH_PATH=\"/usr/local/share/wesnoth\" -DLOCALEDIR=\"translations\" -DHAS_RELATIVE_LOCALEDIR=1 -DFIFODIR=\"/usr/local/var/run/wesnothd\" -DHAVE_FRIBIDI -I/usr/include -O2 -W -Wall -ansi -D_X11 -MT filesystem.o -MD -MP -MF $depbase.Tpo -c -o **filesystem.o filesystem.cpp &&\**
mv -f $depbase.Tpo $depbase.Po
depbase=`echo game_config.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/freetype2 -I ./sdl_ttf -I../intl -I../intl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWESNOTH_PATH=\"/usr/local/share/wesnoth\" -DLOCALEDIR=\"translations\" -DHAS_RELATIVE_LOCALEDIR=1 -DFIFODIR=\"/usr/local/var/run/wesnothd\" -DHAVE_FRIBIDI -I/usr/include -O2 -W -Wall -ansi **-D_X11 -MT game_config.o -MD -MP -MF $depbase.Tpo -c -o game_config.o game_config.cpp **&&\
mv -f $depbase.Tpo $depbase.Po
depbase=`echo serialization/preprocessor.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/freetype2 -I ./sdl_ttf -I../intl -I../intl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWESNOTH_PATH=\"/usr/local/share/wesnoth\" -DLOCALEDIR=\"translations\" -DHAS_RELATIVE_LOCALEDIR=1 -DFIFODIR=\"/usr/local/var/run/wesnothd\" -DHAVE_FRIBIDI -I/usr/include -O2 -W -Wall -ansi **-D_X11 -MT serialization/preprocessor.o -MD -MP -MF $depbase.Tpo -c -o **serialization/preprocessor.o serialization/preprocessor.cpp &&\
mv -f $depbase.Tpo $depbase.Po
depbase=`echo zipios++/xcoll.o | sed 's|[^/]*$|.deps/&|;s|\.o$||'`;\
g++ -DHAVE_CONFIG_H -I. -I.. -I/usr/include/freetype2 -I ./sdl_ttf -I../intl -I../intl -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DWESNOTH_PATH=\"/usr/local/share/wesnoth\" -DLOCALEDIR=\"translations\" -DHAS_RELATIVE_LOCALEDIR=1 -DFIFODIR=\"/usr/local/var/run/wesnothd\" -DHAVE_FRIBIDI -I/usr/include -O2 -W -Wall -ansi **-D_X11 -MT zipios++/xcoll.o -MD -MP -MF $depbase.Tpo -c -o zipios++/xcoll.o **zipios++/xcoll.cpp &&\
mv -f $depbase.Tpo $depbase.Po
It's always doing something different using the same make script. :popcorn:

---

### Post by hikaricore on 2007-06-17
I'm not trying to discourage you from learning to compile, because it's a very important thing to understand when using Linux.

But if you don't need the absolute latest version, 1.2.4 is availible at GetDeb.net in their games section:
[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3) (near the bottom of the page)
Easily installable Ubuntu Feisty packages for painless download and setup. (be sure to get all wesnoth packages)

The should have 1.2.5 up within a few weeks. They just updated their versions of SMC and Xmoto which came out this weekend.
I absolutely love their turn around time.  ^_^

---

### Post by bamesah on 2007-06-17
> **EdThaSlayer said:**
> First of all

Not being able to reach a website is an internet problem, not a game problem. :)
So the wesnoth guys were right. 

Second, you might not have all the libraries needed to install this latest version of battle of wesnoth. The make doesn't seem to be failing as it takes time to compile Battle of Wesnoth. THe reason I say this is because I don't see "filesystem.o filesystem.cpp &&\" ,"-o game_config.o game_config.cpp &&\", and "$depbase.Tpo -c -o serialization/preprocessor.o serialization/preprocessor.cpp &&\" being repeated over and over again. Just let it compile, and if there is an error(where it actually says there is an error. Then post that error. :)  (Because of the time it takes to compile I always prefer to use the one in the repositories).
Look closer :)


It's always doing something different using the same make script. :popcorn:

Maybe there isn't really an error but it just stayed like this for a whole 30 min. so i am not sure, i will leave it for 2 hours again ans see??

---

### Post by bamesah on 2007-06-17
> **hikaricore said:**
> I'm not trying to discourage you from learning to compile, because it's a very important thing to understand when using Linux.

But if you don't need the absolute latest version, 1.2.4 is availible at GetDeb.net in their games section:
[http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3) (near the bottom of the page)
Easily installable Ubuntu Feisty packages for painless download and setup. (be sure to get all wesnoth packages)

The should have 1.2.5 up within a few weeks. They just updated their versions of SMC and Xmoto which came out this weekend.
I absolutely love their turn around time.  ^_^

I don't want to download from Getdeb.net because it doesn't have all packages that are in the Synaptice Manager and i don't want to dl from Synaptic coz it is old

---

### Post by EdThaSlayer on 2007-06-17
> **bamesah said:**
> I don't want to download from Getdeb.net because it doesn't have all packages that are in the Synaptice Manager and i don't want to dl from Synaptic coz it is old

Well, the getdeb version should also be able to get the packages for you. It's also much easier to install, just a double-click does the job. :)

---

### Post by bamesah on 2007-06-17
> **EdThaSlayer said:**
> Well, the getdeb version should also be able to get the packages for you. It's also much easier to install, just a double-click does the job. :)

Are  u sure it contains all the nedded packages, coz in Synaptic I see a lot more Campain Packages

---

