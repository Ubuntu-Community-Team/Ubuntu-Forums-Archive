---
title: "errors with vlc compilation"
date: 2008-12-16
forum: General Help
---

### Post by Meow27 on 2008-12-16
ok i was able to configure vlc with --disable-zvbi

it succeeded but i got this problem when doing make


```
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../..   -I../../include -I../../include  -DSYS_LINUX `top_builddir="../.." ../../vlc-config --cflags plugin libogg_plugin_la-ogg.lo` -Wall -Wextra -Wsign-compare -Wundef -Wpointer-arith -Wbad-function-cast -Wcast-align -Wwrite-strings -Wmissing-prototypes -Wvolatile-register-var -Werror-implicit-function-declaration -MT libogg_plugin_la-ogg.lo -MD -MP -MF .deps/libogg_plugin_la-ogg.Tpo -c -o libogg_plugin_la-ogg.lo `test -f 'ogg.c' || echo './'`ogg.c
 gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../.. -I../../include -I../../include -DSYS_LINUX -I/usr/local/include -D_FILE_OFFSET_BITS=64 -D__USE_UNIX98 -D_LARGEFILE64_SOURCE -D_REENTRANT -D_THREAD_SAFE -D__LIBVLC__ -D__PLUGIN__ -DMODULE_NAME=ogg -DMODULE_NAME_IS_ogg -DMODULE_STRING=\"ogg\" -O2 -ffast-math -funroll-loops -mtune=pentium2 -fomit-frame-pointer -Wall -Wextra -Wsign-compare -Wundef -Wpointer-arith -Wbad-function-cast -Wcast-align -Wwrite-strings -Wmissing-prototypes -Wvolatile-register-var -Werror-implicit-function-declaration -MT libogg_plugin_la-ogg.lo -MD -MP -MF .deps/libogg_plugin_la-ogg.Tpo -c ogg.c  -fPIC -DPIC -o .libs/libogg_plugin_la-ogg.o
In file included from ../../include/vlc_common.h:500,
                 from ogg.c:32:
../../include/vlc_mtime.h:80: warning: ‘error’ attribute directive ignored
../../include/vlc_mtime.h:90: warning: ‘warning’ attribute directive ignored
../../include/vlc_mtime.h:108: warning: ‘error’ attribute directive ignored
In file included from ../../include/vlc_common.h:867,
                 from ogg.c:32:
../../include/vlc_variables.h: In function ‘__var_AssertType’:
../../include/vlc_variables.h:202: warning: unused variable ‘i_type’
../../include/vlc_variables.h:200: warning: unused parameter ‘i_expected’
ogg.c:43:20: error: vorbis.h: No such file or directory
ogg.c: In function ‘Ogg_FindLogicalStreams’:
ogg.c:1098: warning: comparison between signed and unsigned
ogg.c:1218: warning: comparison between signed and unsigned
ogg.c: In function ‘Ogg_ExtractXiphMeta’:
ogg.c:1520: error: implicit declaration of function ‘vorbis_ParseComment’
make[5]: *** [libogg_plugin_la-ogg.lo] Error 1
make[5]: Leaving directory `/home/meow/Program_Files/vlc-1.0.0-git/modules/demux'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/meow/Program_Files/vlc-1.0.0-git/modules/demux'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/meow/Program_Files/vlc-1.0.0-git/modules/demux'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/meow/Program_Files/vlc-1.0.0-git/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/meow/Program_Files/vlc-1.0.0-git'
make: *** [all] Error 2

```

i have libvorbis-dev installed >.>

dont know what to disable during the configure or what to install help plz? 

fyi my previous post was here
[http://ubuntuforums.org/showthread.php?t=1011560](http://ubuntuforums.org/showthread.php?t=1011560)

---

### Post by Polygon on 2008-12-16
if your compiling from git, it might not compile at all..... which may be why it errors out

is there any reason why your compiling from git anyway?

---

### Post by mc4man on 2008-12-16
Try building 0.9.8a from here

[http://www.videolan.org/vlc/download-sources.html](http://www.videolan.org/vlc/download-sources.html)

I've built it twice on 8.04 recently with no problems (once with embedded video enabled, once without.

What's interesting is about 3 wks. ago I built a 1.0 snapshot with no problems.
Today I tried the latest 1.0 and got the exact same error you posted - exact.

Configured out ogg and vorbis no change, same error. I went back and grabbed the source from 3 weeks ago and it built fine. So somethings changed, maybe version wise, maybe code wise. I've only seen vorbis.h in the ffmpeg source, not in the libvorbis or libogg -devs.

If anyone reading here knows how to output the terminal to a text file during a make I'd like to compare the two makes. (way too many lines to be able to scroll back

If you wish post post your ./configure command before building from above link


Edit: the problem seems to be around here
in sources that build, in 1.0.0-git/modules/demux/ogg.c  (also ..demux/flac.c has vorbis.h

> #ifdef HAVE_CONFIG_H
# include "config.h"
#endif

#include <vlc_common.h>
#include <vlc_plugin.h>
#include <vlc_demux.h>
#include <vlc_meta.h>
#include <vlc_input.h>

#include <ogg/ogg.h>

in ones that don't

> #ifdef HAVE_CONFIG_H
# include "config.h"
#endif

#include <vlc_common.h>
#include <vlc_plugin.h>
#include <vlc_demux.h>
#include <vlc_meta.h>
#include <vlc_input.h>

#include <ogg/ogg.h>

#include <vlc_codecs.h>
#include <vlc_bits.h>
#include <vlc_charset.h>
#include "vorbis.h"    


---

### Post by Meow27 on 2008-12-16
> **Polygon said:**
> 

is there any reason why your compiling from git anyway?

yes cause if im gonna be compiling something, i might as well try the latest version i can get (with the risk of instability)

---

### Post by mc4man on 2008-12-16
@ Meow27

I got the latest git to build and run, there are about 16 lines of code in 5 files that needed attention. Hardly worth the effort for what is termed "an unstable' release. (and may be more so after i 'fixed' it.

I'd suggest sticking with  the the stable release if you want to build (0.9.8a

Otherwise if you wanted to test 1.0 releases then get nightly build binaries for ubuntu. (note they are only available for intrepid.

Also note that a least for me the things that are broken that I care about in 0.9.8a are still that way in 1.0.

---

### Post by Meow27 on 2008-12-17
im not sure wether i should mark this post solved then.... i did get what i wanted (a newer version of vlc so i can play flv files) but the git was intended origionally for compilation...

i guess ill just leave it like this :)

p.s. yes i was able to compile 0.9.8a but the make install does work (w00t) so im shortcutting all permission to the compiled folder :P

---

