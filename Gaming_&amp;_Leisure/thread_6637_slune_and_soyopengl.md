---
title: "slune and soyopengl"
date: 2004-11-30
forum: Gaming &amp; Leisure
---

### Post by franx on 2004-11-30
I installed and tried to start the game slune.  Here's the response I got:

franx@ubuntu:~ $ slune
* Slune * Slune lives in /usr/share/games
* Soya 3D * Using 8 bits stencil buffer

* Soya 3D * version 0.8.1
* Using OpenGL 1.2 Mesa 4.0.4
*   - renderer : Mesa DRI Rage128 20020221 AGP 1x
*   - vendor   : VA Linux Systems, Inc.
*   - maximum number of lights        : 8
*   - maximum number of clip planes   : 6
*   - maximum number of texture units : 2
*   - maximum texture size            : 512 pixels

Traceback (most recent call last):
  File "/usr/games/slune", line 128, in ?
    import slune.level, slune.character, slune.player
  File "/usr/share/games/slune/level.py", line 23, in ?
    import soya, soya.widget as widget, soyaopengl
ImportError: No module named soyaopengl
* Soya3D * Quit...

Anybody know what it means?  Anything I can do about it to get the game to work?

Fran

---

