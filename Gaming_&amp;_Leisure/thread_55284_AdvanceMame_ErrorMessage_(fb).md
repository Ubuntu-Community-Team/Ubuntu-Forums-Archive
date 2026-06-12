---
title: "AdvanceMame ErrorMessage (fb)"
date: 2005-08-08
forum: Gaming &amp; Leisure
---

### Post by tom-ubuntu on 2005-08-08
After an unsuccessful request for AdvanceMame and AdvanceMenu for the backport project, I compiled both myself but getting an error message:

fb: unsupported under x

What does it mean? It actually should run according to the docs, because videomode is set to auto and not to fb. Found a few posts via google where people with Ubuntu are having the same problems, but without any solution.

Perhaps we can figure it out. Anyone else got experience with this?

---

### Post by jeffbacon on 2005-08-30
I'm having the exact same issue.  I built it from source fine, but it complains about the fb not supported.  I'd really like to get this going if anyone has any experience solving this issue.

---

### Post by jeffbacon on 2005-08-31
just ran accross this actually...

[http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=603](http://www.linuxformat.co.uk/index.php?name=PNphpBB2&file=viewtopic&t=603)

.. trying it now....

no dice, "./configure --disable-sdl" configures it all but make files on:
```

obj/menu/linux/blend/lib/videoall.o(.text+0xb): In function `video_reg_driver_all':
: undefined reference to `video_fb_driver'
obj/menu/linux/blend/sdl/vsdl.o(.text+0x1ad): In function `sdl_init':
: undefined reference to `os_internal_sdl_get'
obj/menu/linux/blend/sdl/vsdl.o(.text+0x26b): In function `sdl_init':
: undefined reference to `os_internal_sdl_title_get'
obj/menu/linux/blend/sdl/vsdl.o(.text+0x272): In function `sdl_init':
: undefined reference to `os_internal_sdl_title_get'
obj/menu/linux/blend/sdl/vsdl.o(.text+0xc76): In function `sdl_mode_set':
: undefined reference to `os_internal_sdl_title_get'
obj/menu/linux/blend/sdl/vsdl.o(.text+0xc7d): In function `sdl_mode_set':
: undefined reference to `os_internal_sdl_title_get'
obj/menu/linux/blend/sdl/ssdl.o(.text+0x95): In function `soundb_sdl_init':
: undefined reference to `os_internal_sdl_get'
obj/menu/linux/blend/sdl/ksdl.o(.text+0x20): In function `keyb_sdl_init':
: undefined reference to `os_internal_sdl_get'
obj/menu/linux/blend/sdl/msdl.o(.text+0x18): In function `mouseb_sdl_init':
: undefined reference to `os_internal_sdl_get'
obj/menu/linux/blend/sdl/jsdl.o(.text+0x19): In function `joystickb_sdl_init':
: undefined reference to `os_internal_sdl_get'
collect2: ld returned 1 exit status
make: *** [obj/menu/linux/blend/advmenu] Error 1

```

---

### Post by BoyOfDestiny on 2005-08-31
hmm both advancemame and menu work fine for me (although I couldn't get advancemess to compile... :))

Make sure you have lib-sdl stuff in syanaptic (and the -dev stuff)
The other thing that gave me trouble initially was not having freetype (or freetype config?) so make sure you have that as well.

Good Luck, but rest assured it works

(running breezy on 2.6.12-7?-686)

EDIT: Also when I ran hoary on 2.6.10 both worked (although it was advancemame .97 at the time :)

---

### Post by Mosey on 2005-12-18
did anyone ever resolve this issue...it apparently is still a problem.

I'm getting the same error.

How does one go about disabling framebuffer in advancemame.

---

### Post by bviking on 2008-06-02
> **Mosey said:**
> did anyone ever resolve this issue...it apparently is still a problem.

I'm getting the same error.

How does one go about disabling framebuffer in advancemame.

Sorry to raise a long-dead thread from the grave but this has been giving me the irritations all weekend and I just figured it out.

First off, check you have all needed packages:

```
$ sudo apt-get install gcc libtool libslang2-dev libsdl1.2debian libfreetype6-dev libexpat1-dev \
  libsdl1.2-dev make libxml2-dev g++ fbset
```

A new version of AdvanceMenu was released recently that is supposed to address compilation errors on gcc 4.x.x: [http://advancemame.sourceforge.net/menu-history.html](http://advancemame.sourceforge.net/menu-history.html)

So we download and extract the updated package like this:

```
$ wget [http://prdownloads.sourceforge.net/advancemame/advancemenu-2.4.14.tar.gz?download](http://prdownloads.sourceforge.net/advancemame/advancemenu-2.4.14.tar.gz?download)
$ tar -xvf advancemenu-2.4.14.tar.gz
$ cd advancemenu-2.4.14
```

Then we run the configure script:
```

$ ./configure
```


And if all goes well, we should be able to:

```
$ make
```


However, at this point I ran into the compilation errors others have posted above. I think it was because I had started a "make" without some of the required packages installed.

A simple

```
$ make clean
$ make
```

and I'm good to go!

Hope this helps someone else.

By the way, there's heaps of useful info here: 

[http://enzerink.net/peter/wiki/index.php?title=DebMAME](http://enzerink.net/peter/wiki/index.php?title=DebMAME)

which helped me figure this out!

---

