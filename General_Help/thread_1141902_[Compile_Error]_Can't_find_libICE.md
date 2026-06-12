---
title: "[Compile Error] Can't find libICE"
date: 2009-04-28
forum: General Help
---

### Post by arnydo on 2009-04-28
Im pretty new to Ubuntu and so far I am very happy with it. However, im still trying to get the hang of manually installing programs. While trying to install "recordmydesktop-0.3.8.1" i can not successfully compile the program. It says it "Can't find libICE"

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
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
checking whether gcc and cc understand -c and -o together... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking how to run the C preprocessor... gcc -E
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
checking whether byte ordering is bigendian... no
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking for ANSI C header files... (cached) yes
checking for X... no
checking alsa/asoundlib.h usability... no
checking alsa/asoundlib.h presence... no
checking for alsa/asoundlib.h... no
checking endian.h usability... yes
checking endian.h presence... yes
checking for endian.h... yes
checking sys/soundcard.h usability... yes
checking sys/soundcard.h presence... yes
checking for sys/soundcard.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking for unistd.h... (cached) yes
checking vorbis/vorbisfile.h usability... no
checking vorbis/vorbisfile.h presence... no
checking for vorbis/vorbisfile.h... no
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking for u_int16_t... yes
checking for u_int32_t... yes
checking for u_int64_t... yes
checking for isnan in -lm... yes
checking for deflate in -lz... yes
checking for IceOpenConnection in -lICE... no
configure: error: [COLOR=Red]Can't find libICE[/COLOR]

---

### Post by taurus on 2009-04-28
You probably need to install the libice6 & libice-dev packages first.

---

### Post by arnydo on 2009-04-28
Thank you so much for your help. Now that i realize how easy that was, and that it was pretty much common since, that was easier than i thought. After i installed what you recommended i had to install around 6-7 more lib's, and it configured fine. Thanks again for your help.

---

