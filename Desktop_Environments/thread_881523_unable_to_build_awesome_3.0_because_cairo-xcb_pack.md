---
title: "unable to build awesome 3.0 because cairo-xcb package missing"
date: 2008-08-06
forum: Desktop Environments
---

### Post by prototype_angel on 2008-08-06
I want to build the awesome 3.0 desktop manager.

Here's the output of $ make on my hardy system with all dependencies satisfied.

```

[13:03]...bird/awesome-3.0-rc1: make
Running cmake…
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- cat -> /bin/cat
-- ln -> /bin/ln
-- grep -> /bin/grep
-- git not found.
-- hostname -> /bin/hostname
-- gperf -> /usr/bin/gperf
-- luac -> /usr/bin/luac
-- asciidoc -> /usr/bin/asciidoc
-- xmlto -> /usr/bin/xmlto
-- gzip -> /bin/gzip
-- lua -> /usr/bin/lua
-- luadoc not found.
-- Looking for doxygen...
-- Looking for doxygen... - found /usr/bin/doxygen
-- Looking for dot tool...
-- Looking for dot tool... - NOT found
-- Not generating luadoc. Missing: luadoc
-- checking for modules 'glib-2.0;cairo;pango;gdk-2.0>=2.2;gdk-pixbuf-2.0>=2.2;xcb;xcb-event;xcb-randr;xcb-xinerama;xcb-shape;xcb-aux;xcb-atom;xcb-keysyms;xcb-render;xcb-icccm;cairo-xcb'
--   package 'cairo-xcb' not found
CMake Error: A required package was not found
CMake Error: 
-- Configuring done
make: *** [.build-deepthought-i486-linux-gnu-4.2.3/CMakeCache.txt] Error 255

```

Can someone tell me where I can find "cairo-xcb"

---

### Post by shearn89 on 2008-08-06
hey - posted on my awesome howto thread. There's a link to the source, and the required ./configure switches.

---

