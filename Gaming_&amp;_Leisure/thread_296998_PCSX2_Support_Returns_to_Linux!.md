---
title: "PCSX2 Support Returns to Linux!"
date: 2006-11-10
forum: Gaming &amp; Leisure
---

### Post by cleverselfreferentialname on 2006-11-10
A lot of perhaps unintentional FUD has been floating around about the apparent ungoodness of Linux PS2 emulators.

Those who have an interest in the emulation scene might have heard when Linux support was discontinued for the PCSX2 emulator some time ago.

Well, now: it's back. And it works a LOT better now too. At least on the unscrupulous platforms. I haven't gotten it working on *nix yet.

> the upcoming 0.9.2 release is looking very stable and after doing some research, we have decided to add support for x86-64 recompilation, both for 64bit versions of Linux and Windows (yes, Linux support is returning).

[Source here.]("http://www.pcsx2.net/files/4718")

I think you need automake2.13 also, which is in the repos under that name.

Now, I haven't *exactly* gotten it to work, *air quotes on work* but I'm sure one of my Ubuntero/a brothers and sisters can figure that out.

---

### Post by po0f on 2006-11-10
cleverselfreferentialname,

What problems were you having with it?  Building, running, compatibility with certain games?  I can't test it right now, all I have are PSX games (unless I can play PSX games on a PS2 emulator?), but I just got paid today so I might have to get a couple of games.  Actually, just one game, FFX (listed as "playable"!).  :)

---

### Post by MaximB on 2006-11-11
how exactly do I compile this ?

---

### Post by tenghoward on 2006-11-23
Inside of PSCX2 Source code. :KS 

> In the main directory type:

aclocal

autoconf

automake

./configure [options]

make





[options] include



--enable-debug {Build with symbols and no optimizations}

--enable-devbuild {Build with extra tests}

However, when I tried to compile it, it gave me error. ](*,) 

```
Making all in .
make[1]: Entering directory `/home/tenghoward/Desktop/PCSX2'
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT CDVDiso.o -MD -MP -MF ".deps/CDVDiso.Tpo" -c -o CDVDiso.o CDVDiso.c; \
        then mv -f ".deps/CDVDiso.Tpo" ".deps/CDVDiso.Po"; else rm -f ".deps/CDVDiso.Tpo"; exit 1; fi
CDVDiso.c: In function &#8216;DvdRead&#8217;:
CDVDiso.c:202: error: invalid lvalue in assignment
CDVDiso.c: In function &#8216;CDVD_findfile&#8217;:
CDVDiso.c:304: error: invalid lvalue in assignment
CDVDiso.c:309: error: invalid lvalue in assignment
CDVDiso.c:310: error: invalid lvalue in assignment
CDVDiso.c:364: error: invalid lvalue in assignment
CDVDiso.c:389: error: invalid lvalue in assignment
CDVDiso.c:414: error: invalid lvalue in assignment
CDVDiso.c:415: error: invalid lvalue in assignment
CDVDiso.c:416: error: invalid lvalue in assignment
CDVDiso.c:423: error: invalid lvalue in assignment
CDVDiso.c:428: error: invalid lvalue in assignment
CDVDiso.c:429: error: invalid lvalue in assignment
CDVDiso.c:430: error: invalid lvalue in assignment
CDVDiso.c:459: error: invalid lvalue in assignment
CDVDiso.c:474: error: invalid lvalue in assignment
CDVDiso.c: In function &#8216;CDVD_GetDir_RPC_request&#8217;:
CDVDiso.c:525: error: invalid lvalue in assignment
CDVDiso.c:530: error: invalid lvalue in assignment
CDVDiso.c:531: error: invalid lvalue in assignment
CDVDiso.c:567: error: invalid lvalue in assignment
CDVDiso.c:592: error: invalid lvalue in assignment
CDVDiso.c:615: error: invalid lvalue in assignment
CDVDiso.c:616: error: invalid lvalue in assignment
CDVDiso.c:617: error: invalid lvalue in assignment
CDVDiso.c:629: error: invalid lvalue in assignment
CDVDiso.c:641: error: invalid lvalue in assignment
CDVDiso.c:642: error: invalid lvalue in assignment
CDVDiso.c:643: error: invalid lvalue in assignment
CDVDiso.c:665: error: invalid lvalue in assignment
CDVDiso.c:698: error: invalid lvalue in assignment
CDVDiso.c: In function &#8216;CDVD_GetDir_RPC_get_entries&#8217;:
CDVDiso.c:735: error: invalid lvalue in assignment
CDVDiso.c:736: error: invalid lvalue in assignment
CDVDiso.c:737: error: invalid lvalue in assignment
CDVDiso.c:742: error: invalid lvalue in assignment
CDVDiso.c:767: error: invalid lvalue in assignment
CDVDiso.c:793: error: invalid lvalue in assignment
CDVDiso.c:803: error: invalid lvalue in assignment
CDVDiso.c:809: error: invalid lvalue in assignment
make[1]: *** [CDVDiso.o] Error 1
make[1]: Leaving directory `/home/tenghoward/Desktop/PCSX2'
make: *** [all-recursive] Error 1

```

Howard T.

---

### Post by bebop_tango on 2006-11-27
I'm having the exact same errors while compiling the source...

---

### Post by KLineD on 2006-12-04
When I do automake I get
```
automake: configure.ac: required file `./config.guess' not found
automake: configure.ac: required file `./config.sub' not found
Linux/Makefile.am:10: LDADD defined both conditionally and unconditionally
```

And then ./configure fails with:
```

configure: creating ./config.status
config.status: creating Makefile
config.status: WARNING:  Makefile.in seems to ignore the --datarootdir setting
config.status: creating DebugTools/Makefile
config.status: WARNING:  DebugTools/Makefile.in seems to ignore the --datarootdir setting
config.status: creating Linux/Makefile
config.status: WARNING:  Linux/Makefile.in seems to ignore the --datarootdir setting
config.status: creating IPU/Makefile
config.status: WARNING:  IPU/Makefile.in seems to ignore the --datarootdir setting
config.status: creating IPU/mpeg2lib/Makefile
config.status: WARNING:  IPU/mpeg2lib/Makefile.in seems to ignore the --datarootdir setting
config.status: creating pcl/Makefile
config.status: WARNING:  pcl/Makefile.in seems to ignore the --datarootdir setting
config.status: creating RDebug/Makefile
config.status: WARNING:  RDebug/Makefile.in seems to ignore the --datarootdir setting
config.status: creating tinyxml/Makefile
config.status: WARNING:  tinyxml/Makefile.in seems to ignore the --datarootdir setting
config.status: creating x86/Makefile
config.status: WARNING:  x86/Makefile.in seems to ignore the --datarootdir setting
config.status: creating x86/ix86/Makefile
config.status: WARNING:  x86/ix86/Makefile.in seems to ignore the --datarootdir setting
config.status: creating x86/ix86-32/Makefile
config.status: WARNING:  x86/ix86-32/Makefile.in seems to ignore the --datarootdir setting
config.status: creating x86/ix86-64/Makefile
config.status: WARNING:  x86/ix86-64/Makefile.in seems to ignore the --datarootdir setting
config.status: creating zlib/Makefile
config.status: WARNING:  zlib/Makefile.in seems to ignore the --datarootdir setting
./configure: line 4829: bindir: command not found
Configuration:
  Target system type:    
  x86-64 build?        no
  Debug build?         no
  Dev build?           no

```

I've been trying to get this to compile for a long time now.

---

### Post by damvcoool on 2006-12-06
> **KLineD said:**
> When I do automake I get
```
automake: configure.ac: required file `./config.guess' not found
automake: configure.ac: required file `./config.sub' not found
Linux/Makefile.am:10: LDADD defined both conditionally and unconditionally
```


Try using automake 1.9

---

### Post by dracule on 2006-12-06
i get this :

make[1]: Entering directory `/home/jaoaja/Desktop/PCSX2'
if gcc -DPACKAGE_NAME=\"pcsx2\" -DPACKAGE_TARNAME=\"pcsx2\" -DPACKAGE_VERSION=\"0.9.2\" -DPACKAGE_STRING=\"pcsx2\ 0.9.2\" -DPACKAGE_BUGREPORT=\"zerofrog@gmail.com\" -DPACKAGE=\"pcsx2\" -DVERSION=\"0.9.2\" -I. -I. -IDebugTools/ -Ix86/  -O2 -fomit-frame-pointer   -O2 -fomit-frame-pointer  -MT memcpy_amd.o -MD -MP -MF ".deps/memcpy_amd.Tpo" -c -o memcpy_amd.o memcpy_amd.cpp; \
        then mv -f ".deps/memcpy_amd.Tpo" ".deps/memcpy_amd.Po"; else rm -f ".deps/memcpy_amd.Tpo"; exit 1; fi
Misc.h: In function &#8216;void* pcsx2_aligned_malloc(size_t, size_t)&#8217;:
Misc.h:157: error: cast from &#8216;char*&#8217; to &#8216;int&#8217; loses precision
make[1]: *** [memcpy_amd.o] Error 1
make[1]: Leaving directory `/home/jaoao/Desktop/PCSX2'
make: *** [all-recursive] Error 1

---

### Post by dracule on 2006-12-07
reading the official forum, they say no linux support until the next release in around feburary.

---

### Post by tenghoward on 2006-12-13
> **dracule said:**
> reading the official forum, they say no linux support until the next release in around feburary.

That explains it. ;) I will be waiting for the next release to come out. :)

Howard T.

---

### Post by KLineD on 2007-02-12
> Work has been silently progressing over in camp PCSX2. So whats going on?

Well for starters PCSX2 linux. Development for PCSX2 linux has gone extremely well, so well infact that several games already run on the developers machine and soon we betatesters shall be entering mainstream testing phase.

[Almost there]("http://www.pcsx2.net/")...

---

### Post by po0f on 2007-02-13
YaY

I can't wait to be able to play FFX and Dynasty Warriors 3 on my box.  :)

---

### Post by KLineD on 2007-04-02
It's finally done! I'm reading this in NGEmu:

> A new release of PCSX2 is now avaliable!  Penguin users rejoice, because this release is only for Linux operating systems.

    Well linux users, we promised we'd have you back and here is the living breathing proof!

    Along with this release you have a couple of new plugins exclusively!

        * ZeroPAD - New pad plugin based off Twinpad, PADWinkeyb and SSSPSX Pad.
        * ZeroGS OGL - An OpenGL conversion of ZeroGS. No more GSSoft for you

    You also have available a 32bit and 64bit build for your pleasure, we do spoil you sometimes! Take note the 64bit version is far from finished!
    The next release will be much quicker than the current implimentation... head over to the download section to grab it.

Read it for yourself [here]("http://www.ngemu.com/index.php?action=post&id=2152")

I'll surely check this out

If you are trying the binary version, copy libCg* in the base folder of pcsx2 to /usr/lib/tls I had to make the directory first. Then everything works ok.

---

