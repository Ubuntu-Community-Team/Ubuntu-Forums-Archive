---
title: "Slune gives exception and doesn't start"
date: 2008-08-30
forum: Gaming &amp; Leisure
---

### Post by cowkiller on 2008-08-30
Hello, I'm trying to run slune on Ubuntu Hardy and it gives me a weird output that I couldn't find around here yet, then crashes out... Looks like an ALSA problem, but I've never seen anything alike. This is the output given: 

```

* Slune * Slune lives in /usr/share/games
* Soya * Using 8 bits stencil buffer

* Soya * version 0.13.2
* Using OpenGL 2.1.7412 Release
*   - renderer : ATI Radeon HD 3870
*   - vendor   : ATI Technologies Inc.
*   - maximum number of lights        : 8
*   - maximum number of clip planes   : 6
*   - maximum number of texture units : 8
*   - maximum texture size            : 8192 pixels
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
open /dev/[sound/]dsp: Device or resource busy
Exception exceptions.TypeError: 'exceptions must be strings, classes, or instances, not exceptions.RuntimeError' in '_soya._init_sound' ignored

Traceback (most recent call last):
  File "/usr/games/slune", line 42, in <module>
    soya.set_sound_volume(globdef.SOUND_VOLUME)
  File "sound.pyx", line 103, in _soya.set_sound_volume
TypeError: exceptions must be strings, classes, or instances, not exceptions.RuntimeError
* Soya3D * Quit...


```

I'm totally puzzled here... anyone can figure out what could it be?

---

### Post by mar2000 on 2008-11-30
I use to play slune just fine with 7.10. Now I upgraded to 8.10. At first, slune did not work at all until I did this:

```

cd /usr/lib
sudo ln -s libGLEW.so.1.5 libGLEW.so.1.4

```

 Now slune starts but will soon crash afterward. This is what I get:

```

* Slune * Slune lives in /usr/share
* Soya * Using 8 bits stencil buffer

* Soya * version 0.14
* Using OpenGL 1.4 Mesa 7.2
*   - renderer : Mesa DRI Intel(R) 965GM 20061102
*   - vendor   : Tungsten Graphics, Inc
*   - maximum number of lights        : 8
*   - maximum number of clip planes   : 6
*   - maximum number of texture units : 8
*   - maximum texture size            : 2048 pixels
* Using OpenAL 1.1
*   - renderer  : OpenAL Soft
*   - vendor    : OpenAL Community

* Slune * (Psyco not found ; if you are using an x86 processor, installing psyco can speed up Slune a little)
* Py2Play * IDLER created !
* Py2Play * creating active player foobar : ('foobar', 'foobar', 36079)...
python: ../common/dri_bufmgr_fake.c:1054: dri_fake_reloc_and_validate_buffer: Assertion `bo_fake->map_count == 0' failed.
Aborted

```

I really don't know if this is an 8.10 issue or just something specific to my computer.

---

### Post by grappler on 2008-12-25
Did you ever sort this problem with slune out? I'm having exactly the same problem on 8.10 on two different computers (a 32 bit and a 64 bit installation).

---

### Post by nailbnny on 2009-03-18
> **grappler said:**
> Did you ever sort this problem with slune out? I'm having exactly the same problem on 8.10 on two different computers (a 32 bit and a 64 bit installation).

It has something to do with python and openal sound.  I really have no idea...  Anyhoo, you can start it with slune --no-sound.

-nB

---

