---
title: "building AwesomeWM 3.4.9"
date: 2011-01-19
forum: Desktop Environments
---

### Post by 0nelove on 2011-01-19
Anybody having success building awesomeWM?  I've been using it for a few weeks from the .deb, but building the 3.4.9 (stable) is giving me some trouble.  Did have a go at installing the required dependencies as described in the wiki linked below, but still obviously missing something.  Thanks for any help.

```
Running make Makefile…
Building…
Scanning dependencies of target generated_sources
[  0%] Generating atoms-intern.h
[  0%] Generating atoms-extern.h
[  0%] Generating common/tokenize.c
[  0%] Generating common/tokenize.h
[  3%] Built target generated_sources
Scanning dependencies of target awesome
[  3%] Building C object CMakeFiles/awesome.dir/awesome.c.o
[  4%] Building C object CMakeFiles/awesome.dir/client.c.o
[  5%] Building C object CMakeFiles/awesome.dir/strut.c.o
[  6%] Building C object CMakeFiles/awesome.dir/dbus.c.o
[  6%] Building C object CMakeFiles/awesome.dir/root.c.o
[  7%] Building C object CMakeFiles/awesome.dir/event.c.o
/home/xx/awesome-3.4.9/event.c: In function ‘xerror’:
/home/xx/awesome-3.4.9/event.c:798: error: ‘XCB_EVENT_ERROR_BAD_WINDOW’ undeclared (first use in this function)
/home/xx/awesome-3.4.9/event.c:798: error: (Each undeclared identifier is reported only once
/home/xx/awesome-3.4.9/event.c:798: error: for each function it appears in.)
/home/xx/awesome-3.4.9/event.c:799: error: ‘XCB_EVENT_ERROR_BAD_MATCH’ undeclared (first use in this function)
/home/xx/awesome-3.4.9/event.c:801: error: ‘XCB_EVENT_ERROR_BAD_VALUE’ undeclared (first use in this function)
make[3]: *** [CMakeFiles/awesome.dir/event.c.o] Error 1
make[2]: *** [CMakeFiles/awesome.dir/all] Error 2
make[1]: *** [all] Error 2
make: *** [cmake-build] Error 2


```
similar problem here: [http://superuser.com/questions/232495/building-awesome-wm](http://superuser.com/questions/232495/building-awesome-wm)
similar error, unresolved:
[http://askubuntu.com/questions/21281/building-awesome-wm](http://askubuntu.com/questions/21281/building-awesome-wm)
build instructions (old): [https://awesome.naquadah.org/wiki/Awesome-3-Ubuntu-git](https://awesome.naquadah.org/wiki/Awesome-3-Ubuntu-git)


FULL output of make:
```

Running cmake…
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
-- cat -> /bin/cat
-- ln -> /bin/ln
-- grep -> /bin/grep
-- git -> /usr/bin/git
-- hostname -> /bin/hostname
-- gperf -> /usr/bin/gperf
-- asciidoc -> /usr/bin/asciidoc
-- xmlto -> /usr/bin/xmlto
-- gzip -> /bin/gzip
-- lua -> /usr/bin/lua
-- luadoc -> /usr/bin/luadoc
-- convert -> /usr/bin/convert
-- Found Doxygen: /usr/bin/doxygen
-- Found Lua51: /usr/lib/liblua5.1.so;/usr/lib/libm.so
-- checking for module 'xcb>=1.4'
--   found xcb, version 1.5
-- checking for modules 'glib-2.0;cairo;x11;pango>=1.19.3;pangocairo>=1.19.3;xcb-randr;xcb-xtest;xcb-xinerama;xcb-shape;xcb-aux>=0.3.0;xcb-atom>=0.3.0;xcb-keysyms>=0.3.4;xcb-icccm>=0.3.6;xcb-image>=0.3.0;cairo-xcb;libstartup-notification-1.0>=0.10;xproto>=7.0.15;imlib2;libxdg-basedir>=1.0.0'
--   found glib-2.0, version 2.24.1
--   found cairo, version 1.8.10
--   found x11, version 1.3.2
--   found pango, version 1.28.0
--   found pangocairo, version 1.28.0
--   found xcb-randr, version 1.5
--   found xcb-xtest, version 1.5
--   found xcb-xinerama, version 1.5
--   found xcb-shape, version 1.5
--   found xcb-aux, version 0.3.7
--   found xcb-atom, version 0.3.7
--   found xcb-keysyms, version 0.3.7
--   found xcb-icccm, version 0.3.7
--   found xcb-image, version 0.3.7
--   found cairo-xcb, version 1.8.10
--   found libstartup-notification-1.0, version 0.10
--   found xproto, version 7.0.16
--   found imlib2, version 1.4.2
--   found libxdg-basedir, version 1.0.2
-- Looking for backtrace_symbols
-- Looking for backtrace_symbols - found
-- checking for execinfo -- found
-- checking for __builtin_clz -- yes
-- checking for module 'dbus-1'
--   found dbus-1, version 1.2.16
-- Configuring lib/naughty.lua
-- Configuring lib/beautiful.lua
-- Configuring lib/awful/client.lua
-- Configuring lib/awful/layout/suit/fair.lua
-- Configuring lib/awful/layout/suit/spiral.lua
-- Configuring lib/awful/layout/suit/init.lua
-- Configuring lib/awful/layout/suit/tile.lua
-- Configuring lib/awful/layout/suit/floating.lua
-- Configuring lib/awful/layout/suit/max.lua
-- Configuring lib/awful/layout/suit/magnifier.lua
-- Configuring lib/awful/layout/init.lua
-- Configuring lib/awful/tag.lua
-- Configuring lib/awful/tooltip.lua
-- Configuring lib/awful/button.lua
-- Configuring lib/awful/placement.lua
-- Configuring lib/awful/startup_notification.lua
-- Configuring lib/awful/titlebar.lua
-- Configuring lib/awful/init.lua
-- Configuring lib/awful/hooks.lua
-- Configuring lib/awful/key.lua
-- Configuring lib/awful/menu.lua
-- Configuring lib/awful/screen.lua
-- Configuring lib/awful/completion.lua
-- Configuring lib/awful/dbus.lua
-- Configuring lib/awful/autofocus.lua
-- Configuring lib/awful/remote.lua
-- Configuring lib/awful/rules.lua
-- Configuring lib/awful/prompt.lua
-- Configuring lib/awful/util.lua
-- Configuring lib/awful/wibox.lua
-- Configuring lib/awful/mouse/init.lua
-- Configuring lib/awful/mouse/finder.lua
-- Configuring lib/awful/widget/layout/init.lua
-- Configuring lib/awful/widget/layout/default.lua
-- Configuring lib/awful/widget/layout/horizontal.lua
-- Configuring lib/awful/widget/layout/vertical.lua
-- Configuring lib/awful/widget/button.lua
-- Configuring lib/awful/widget/graph.lua
-- Configuring lib/awful/widget/init.lua
-- Configuring lib/awful/widget/layoutbox.lua
-- Configuring lib/awful/widget/taglist.lua
-- Configuring lib/awful/widget/textclock.lua
-- Configuring lib/awful/widget/tasklist.lua
-- Configuring lib/awful/widget/common.lua
-- Configuring lib/awful/widget/prompt.lua
-- Configuring lib/awful/widget/launcher.lua
-- Configuring lib/awful/widget/progressbar.lua
-- Configuring themes/sky//theme.lua
-- Configuring themes/zenburn//theme.lua
-- Configuring themes/default//theme.lua
-- Configuring config.h
-- Configuring awesomerc.lua
-- Configuring awesome-version-internal.h
-- Configuring awesome.doxygen
-- Configuring done
-- Generating done
-- Build files have been written to: /home/xx/awesome-3.4.9/.build-xx-x86_64-linux-gnu-4.4.3
Running make Makefile…
Building…
Scanning dependencies of target generated_sources
[  0%] Generating atoms-intern.h
[  0%] Generating atoms-extern.h
[  0%] Generating common/tokenize.c
[  0%] Generating common/tokenize.h
[  3%] Built target generated_sources
Scanning dependencies of target awesome
[  3%] Building C object CMakeFiles/awesome.dir/awesome.c.o
[  4%] Building C object CMakeFiles/awesome.dir/client.c.o
[  5%] Building C object CMakeFiles/awesome.dir/strut.c.o
[  6%] Building C object CMakeFiles/awesome.dir/dbus.c.o
[  6%] Building C object CMakeFiles/awesome.dir/root.c.o
[  7%] Building C object CMakeFiles/awesome.dir/event.c.o

/home/xx/awesome-3.4.9/event.c: In function ‘xerror’:
/home/xx/awesome-3.4.9/event.c:798: error: ‘XCB_EVENT_ERROR_BAD_WINDOW’ undeclared (first use in this function)
/home/xx/awesome-3.4.9/event.c:798: error: (Each undeclared identifier is reported only once
/home/xx/awesome-3.4.9/event.c:798: error: for each function it appears in.)
/home/xx/awesome-3.4.9/event.c:799: error: ‘XCB_EVENT_ERROR_BAD_MATCH’ undeclared (first use in this function)
/home/xx/awesome-3.4.9/event.c:801: error: ‘XCB_EVENT_ERROR_BAD_VALUE’ undeclared (first use in this function)
make[3]: *** [CMakeFiles/awesome.dir/event.c.o] Error 1
make[2]: *** [CMakeFiles/awesome.dir/all] Error 2
make[1]: *** [all] Error 2
make: *** [cmake-build] Error 2

```

---

### Post by VampyrePrince on 2011-01-22
Looks like you're having errors with XCB. Have you tried updating it?

---

### Post by 0nelove on 2011-01-23
Think xcb is all set (see above -version 2.4).  Included full output of make.. (sry for that omission).
xcb -V
xcb version Xcb 2.4

---

### Post by 0nelove on 2011-01-30
Never had success building it, but here's a link in case somebody else stumbles on this post with the same problem.

[http://packages.debian.org/sid/awesome](http://packages.debian.org/sid/awesome)

---

