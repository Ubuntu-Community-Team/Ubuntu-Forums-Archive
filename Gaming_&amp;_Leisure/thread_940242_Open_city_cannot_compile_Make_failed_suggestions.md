---
title: "Open city cannot compile Make failed suggestions?"
date: 2008-10-06
forum: Gaming &amp; Leisure
---

### Post by ironslave on 2008-10-06
I followed this guide [Open city]("http://gaming.gwos.org/doku.php/guides:32bit:open_city")


I am not to good with compiling software and it usually fails :( can anyone help me figure this out? 

i am running 32 BIT Hardy 8.041

```
james@LinuxMode:~/Desktop/opencity-0.0.5stable$ make
make  all-recursive
make[1]: Entering directory `/home/james/Desktop/opencity-0.0.5stable'
Making all in config
make[2]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/config'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/config'
Making all in docs
make[2]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/docs'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/docs'
Making all in src
make[2]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/src'
Making all in binreloc
make[3]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/src/binreloc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/src/binreloc'
Making all in enum
make[3]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/src/enum'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/src/enum'
Making all in mapgen
make[3]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/src/mapgen'
if gcc -DHAVE_CONFIG_H -I. -I. -I../..  -I../../src/mapgen/ -I../../src/mapgen/filter -I../../src/mapgen/generator -I../../src   -I/usr/X11R6/include  -DNDEBUG -Wall -Wmissing-braces -Wparentheses -ansi -pedantic-errors -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT pngfuncs.o -MD -MP -MF ".deps/pngfuncs.Tpo" -c -o pngfuncs.o pngfuncs.c; \
        then mv -f ".deps/pngfuncs.Tpo" ".deps/pngfuncs.Po"; else rm -f ".deps/pngfuncs.Tpo"; exit 1; fi
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
make[3]: *** [pngfuncs.o] Error 1
make[3]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/src/mapgen'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable'
make: *** [all] Error 2
james@LinuxMode:~/Desktop/opencity-0.0.5stable$ make
make  all-recursive
make[1]: Entering directory `/home/james/Desktop/opencity-0.0.5stable'
Making all in config
make[2]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/config'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/config'
Making all in docs
make[2]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/docs'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/docs'
Making all in src
make[2]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/src'
Making all in binreloc
make[3]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/src/binreloc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/src/binreloc'
Making all in enum
make[3]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/src/enum'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/src/enum'
Making all in mapgen
make[3]: Entering directory `/home/james/Desktop/opencity-0.0.5stable/src/mapgen'
if gcc -DHAVE_CONFIG_H -I. -I. -I../..  -I../../src/mapgen/ -I../../src/mapgen/filter -I../../src/mapgen/generator -I../../src   -I/usr/X11R6/include  -DNDEBUG -Wall -Wmissing-braces -Wparentheses -ansi -pedantic-errors -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -MT pngfuncs.o -MD -MP -MF ".deps/pngfuncs.Tpo" -c -o pngfuncs.o pngfuncs.c; \
        then mv -f ".deps/pngfuncs.Tpo" ".deps/pngfuncs.Po"; else rm -f ".deps/pngfuncs.Tpo"; exit 1; fi
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from pngfuncs.h:26,
                 from pngfuncs.c:24:
/usr/include/SDL/begin_code.h:94:8: error: extra tokens at end of #endif directive
make[3]: *** [pngfuncs.o] Error 1
make[3]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/src/mapgen'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/james/Desktop/opencity-0.0.5stable'
make: *** [all] Error 2
james@LinuxMode:~/Desktop/opencity-0.0.5stable$                                           
```

---

