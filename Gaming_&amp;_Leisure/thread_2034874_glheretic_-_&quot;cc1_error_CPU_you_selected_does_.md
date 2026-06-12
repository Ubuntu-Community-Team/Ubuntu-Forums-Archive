---
title: "glheretic - &quot;cc1: error: CPU you selected does not support x86-64 instruction set&quot;"
date: 2012-07-29
forum: Gaming &amp; Leisure
---

### Post by Rhodoferax on 2012-07-29
I'm trying to install *Heretic* from source.

I downloaded the .tar.gz shareware wad from [here; ]("http://heretic.linuxgames.com/homepage3.html")no problems.

I began following the instructions on [this page]("https://help.ubuntu.com/community/CompilingEasyHowTo"), and when I tried entering ```
make
``` I got this output:

```

make glheretic - will build GLHeretic - needs OpenGL hardware accelleration

 make sndserver - will build the soundserver for Heretic

 make musserver - will build the musicserver (from lxdoom) for Heretic

 make clean     - will clean up object and exec files

```So then I tried entering ```
make glheretic
```, and the terminal gave me this:

```

gcc -pipe -E -M -Wall -DUNIX -DHAVE_USLEEP -DHAVE_MATH_H -DHAVE_VALUES_H -DLINUX_MOUSE -DUDP_PROTOCOL -DI_GGI_HERETIC -DNEED_SHMGETEVENTBASE -D__NEWVGALIB__  -O2 -fomit-frame-pointer -mcpu=i586 -march=i586 -D__32BIT__ -DHAVE_ALLOCA_H -DINLINE_FIXED -I. -I.. -I/usr/X11R6/include -D__DOSOUND__ -DSNDSERV -Isoundclient -D__DOMUSIC__ -DMUSSERV  -Iopengl -DGL_HERETIC -I/usr/X11R6/include -DNICE_GL -L/usr/X11R6/lib *.c opengl/*.c \
    soundclient/i_sound.c soundclient/soundst.c soundclient/sounds.c m_misc.c graphics/i_sdl_gl.c > .depend 
gcc: warning: ‘-mcpu=’ is deprecated; use ‘-mtune=’ or ‘-march=’ instead
cc1: error: CPU you selected does not support x86-64 instruction set
#snip
make: *** [depsdlogl] Error 1

```(note: it actually output ```
cc1: error: CPU you selected does not support x86-64 instruction set
``` a little over 100 times, but I've cut out all but one to keep this post to a reasonable length. The ```
#snip
``` shows where the rest were).

I did some Googling, and I* think* the problem might be to do with gcc, but I can't find any way to update it.

Stuff that is probably relevant:

* I'm using Ubuntu 12.04
* ```
gcc --version
``` gives ```
gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
```*```
 uname -a
``` gives ```
Linux <my PC's name> 3.2.0-27-generic #43-Ubuntu SMP Fri Jul 6 14:25:57 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```Anybody know what might be going on?

---

### Post by spjackson on 2012-07-29
The package you are trying to build has been configured to target 32 bit systems. We know this because
```

-mcpu=i586 -march=i586 -D__32BIT__

```are passed to gcc.

On a 64-bit system such as yours, the gcc and associated libraries are 64-bit and cannot generate code for 32 bit.

That's what your error message means. Now what can you do about it? If you are only going to run it on your 64-bit system, then find out whether you can configure it for a 64-bit build. If you want to run it on 32-bit systems or if this software only works as 32-bit, then you will need to install extra gcc and library packages for building 32-bit on 64-bit systems. (I don't recall the package names.)

---

