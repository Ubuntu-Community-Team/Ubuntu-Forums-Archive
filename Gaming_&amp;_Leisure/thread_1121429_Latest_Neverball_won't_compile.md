---
title: "Latest Neverball won't compile"
date: 2009-04-10
forum: Gaming &amp; Leisure
---

### Post by jdunn on 2009-04-10
I compiled and ran Neverball 1.5.0 a few weeks ago without any issues.  No such luck with version 1.5.1.  Has anyone had luck with this?

---

### Post by hikaricore on 2009-04-10
Getdeb.net to the rescue?

[http://www.getdeb.net/app/Neverball](http://www.getdeb.net/app/Neverball)

^_^

*edit* oops sorry i just saw that you were trying to compile 1.5.1  >.<  I guess I should be sure to read the whole post in the future. lol
Anyways, did you check that your dependencies for the build were up to date?  Some compile error output would probably be helpful in diagnosing the problem as well..

---

### Post by jdunn on 2009-04-10
> **hikaricore said:**
> Getdeb.net to the rescue?

[http://www.getdeb.net/app/Neverball](http://www.getdeb.net/app/Neverball)

^_^

*edit* oops sorry i just saw that you were trying to compile 1.5.1  >.<  I guess I should be sure to read the whole post in the future. lol
Anyways, did you check that your dependencies for the build were up to date?  Some compile error output would probably be helpful in diagnosing the problem as well..

Dependencies are up-to-date according to the vague info from the INSTALL file.  I'm not sure how to direct all the output from the make to a file.  There is only one error and I can't find it.

---

### Post by Grishka on 2009-04-10
to write your terminal output to a text file, use ">&". for example "make >& make.log" will create a make.log file in the install dir. but don't post all of it here. tell us what ./configure says, and post a few last lines of make log.

EDIT: I should have checked beforehand, there's no configure script. just tried compiling, and it runs fine, so you're probably missing some libraries. check the INSTALL file, and search for necessary packages in synaptic. libsdl1.2-dev is certainly needed. installing other sdl development libraries won't hurt, either.

---

### Post by jdunn on 2009-04-10
> **Grishka said:**
> to write your terminal output to a text file, use ">&". for example "make >& make.log" will create a make.log file in the install dir. but don't post all of it here. tell us what ./configure says, and post a few last lines of make log.

EDIT: I should have checked beforehand, there's no configure script. just tried compiling, and it runs fine, so you're probably missing some libraries. check the INSTALL file, and search for necessary packages in synaptic. libsdl1.2-dev is certainly needed. installing other sdl development libraries won't hurt, either.

sudo make >& make.log
bash: make.log: Permission denied

I already checked the dependencies in the INSTALL file.  I have libsdl1.2-dev, libsdl-ttf2.0-dev, libvorbis-dev, libpng12-dev, libjpeg62-dev which are the dependencies the INSTALL file asks for.  I had no trouble installing 1.5.0 a few weeks ago.

**edit**

ran make as user and got this from the make.log file:
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive

make: *** [neverball] Error 1

---

### Post by Grishka on 2009-04-10
> **jdunn said:**
> sudo make >& make.log
bash: make.log: Permission denied

I already checked the dependencies in the INSTALL file.  I have libsdl1.2-dev, libsdl-ttf2.0-dev, libvorbis-dev, libpng12-dev, libjpeg62-dev which are the dependencies the INSTALL file asks for.  I had no trouble installing 1.5.0 a few weeks ago.

**edit**

ran make as user and got this from the make.log file:
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive

make: *** [neverball] Error 1

you should never make as root. unpack the original source into a new directory, and try again. just make. also, post a few extra lines of make log, or attach the whole thing.

---

### Post by jdunn on 2009-04-10
> **Grishka said:**
> you should never make as root. unpack the original source into a new directory, and try again. just make. also, post a few extra lines of make log, or attach the whole thing.


```
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/lang.d -MT "share/lang.o" share/lang.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/lang.o -c share/lang.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/lang.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/lang.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/st_resol.d -MT "share/st_resol.o" share/st_resol.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/st_resol.o -c share/st_resol.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/geom.h:6,
                 from share/st_resol.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/geom.h:6,
                 from share/st_resol.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from share/st_resol.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/vec3.d -MT "share/vec3.o" share/vec3.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/vec3.o -c share/vec3.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/base_image.d -MT "share/base_image.o" share/base_image.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/base_image.o -c share/base_image.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/base_image.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/base_image.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/image.d -MT "share/image.o" share/image.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/image.o -c share/image.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/image.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/solid.d -MT "share/solid.o" share/solid.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/solid.o -c share/solid.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/solid.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/solid.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
share/solid.c: In function &#8216;sol_load_mtrl&#8217;:
share/solid.c:37: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
share/solid.c: In function &#8216;sol_load_file&#8217;:
share/solid.c:268: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
share/solid.c: In function &#8216;sol_load_head&#8217;:
share/solid.c:332: warning: ignoring return value of &#8216;fread&#8217;, declared with attribute warn_unused_result
share/solid.c: In function &#8216;sol_stor_mtrl&#8217;:
share/solid.c:385: warning: ignoring return value of &#8216;fwrite&#8217;, declared with attribute warn_unused_result
share/solid.c: In function &#8216;sol_stor_file&#8217;:
share/solid.c:559: warning: ignoring return value of &#8216;fwrite&#8217;, declared with attribute warn_unused_result
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/solid_gl.d -MT "share/solid_gl.o" share/solid_gl.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/solid_gl.o -c share/solid_gl.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/solid_gl.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from share/solid_gl.c:25:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/solid_phys.d -MT "share/solid_phys.o" share/solid_phys.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/solid_phys.o -c share/solid_phys.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/geom.h:6,
                 from share/solid_phys.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/geom.h:6,
                 from share/solid_phys.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/part.d -MT "share/part.o" share/part.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/part.o -c share/part.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/part.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from share/part.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/back.d -MT "share/back.o" share/back.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/back.o -c share/back.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/back.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from share/back.c:22:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/geom.d -MT "share/geom.o" share/geom.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/geom.o -c share/geom.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/geom.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from share/geom.c:25:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/item.d -MT "share/item.o" share/item.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/item.o -c share/item.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/item.h:18,
                 from share/item.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/item.h:18,
                 from share/item.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/image.h:4,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from share/item.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/ball.d -MT "share/ball.o" share/ball.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/ball.o -c share/ball.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from share/ball.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/gui.d -MT "share/gui.o" share/gui.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/gui.o -c share/gui.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from share/gui.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from share/gui.c:22:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/base_config.d -MT "share/base_config.o" share/base_config.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/base_config.o -c share/base_config.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/base_config.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/base_config.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/config.d -MT "share/config.o" share/config.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/config.o -c share/config.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/video.d -MT "share/video.o" share/video.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/video.o -c share/video.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from share/video.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/binary.d -MT "share/binary.o" share/binary.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/binary.o -c share/binary.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/binary.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/binary.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/state.d -MT "share/state.o" share/state.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/state.o -c share/state.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from share/state.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/audio.d -MT "share/audio.o" share/audio.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/audio.o -c share/audio.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/audio.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/text.d -MT "share/text.o" share/text.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/text.o -c share/text.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/text.h:4,
                 from share/text.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/sync.d -MT "share/sync.o" share/sync.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/sync.o -c share/sync.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/tilt.d -MT "share/tilt.o" share/tilt.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/tilt.o -c share/tilt.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/tilt.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/common.d -MT "share/common.o" share/common.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/common.o -c share/common.c
share/common.c: In function &#8216;file_copy&#8217;:
share/common.c:173: warning: ignoring return value of &#8216;fwrite&#8217;, declared with attribute warn_unused_result
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/keynames.d -MT "share/keynames.o" share/keynames.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/keynames.o -c share/keynames.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_keyboard.h:28,
                 from share/keynames.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_keyboard.h:29,
                 from share/keynames.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from share/keynames.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/syswm.d -MT "share/syswm.o" share/syswm.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/syswm.o -c share/syswm.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_video.h:28,
                 from share/syswm.c:4:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_video.h:29,
                 from share/syswm.c:4:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_video.h:30,
                 from share/syswm.c:4:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from share/syswm.c:4:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL_syswm.h:30,
                 from share/syswm.c:5:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_syswm.h:32,
                 from share/syswm.c:5:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/syswm.c:8:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/image.h:4,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from share/syswm.c:9:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/list.d -MT "share/list.o" share/list.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/list.o -c share/list.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/queue.d -MT "share/queue.o" share/queue.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/queue.o -c share/queue.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF share/cmd.d -MT "share/cmd.o" share/cmd.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o share/cmd.o -c share/cmd.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/cmd.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/cmd.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/hud.d -MT "ball/hud.o" ball/hud.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/hud.o -c ball/hud.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from ball/hud.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/game_common.d -MT "ball/game_common.o" ball/game_common.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/game_common.o -c ball/game_common.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/game_client.d -MT "ball/game_client.o" ball/game_client.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/game_client.o -c ball/game_client.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from ball/game_client.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from ball/game_client.c:26:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/game_server.d -MT "ball/game_server.o" ball/game_server.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/game_server.o -c ball/game_server.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from ball/game_server.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/game_proxy.d -MT "ball/game_proxy.o" ball/game_proxy.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/game_proxy.o -c ball/game_proxy.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/score.d -MT "ball/score.o" ball/score.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/score.o -c ball/score.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/score.h:4,
                 from ball/score.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/score.h:4,
                 from ball/score.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/level.d -MT "ball/level.o" ball/level.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/level.o -c ball/level.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from ball/level.c:22:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from ball/level.c:22:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/level.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/progress.d -MT "ball/progress.o" ball/progress.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/progress.o -c ball/progress.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/progress.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/set.d -MT "ball/set.o" ball/set.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/set.o -c ball/set.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/set.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from ball/set.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/demo.d -MT "ball/demo.o" ball/demo.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/demo.o -c ball/demo.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/level.h:4,
                 from ball/demo.h:7,
                 from ball/demo.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/level.h:4,
                 from ball/demo.h:7,
                 from ball/demo.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/util.d -MT "ball/util.o" ball/util.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/util.o -c ball/util.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/util.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/util.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/util.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_conf.d -MT "ball/st_conf.o" ball/st_conf.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_conf.o -c ball/st_conf.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/geom.h:6,
                 from ball/st_conf.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from share/solid.h:19,
                 from share/geom.h:6,
                 from ball/st_conf.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_conf.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_demo.d -MT "ball/st_demo.o" ball/st_demo.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_demo.o -c ball/st_demo.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_demo.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_demo.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_demo.c:24:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_save.d -MT "ball/st_save.o" ball/st_save.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_save.o -c ball/st_save.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_save.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_save.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_save.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_goal.d -MT "ball/st_goal.o" ball/st_goal.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_goal.o -c ball/st_goal.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_goal.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_goal.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_goal.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_fall_out.d -MT "ball/st_fall_out.o" ball/st_fall_out.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_fall_out.o -c ball/st_fall_out.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_fall_out.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_fall_out.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_fall_out.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_time_out.d -MT "ball/st_time_out.o" ball/st_time_out.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_time_out.o -c ball/st_time_out.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_time_out.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_time_out.c:15:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_time_out.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_done.d -MT "ball/st_done.o" ball/st_done.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_done.o -c ball/st_done.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_done.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_done.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_done.c:23:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_level.d -MT "ball/st_level.o" ball/st_level.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_level.o -c ball/st_level.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_level.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_level.c:18:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_level.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_over.d -MT "ball/st_over.o" ball/st_over.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_over.o -c ball/st_over.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_over.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_over.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_over.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_play.d -MT "ball/st_play.o" ball/st_play.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_play.o -c ball/st_play.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/level.h:4,
                 from ball/demo.h:7,
                 from ball/st_play.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/level.h:4,
                 from ball/demo.h:7,
                 from ball/st_play.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_play.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_set.d -MT "ball/st_set.o" ball/st_set.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_set.o -c ball/st_set.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_set.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_set.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_set.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_start.d -MT "ball/st_start.o" ball/st_start.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_start.o -c ball/st_start.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_start.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/st_start.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_start.c:20:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_title.d -MT "ball/st_title.o" ball/st_title.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_title.o -c ball/st_title.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/level.h:4,
                 from ball/demo.h:7,
                 from ball/st_title.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/level.h:4,
                 from ball/demo.h:7,
                 from ball/st_title.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_title.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_help.d -MT "ball/st_help.o" ball/st_help.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_help.o -c ball/st_help.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_help.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_name.d -MT "ball/st_name.o" ball/st_name.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_name.o -c ball/st_name.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_endian.h:28,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_name.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from share/base_config.h:24,
                 from ball/set.h:4,
                 from ball/util.h:4,
                 from ball/st_name.c:19:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_name.c:21:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_shared.d -MT "ball/st_shared.o" ball/st_shared.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_shared.o -c ball/st_shared.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_shared.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/st_pause.d -MT "ball/st_pause.o" ball/st_pause.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/st_pause.o -c ball/st_pause.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from share/config.h:26,
                 from ball/st_pause.c:16:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -MM -MP -MF ball/main.d -MT "ball/main.o" ball/main.c
cc -Wall -ansi -pedantic  -O2 -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -U_GNU_SOURCE -I/usr/include/libpng12 -Ishare -DVERSION=\"1.5.1\" -DENABLE_NLS=1 -DNDEBUG -o ball/main.o -c ball/main.c
In file included from /usr/include/SDL/SDL_stdinc.h:137,
                 from /usr/include/SDL/SDL_main.h:26,
                 from /usr/include/SDL/SDL.h:28,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_error.h:30,
                 from /usr/include/SDL/SDL_audio.h:29,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_endian.h:47,
                 from /usr/include/SDL/SDL_audio.h:30,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mutex.h:34,
                 from /usr/include/SDL/SDL_audio.h:31,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_thread.h:37,
                 from /usr/include/SDL/SDL_audio.h:32,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_rwops.h:33,
                 from /usr/include/SDL/SDL_audio.h:33,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_audio.h:35,
                 from /usr/include/SDL/SDL.h:30,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cdrom.h:31,
                 from /usr/include/SDL/SDL.h:31,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_cpuinfo.h:31,
                 from /usr/include/SDL/SDL.h:32,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_active.h:31,
                 from /usr/include/SDL/SDL_events.h:30,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_keyboard.h:32,
                 from /usr/include/SDL/SDL_events.h:31,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_video.h:32,
                 from /usr/include/SDL/SDL_mouse.h:30,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_mouse.h:32,
                 from /usr/include/SDL/SDL_events.h:32,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_joystick.h:31,
                 from /usr/include/SDL/SDL_events.h:33,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_events.h:36,
                 from /usr/include/SDL/SDL.h:35,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_loadso.h:47,
                 from /usr/include/SDL/SDL.h:36,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_timer.h:31,
                 from /usr/include/SDL/SDL.h:40,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_version.h:30,
                 from /usr/include/SDL/SDL.h:42,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL.h:44,
                 from ball/main.c:17:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
In file included from /usr/include/SDL/SDL_ttf.h:34,
                 from share/image.h:5,
                 from ball/main.c:25:
/usr/include/SDL/begin_code.h:94:8: warning: extra tokens at end of #endif directive
cc -Wall -ansi -pedantic  -O2 -o neverball share/lang.o share/st_resol.o share/vec3.o share/base_image.o share/image.o share/solid.o share/solid_gl.o share/solid_phys.o share/part.o share/back.o share/geom.o share/item.o share/ball.o share/gui.o share/base_config.o share/config.o share/video.o share/binary.o share/state.o share/audio.o share/text.o share/sync.o share/tilt.o share/common.o share/keynames.o share/syswm.o share/list.o share/queue.o share/cmd.o ball/hud.o ball/game_common.o ball/game_client.o ball/game_server.o ball/game_proxy.o ball/score.o ball/level.o ball/progress.o ball/set.o ball/demo.o ball/util.o ball/st_conf.o ball/st_demo.o ball/st_save.o ball/st_goal.o ball/st_fall_out.o ball/st_time_out.o ball/st_done.o ball/st_level.o ball/st_over.o ball/st_play.o ball/st_set.o ball/st_start.o ball/st_title.o ball/st_help.o ball/st_name.o ball/st_shared.o ball/st_pause.o ball/main.o  -L/usr/lib -lSDL -ljpeg -lpng12   -lSDL_ttf -lvorbisfile -lGL -lm
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [neverball] Error 1
```

---

### Post by jdunn on 2009-04-10
make.log.gz

---

### Post by Grishka on 2009-04-10
man, the common procedure is "make", then "sudo make install". but neverball won't make install anyway. you'll have to manually put the compiled binary in /usr/local/bin, or wherever. anyway, your error has something to do with missing opengl libraries. try these libs: [apt://libgl1-mesa-dev]("apt://libgl1-mesa-dev"), [apt://libglitz1-dev]("apt://libglitz1-dev"), [apt://libglitz-glx1-dev]("apt://libglitz-glx1-dev") and [apt://libglu1-mesa-dev]("apt://libglu1-mesa-dev")

---

### Post by jdunn on 2009-04-10
> **Grishka said:**
> man, the common procedure is "make", then "sudo make install". but neverball won't make install anyway. you'll have to manually put the compiled binary in /usr/local/bin, or wherever. anyway, your error has something to do with missing opengl libraries. try these libs: [apt://libgl1-mesa-dev]("apt://libgl1-mesa-dev"), [apt://libglitz1-dev]("apt://libglitz1-dev"), [apt://libglitz-glx1-dev]("apt://libglitz-glx1-dev") and [apt://libglu1-mesa-dev]("apt://libglu1-mesa-dev")



I haven't removed any packages so, I can't understand why 1.5.0 compiled perfectly and 1.5.1 will not.

I was missing from your suggestions libglitz-dev and libglitz-glx1-dev.  I added them and recompiled with the same error.

---

### Post by Grishka on 2009-04-10
> **jdunn said:**
> I haven't removed any packages so, I can't understand why 1.5.0 compiled perfectly and 1.5.1 will not.

I was missing from your suggestions libglitz-dev and libglitz-glx1-dev.  I added them and recompiled with the same error.

you need libGL.so, do you have it on your system? also, what graphics card are you using?
I just checked, libGL is provided by two packages. libgl1-mesa-dev and nvidia-glx-xxx-dev. if you find some libGL.so.1 or something like that, try making a symlink to it, and call it libGL.so. unless you already have libGL.so in your libraries directory. in which case, idk. it may be broken, or maybe neverball makefile is looking for a different version.

---

### Post by jdunn on 2009-04-10
solution:
Someone from the neverball forum suggested I create a symbolic link for libGL.so to libGL.so.1.  It worked.  Although, I still got 1 or 2 errors in the compile, It fully compiled successfully and runs with music et al.

*Edit*
same as your latest suggestion, I see.  Thanks.
To answer your question, I'm using a GeForce 9200M GS...so lshw says.

---

