---
title: "Can't compile dgen-sdl-1.33 - SDL version &gt;= 1.2.0 not found"
date: 2015-07-12
forum: Gaming &amp; Leisure
---

### Post by Ashfaqur Rahman on 2015-07-12
I am trying to compile [dgen-sdl-1.33]("http://sourceforge.net/projects/dgen/files/dgen/1.33/") on Ubuntu 14.04. But its giving "SDL version >= 1.2.0 not found" error after running ./configure.

I have compiled and installed SDL2-2.0.3 [following this]("http://askubuntu.com/questions/344512/what-is-the-general-procedure-to-install-development-libraries-in-ubuntu"). Still its giving the same error!

Output of $ dpkg -l | grep sdl

```

ii  libsdl-image1.2:amd64                                       1.2.12-5build2                                      amd64        Image loading library for Simple DirectMedia Layer 1.2, libraries
ii  libsdl-mixer1.2:amd64                                       1.2.12-10                                           amd64        Mixer library for Simple DirectMedia Layer 1.2, libraries
ii  libsdl-pango1:amd64                                         0.1.2-6                                             amd64        text rendering with Pango in SDL applications (shared library)
ii  libsdl-ttf2.0-0:amd64                                       2.0.11-3                                            amd64        TrueType Font library for Simple DirectMedia Layer 1.2, libraries
ii  libsdl1.2debian:amd64                                       1.2.15-8ubuntu1.1                                   amd64        Simple DirectMedia Layer
ii  libsdl1.2debian:i386                                        1.2.15-8ubuntu1.1                                   i386         Simple DirectMedia Layer
ii  libsdl2-2.0-0:amd64                                         2.0.2+dfsg1-3ubuntu1.1                              amd64        Simple DirectMedia Layer
ii  libsdl2-dev                                                 2.0.2+dfsg1-3ubuntu1.1                              amd64        Simple DirectMedia Layer development files

```

What is the problem?

Thanks!

---

### Post by MikeCyber on 2015-07-12
If you've compiled yourself sdl chances are high that they're not found because the headers are somewhere else. Like /usr/includes/sdl to /include/sdl or so.
Change the configure script or install sdl with synaptic:
[http://packages.ubuntu.com/search?keywords=sdl2](http://packages.ubuntu.com/search?keywords=sdl2)

---

### Post by Ashfaqur Rahman on 2015-07-12
I think downloading those packages through package manager won't work. As ***$ sudo apt-get --simulate install libsdl2-2.0-0 libsdl2-dev ***shows:

```

libsdl2-2.0-0 is already the newest version.
libsdl2-dev is already the newest version.

```

To make sure I have purged *libsdl2-2.0-0 *which purged *libsdl2-dev *too. And re-install *libsdl2-2.0-0 & [I]libsdl2-dev*[/I]. Still showing same problem.

I think I have to find the include path for sdl2 & pass it manually in the configure script. ***$ ls /usr/include | grep sdl2 ***&*** [I][B]$ ls /usr/local/include | grep sdl2 ***[/B][/I]shows nothing. I have no include directory in my root. where it can go? or How can I find?

After finding include path how can I specify it in the configure script? I have read the README file. It didn't specify any configure variable for SDL path.

Thanks

---

### Post by steeldriver on 2015-07-12
Are you sure it needs SDL[COLOR=#ff0000]**2**[/COLOR]? I just tried it on my 14.04 box and it seemed quite happy with the (installed) version of libsdl[COLOR=#ff0000]**1.2**[/COLOR]-dev

```

$ apt-cache policy libsdl1.2-dev 
libsdl1.2-dev:
  Installed: 1.2.15-8ubuntu1.1
  Candidate: 1.2.15-8ubuntu1.1
  Version table:
 *** 1.2.15-8ubuntu1.1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1.2.15-8ubuntu1 0
        500 http://ca.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

SDL2 is a different API I think and may not satisfy the requirement

---

### Post by Ashfaqur Rahman on 2015-07-12
After reading README in dgen source I noticed it requires SDL >= 1.2 to compile. I checked in my system if SDL is already installed. Found 1.2 installed already. So I thought may be I need to install higher version. I looked up SDL's website & found 2.0. Installed *libsdl2-2.0-0 & [I]libsdl2-dev. *[/I]But it didn't work.

I just missed the point that I should have installed *libsdl1.2-dev* instead!!
Successfully compiled & installed.

Thanks!                                                                                      [**[COLOR=#DD4814][B]steeldriver**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1627500")

---

### Post by YpeKPbW on 2015-08-16
Sorry to bother you guys with this thread again, but I have the same problem here...

I already verified to have libsdl (dev version) installed.

```
$ dpkg -l | grep libsdl
ii  libsdl-image1.2:amd64                       1.2.12-5build2                          amd64        Image loading library for Simple DirectMedia Layer 1.2, libraries
ii  libsdl-ttf2.0-0:amd64                       2.0.11-3                                amd64        TrueType Font library for Simple DirectMedia Layer 1.2, libraries
ii  libsdl1.2debian:amd64                       1.2.15-8ubuntu1.1                       amd64        Simple DirectMedia Layer
ii  libsdl1.2debian:i386                        1.2.15-8ubuntu1.1                       i386         Simple DirectMedia Layer
ii  libsdl2-2.0-0:amd64                         2.0.2+dfsg1-3ubuntu1.1                  amd64        Simple DirectMedia Layer

```

This is the output when I try to configure:
```
$ sh ./configure && make && make install
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether make supports nested variables... yes
checking whether make supports nested variables... (cached) yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc option to accept ISO C99... -std=gnu99
checking how to run the C preprocessor... gcc -std=gnu99 -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking whether ln -s works... yes
checking for ranlib... ranlib
checking whether make sets $(MAKE)... (cached) yes
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
checking for sdl-config... no
checking for SDL - version >= 1.2.0... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
configure: error: SDL version >= 1.2.0 not found.

```

What I understand is that sdl-config is missing and so the path to libsdl cannot be acquired; how should I specify the path manually?


Thank you!

---

### Post by steeldriver on 2015-08-16
> **YpeKPbW said:**
> 
I already verified to have libsdl (dev version) installed.

 
How do you figure that? if the dev package is installed, you should see a line like

```
$ dpkg -l | grep libsdl
**ii  libsdl1.2[COLOR=#0000ff]-dev[/COLOR]                                         1.2.15-8ubuntu1.1                                   amd64        Simple DirectMedia Layer[COLOR=#0000ff] development files[/COLOR]**
ii  libsdl1.2debian:amd64                                 1.2.15-8ubuntu1.1                                   amd64        Simple DirectMedia Layer
ii  libsdl2-2.0-0:amd64                                   2.0.2+dfsg1-3ubuntu1.1                              amd64        Simple DirectMedia Layer
ii  libsdl2-dev                                           2.0.2+dfsg1-3ubuntu1.1                              amd64        Simple DirectMedia Layer development files

```

---

### Post by YpeKPbW on 2015-08-16
> **steeldriver said:**
> How do you figure that? if the dev package is installed, you should see a line like

```
$ dpkg -l | grep libsdl
**ii  libsdl1.2[COLOR=#0000ff]-dev[/COLOR]                                         1.2.15-8ubuntu1.1                                   amd64        Simple DirectMedia Layer[COLOR=#0000ff] development files[/COLOR]**
ii  libsdl1.2debian:amd64                                 1.2.15-8ubuntu1.1                                   amd64        Simple DirectMedia Layer
ii  libsdl2-2.0-0:amd64                                   2.0.2+dfsg1-3ubuntu1.1                              amd64        Simple DirectMedia Layer
ii  libsdl2-dev                                           2.0.2+dfsg1-3ubuntu1.1                              amd64        Simple DirectMedia Layer development files

```

SuperFACEPALM!!#-o

I was confused by autocomplete suggestion when apt-get install this... (I was convinced the one proposed were the one installed!!)

However simply installing libsdl2-dev DOESN'T work; I need to install libsdl1.2-dev...have you any idea of why? (shouldn't be better to use the newer version?)

Thank you so much

p.s: the so installed dgen is in /usr/local/bin; there is a way to make it the "default" one instead of the repository-installed one? (so I could launch it simply typing dgen in the command line)

---

### Post by steeldriver on 2015-08-16
As I already mentioned in post #4, libsdl2 is not simply a "newer, better" version - it provides a different API that is not compatible with libsdl1 so you cannot substitute libsdl2-dev if a package requires libsdl1.2-dev

Your shell's PATH should contain /usr/local/bin ahead of /usr/bin, so /usr/local/bin/dgen should be executed in preference to anything installed from the repository - you can check with

```

echo $PATH

which dgen

```

Hope this helps

---

### Post by YpeKPbW on 2015-08-16
thanks!

---

