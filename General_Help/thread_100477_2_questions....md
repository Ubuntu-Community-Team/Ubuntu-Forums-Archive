---
title: "2 questions..."
date: 2005-12-07
forum: General Help
---

### Post by korkow on 2005-12-07
My first is... how the heck do you get kaffeine (or any player for that matter) to play wmv's?  I have all the codecs in /usr/lib/win32, but I just wont work!

Second question... I know the answer to this is probably really obvious but I can't figure it out. For some reason, I can't install ANYTHING with the traditional "/.configure make make install". when I do ./configure I get this is the output:

>checking build system type... i686-pc-linux-gnulibc1
>checking host system type... i686-pc-linux-gnulibc1
>checking target system type... i686-pc-linux-gnulibc1
>checking for a BSD-compatible install... /usr/bin/install -c
>checking whether build environment is sane... yes
>checking for gawk... gawk
>checking whether make sets $(MAKE)... no
>checking for style of include used by make... none
>checking for gcc... gcc
>checking for C compiler default output file name... configure: error: C compiler             >cannot create executables
>See `config.log' for more details.

Then when I type "make", it just tells me make isn't a command.

Any help?

---

### Post by aysiu on 2005-12-07
Read the second link in my sig.

---

### Post by linbetwin on 2005-12-07
You have to install multimedia codecs and **build-essential** (for building packages from source). Anyway what are you trying to install?

---

### Post by korkow on 2005-12-07
Okay... I can install stuff now, but I still can't get any media player to play quicktime or wmv or anything. I have the latest xine libs (1.1.1), and I have all codecs in both /usr/lib/win32 (for kaffeine) and /usr/local/libs/codecs (for mplayer). For some reason, I can get sound on mplayer, but no video. Which is kind of pointless.

---

