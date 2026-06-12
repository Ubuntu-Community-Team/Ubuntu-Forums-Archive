---
title: "Balazar crashes on startup"
date: 2007-10-04
forum: Gaming &amp; Leisure
---

### Post by blastradius on 2007-10-04
Just installed Feisty, went and installed Balazar using add/remove from the main menu, everything went fine but when clicking on Balazar or typing at the terminal I got this:-

Balazar * Balazar lives in /usr/share/games
* Balazar * (Psyco not found ; if you are using an x86 processor, installing psyco can speed up Balazar a little)
* Soya * Using 8 bits stencil buffer

* Soya * version 0.12
* Using OpenGL 1.3 Mesa 6.5.2
*   - renderer : Mesa DRI R300 20060815 AGP 1x x86/MMX+/3DNow!+/SSE2 TCL
*   - vendor   : Tungsten Graphics, Inc.
*   - maximum number of lights        : 8
*   - maximum number of clip planes   : 6
*   - maximum number of texture units : 8
*   - maximum texture size            : 2048 pixels
* Using OpenAL 1.1
*   - renderer  : Software
*   - vendor    : OpenAL Community

*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 430
Software fallback:ctx->Point.SmoothFlag
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
Unknown GL_ERROR
Traceback (most recent call last):
  File "/usr/games/balazar", line 138, in <module>
    balazar.game_interface.init()
  File "/usr/share/games/balazar/game_interface.py", line 39, in init
    soya.render()
  File "renderer.pyx", line 424, in _soya.render
  File "renderer.pyx", line 404, in _soya.check_gl_error
TypeError: exceptions must be strings, classes, or instances, not GLError
* Soya3D * Quit...

Any ideas????

---

### Post by qubodup on 2007-10-04
*does* work for me with following output:
```
$ balazar
* Balazar * Balazar lives in /usr/share/games
* Balazar * (Psyco not found ; if you are using an x86 processor, installing psyco can speed up Balazar a little)
* Soya * Using 8 bits stencil buffer

* Soya * version 0.12
* Using OpenGL 2.1.0 NVIDIA 96.31
*   - renderer : GeForce FX 5200/AGP/SSE/3DNOW!
*   - vendor   : NVIDIA Corporation
*   - maximum number of lights        : 8
*   - maximum number of clip planes   : 6
*   - maximum number of texture units : 4
*   - maximum texture size            : 4096 pixels
* Using OpenAL 1.1
*   - renderer  : Software
*   - vendor    : OpenAL Community
```

Reinstall package?

If no help, you should probably contact the devs.

---

### Post by Ant_Merlin on 2007-10-04
Hello, It looks like you are using Mesa as openGL. This basically means you have not got Graphics card drivers installed that are using OPENGL hardware rendering. iy is trying to render opengl in software. You may need to install drivers for your graphics card. If you have ATI or GEFORCE you can use Envy to install (easiest way)
[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb]("http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb")

select open with Gdebi package Installer.
Start Envy > applications>system tools>envy
and install appropriate driver.
Restart.
then try running balazar again.

---

### Post by blastradius on 2007-10-05
I ran the Envy prog', all installed fine but I've still got the same problem!

Thanks for the replies by the way.

---

### Post by blastradius on 2007-10-05
SORRY!  

Ignore the last post, the message box asking me to reboot was behind my browser so I hadn't seen it when I tried Balazar again.

Everything is ok now.  Thanks guys!!

---

### Post by blastradius on 2007-10-05
Graphics do run very choppy and slow though.

---

### Post by Ant_Merlin on 2007-10-05
Glad envy installed ok. according to qubodups post it looks like it still uses software renderer which will explain slow speed, not used myself, is there an open to change to hardware render?

---

### Post by blastradius on 2007-10-05
Sorted it! ATI drivers needed to be installed.  Piece of cake really.

Now all I have to do is work out how to play the game!!

Thanks again.

---

### Post by qubodup on 2007-10-05
> **Ant_Merlin said:**
> Glad envy installed ok. according to qubodups post it looks like it still uses software renderer which will explain slow speed, not used myself, is there an open to change to hardware render?

It uses software render for **Audio** :)

---

