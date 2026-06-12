---
title: "Marathon Aleph One"
date: 2015-04-24
forum: Gaming &amp; Leisure
---

### Post by tyler69 on 2015-04-24
Hey guys so I'm pretty new to Ubuntu, but I've figured out the gist of things in terms of needing to manually install what you need, to do what you want. But I still don't really know what I'm doing besides typing code that I find to do something..

So as the title suggests, I am trying to install the Marathon Trilogy on my computer, using Aleph One. So far from reading the README that came with the aleph one download ([http://marathon.sourceforge.net/games/marathon.php#download](http://marathon.sourceforge.net/games/marathon.php#download)) I can see I need to download SDL, I went to the website listed in the README and downloaded SDL2.0 which shows up later on my system as SDL2-2.0.3, and I was able to ./configure it and it seems to have installed/configured (I'm not sure) correctly as I did not get any error messages. 

Now the next step in the Readme is to get SDL_images and SDL_net, also linked to, and I was able to download both in 2.0.0 variants (SDL2_image-2.0.0). When I tried to ./configure these after downloading however, they both give me an error message telling me SDL2.0.0 could not be found. This may be where my problem lies, but I don't know so give me any help you can as you read this.

This is what I get for image
```
tyler@Stengah:~/SDL2-2.0.3$ cd SDL2_image-2.0.0
tyler@Stengah:~/SDL2-2.0.3/SDL2_image-2.0.0$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking whether make supports nested variables... yes
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for gcc... gcc
checking whether we are using the GNU Objective C compiler... no
checking whether gcc accepts -g... no
checking dependency style of gcc... gcc3
checking for inline... inline
checking whether make sets $(MAKE)... (cached) yes
checking for windres... no
checking for linux-gnu-windres... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SDL... no
checking for sdl2-config... no
checking for SDL - version >= 2.0.0... no
*** The sdl2-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL2_CONFIG environment variable to the
*** full path to sdl2-config.
configure: error: *** SDL version 2.0.0 not found!
tyler@Stengah:~/SDL2-2.0.3/SDL2_image-2.0.0$
```

And this is what I get for net
```
tyler@Stengah:~/SDL2-2.0.3/SDL2_image-2.0.0$ cd -
/home/tyler/SDL2-2.0.3
tyler@Stengah:~/SDL2-2.0.3$ cd SDL2_net-2.0.0
tyler@Stengah:~/SDL2-2.0.3/SDL2_net-2.0.0$ ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for fgrep... /bin/grep -F
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking for objdump... objdump
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking how to run the C preprocessor... gcc -E
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
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC -DPIC
checking if gcc PIC flag -fPIC -DPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking if gcc supports -c -o file.o... (cached) yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking whether make supports nested variables... yes
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC -DPIC
checking if g++ PIC flag -fPIC -DPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking if g++ supports -c -o file.o... (cached) yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking dependency style of g++... (cached) gcc3
checking whether make sets $(MAKE)... (cached) yes
checking for windres... no
checking for linux-gnu-windres... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SDL... no
checking for sdl2-config... no
checking for SDL - version >= 2.0.0... no
*** The sdl2-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL2_CONFIG environment variable to the
*** full path to sdl2-config.
configure: error: *** SDL version 2.0.0 not found!
tyler@Stengah:~/SDL2-2.0.3/SDL2_net-2.0.0$ 
```

So after this, I decided to press onward just to see if I could still get the game to install at least. In the next step of the README it says to configure AlephOne, so I went to the directory and typed ```
./configure && make && make install
```, Which it shows is supposed to install AlephOne and create a folder where I place the actual individual Marathon game files. But instead I get this error.

```
tyler@Stengah:~$ cd AlephOne-20140104
tyler@Stengah:~/AlephOne-20140104$ ./configure && make && make install
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/home/tyler/AlephOne-20140104/missing: Unknown `--is-lightweight' option
Try `/home/tyler/AlephOne-20140104/missing --help' for more information
configure: WARNING: 'missing' script is too old or missing
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
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
checking for sysconf... yes
checking for sysctlbyname... no
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking SDL_image.h usability... yes
checking SDL_image.h presence... yes
checking for SDL_image.h... yes
checking for IMG_Load in -lSDL_image... yes
checking SDL_ttf.h usability... yes
checking SDL_ttf.h presence... yes
checking for SDL_ttf.h... yes
checking for TTF_Init in -lSDL_ttf... yes
checking SDL_net.h usability... yes
checking SDL_net.h presence... yes
checking for SDL_net.h... yes
checking for SDLNet_Init in -lSDL_net... yes
checking for library containing gethostbyname... none required
checking for library containing socket... none required
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking for zlibVersion in -lz... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for ZZIP... yes
checking for PNG... yes
checking boost/bind.hpp usability... yes
checking boost/bind.hpp presence... yes
checking for boost/bind.hpp... yes
checking boost/function.hpp usability... yes
checking boost/function.hpp presence... yes
checking for boost/function.hpp... yes
checking smpeg/smpeg.h usability... no
checking smpeg/smpeg.h presence... no
checking for smpeg/smpeg.h... no
checking mad.h usability... no
checking mad.h presence... no
checking for mad.h... no
checking sndfile.h usability... no
checking sndfile.h presence... no
checking for sndfile.h... no
checking for VORBISFILE... yes
checking for FFMPEG... yes
checking speex/speex.h usability... yes
checking speex/speex.h presence... yes
checking for speex/speex.h... yes
checking for speex_decoder_init in -lspeex... yes
checking for speex_preprocess_state_init in -lspeexdsp... yes
checking alsa/asoundlib.h usability... yes
checking alsa/asoundlib.h presence... yes
checking for alsa/asoundlib.h... yes
checking for snd_pcm_open in -lasound... yes
checking for OpenGL support... yes
checking for gluScaleImage in -lGLU... yes
checking for GL/glext.h... yes
checking that generated files are newer than configure... done
configure: creating ./config.status
config.status: creating Makefile
config.status: creating AlephOne.spec
config.status: creating Source_Files/Makefile
config.status: creating Source_Files/CSeries/Makefile
config.status: creating Source_Files/Expat/Makefile
config.status: creating Source_Files/FFmpeg/Makefile
config.status: creating Source_Files/Files/Makefile
config.status: creating Source_Files/GameWorld/Makefile
config.status: creating Source_Files/Input/Makefile
config.status: creating Source_Files/LibNAT/Makefile
config.status: creating Source_Files/Lua/Makefile
config.status: creating Source_Files/Misc/Makefile
config.status: creating Source_Files/ModelView/Makefile
config.status: creating Source_Files/Network/Makefile
config.status: creating Source_Files/Network/Metaserver/Makefile
config.status: creating Source_Files/RenderMain/Makefile
config.status: creating Source_Files/RenderOther/Makefile
config.status: creating Source_Files/Sound/Makefile
config.status: creating Source_Files/TCPMess/Makefile
config.status: creating Source_Files/XML/Makefile
config.status: creating tools/Makefile
config.status: creating data/Makefile
config.status: creating data/default_theme/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
Configuration done. Now type "make".
make  all-recursive
make[1]: Entering directory `/home/tyler/AlephOne-20140104'
Making all in Source_Files
make[2]: Entering directory `/home/tyler/AlephOne-20140104/Source_Files'
make[3]: Entering directory `/home/tyler/AlephOne-20140104'
make[3]: Leaving directory `/home/tyler/AlephOne-20140104'
Making all in CSeries
make[3]: Entering directory `/home/tyler/AlephOne-20140104/Source_Files/CSeries'
make[4]: Entering directory `/home/tyler/AlephOne-20140104'
make[4]: Leaving directory `/home/tyler/AlephOne-20140104'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/tyler/AlephOne-20140104/Source_Files/CSeries'
Making all in Expat
make[3]: Entering directory `/home/tyler/AlephOne-20140104/Source_Files/Expat'
make[4]: Entering directory `/home/tyler/AlephOne-20140104'
make[4]: Leaving directory `/home/tyler/AlephOne-20140104'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/tyler/AlephOne-20140104/Source_Files/Expat'
Making all in Files
make[3]: Entering directory `/home/tyler/AlephOne-20140104/Source_Files/Files'
make[4]: Entering directory `/home/tyler/AlephOne-20140104'
make[4]: Leaving directory `/home/tyler/AlephOne-20140104'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/tyler/AlephOne-20140104/Source_Files/Files'
Making all in FFmpeg
make[3]: Entering directory `/home/tyler/AlephOne-20140104/Source_Files/FFmpeg'
make[4]: Entering directory `/home/tyler/AlephOne-20140104'
make[4]: Leaving directory `/home/tyler/AlephOne-20140104'
g++ -DHAVE_CONFIG_H -I. -I../.. -I../../Source_Files/CSeries -I../../Source_Files/Files -I../../Source_Files/GameWorld -I../../Source_Files/Input -I../../Source_Files/Misc -I../../Source_Files/ModelView -I../../Source_Files/Network -I../../Source_Files/Sound -I../../Source_Files/RenderMain -I../../Source_Files/RenderOther -I../../Source_Files/XML -I../../Source_Files -D__STDC_CONSTANT_MACROS -I/usr/include/libpng12   -D_FORTIFY_SOURCE=2    -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DSDL  -g -O2 -MT Movie.o -MD -MP -MF .deps/Movie.Tpo -c -o Movie.o Movie.cpp
Movie.cpp: In member function ‘bool Movie::Setup()’:
Movie.cpp:494:61: error: ‘AVStream’ has no member named ‘quality’
         audio_stream->codec->global_quality = audio_stream->quality = FF_QP2LAMBDA * (aq / 10);
                                                             ^
Movie.cpp: In member function ‘void Movie::EncodeVideo(bool)’:
Movie.cpp:618:21: warning: ‘int avcodec_encode_video(AVCodecContext*, uint8_t*, int, const AVFrame*)’ is deprecated (declared at /usr/include/libavcodec/avcodec.h:4030) [-Wdeprecated-declarations]
         int vsize = avcodec_encode_video(vcodec,
                     ^
Movie.cpp:620:47: warning: ‘int avcodec_encode_video(AVCodecContext*, uint8_t*, int, const AVFrame*)’ is deprecated (declared at /usr/include/libavcodec/avcodec.h:4030) [-Wdeprecated-declarations]
                                          frame);
                                               ^
make[3]: *** [Movie.o] Error 1
make[3]: Leaving directory `/home/tyler/AlephOne-20140104/Source_Files/FFmpeg'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tyler/AlephOne-20140104/Source_Files'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tyler/AlephOne-20140104'
make: *** [all] Error 2
tyler@Stengah:~/AlephOne-20140104$
```

One source I googled about this, said that even with these errors it should still have worked, but I checked the directory it is supposed to be installed to (/usr/local/shared/AlephOne) And AlephOne is not there. 

Any help you guys could give me on what's going wrong would be greatly appreciated, and thank you very much for taking the time to read this!

---

### Post by than4 on 2015-07-30
[SIZE=2]Try googling "compiling aleph one". The sourceforge page offers a guide for compiling the program. 

[http://sourceforge.net/p/marathon/wiki/Linux%20Install%20Instructions/](http://sourceforge.net/p/marathon/wiki/Linux%20Install%20Instructions/)

I just finished compiling, although I completed each step separately. It looks like you don't have all the dependencies, and if you were to execute ./configure by itself, you might be able to see the error more clearly.

Try installing all the required dependencies first:

[I]sudo apt-get install libboost-all-dev libsdl1.2-dev libsdl-image1.2-dev \
  libsdl-net1.2-dev libsdl-ttf2.0-dev libspeexdsp-dev libzzip-dev \
  libavcodec-dev libavformat-dev libavutil-dev libswscale-de[/I]v

Afterwards, proceed with [COLOR=#000000][FONT=Ubuntu Mono]*./configure && make && make install *
[/FONT][/COLOR][/SIZE]
Since I followed the guide myself, I don't know if this will actually work, but you can try.

---

