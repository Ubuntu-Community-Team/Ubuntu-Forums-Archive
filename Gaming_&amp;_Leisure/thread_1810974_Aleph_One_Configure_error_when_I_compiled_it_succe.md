---
title: "Aleph One Configure error when I compiled it successfully before"
date: 2011-07-24
forum: Gaming &amp; Leisure
---

### Post by iamanidiot123 on 2011-07-24
Hi, i'm trying to compile alephone.
I compiled it before, i'm just updating to a new beta package.
I run a ./configure command, but here's what I get:

```
daniel@daniel-desktop:~/AlephOne-20110717$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ranlib... ranlib
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
checking for unistd.h... (cached) yes
checking pwd.h usability... yes
checking pwd.h presence... yes
checking for pwd.h... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for mkstemp... yes
checking for sdl-config... /usr/local/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking SDL_image.h usability... no
checking SDL_image.h presence... no
checking for SDL_image.h... no
checking SDL_ttf.h usability... no
checking SDL_ttf.h presence... no
checking for SDL_ttf.h... no
checking SDL_net.h usability... no
checking SDL_net.h presence... no
checking for SDL_net.h... no
configure: error: You need SDL_net to run Aleph One.
daniel@daniel-desktop:~/AlephOne-20110717$ 

```

I do have SDL headers in /usr/include/SDL:

```
daniel@daniel-desktop:~/AlephOne-20110717$ ls /usr/include/SDL
begin_code.h     SDL_cdrom.h    SDL_events.h    SDL_keyboard.h  SDL_mutex.h     SDL_quit.h    SDL_timer.h
close_code.h     SDL_config.h   SDL_getenv.h    SDL_keysym.h    SDL_name.h      SDL_rwops.h   SDL_ttf.h
SDL_active.h     SDL_cpuinfo.h  SDL.h           SDL_loadso.h    SDL_net.h       SDL_stdinc.h  SDL_types.h
SDL_audio.h      SDL_endian.h   SDL_image.h     SDL_main.h      SDL_opengl.h    SDL_syswm.h   SDL_version.h
SDL_byteorder.h  SDL_error.h    SDL_joystick.h  SDL_mouse.h     SDL_platform.h  SDL_thread.h  SDL_video.h
daniel@daniel-desktop:~/AlephOne-20110717$ 

```

And after trying to compile a previous version which I compiled successfully already, it just came up with the same configure error.  
What's going on?  I installed all the prerequisites, by the way.
I'm running kubuntu. And the application itself still works fine.  Or do I have to have libraries in /usr/local/lib?

---

