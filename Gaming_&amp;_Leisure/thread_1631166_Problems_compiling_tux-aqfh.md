---
title: "Problems compiling tux-aqfh"
date: 2010-11-26
forum: Gaming &amp; Leisure
---

### Post by VuRp0 on 2010-11-26
I tried to compile tux-aqfh from source and got this:
```
Making all in src
make[1]: Entering directory `/tmp/tux_aqfh-1.0.14--20101126145045/tux_aqfh-1.0.14/src'
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c camera.cxx
In file included from tux.h:69,
                 from camera.cxx:1:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c components.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c fade_out.cxx
In file included from tux.h:69,
                 from fade_out.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c feature.cxx
In file included from tux.h:69,
                 from feature.cxx:1:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c gfx.cxx
In file included from tux.h:69,
                 from gfx.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
gfx.cxx: In function â€˜void initWindow(int, int)â€™:
gfx.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
gfx.cxx:36: warning: deprecated conversion from string constant to â€˜char*â€™
gfx.cxx:41: warning: deprecated conversion from string constant to â€˜char*â€™
gfx.cxx:42: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c globalstate.cxx
In file included from tux.h:69,
                 from globalstate.cxx:1:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c gui.cxx
In file included from tux.h:69,
                 from gui.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx: At global scope:
gui.cxx:116: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:119: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:119: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:119: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:119: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:122: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:122: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:122: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:122: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:125: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:125: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:125: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:125: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:128: warning: deprecated conversion from string constant
 to â€˜char*â€™
gui.cxx:128: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:128: warning: deprecated conversion from string constant to â€˜char*â€™
gui.cxx:128: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c hooks.cxx
In file included from tux.h:69,
                 from hooks.cxx:1:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx: In function â€˜float slam_show(int, float*)â€™:
hooks.cxx:200: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx: At global scope:
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conversion from string constant to â€˜char*â€™
hooks.cxx:319: warning: deprecated conve
rsion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c score.cxx
In file included from tux.h:69,
                 from score.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
score.cxx: In function â€˜void reset_tuxrc()â€™:
score.cxx:14: warning: deprecated conversion from string constant to â€˜char*â€™
score.cxx: In function â€˜void parse_tuxrc(int*)â€™:
score.cxx:22: warning: deprecated conversion from string constant to â€˜char*â€™
score.cxx: In function â€˜void save_tuxrc()â€™:
score.cxx:111: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c isect.cxx
In file included from tux.h:69,
                 from isect.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c level.cxx
In file included from tux.h:69,
                 from level.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx: At global scope:
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx: In function â€˜void herring_command(LevelLoaderStatus*, char*, char*)â€™:
level.cxx:609: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:610: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:611: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:612: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:613: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:614: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx: At global scope:
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:71
8: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from s
tring constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
level.cxx:718: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c material.cxx
In file included from tux.h:69,
                 from material.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx: At global scope:
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94:
 warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprec
ated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion 
from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string cons
tant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
material.cxx:94: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c ocean.cxx
In file included from tux.h:69,
                 from ocean.cxx:1:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c orca.cxx
In file included from tux.h:69,
                 from orca.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c penguin.cxx
In file included from tux.h:69,
                 from penguin.cxx:1:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c rocket.cxx
In file included from tux.h:69,
                 from rocket.cxx:1:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c sound.cxx
In file included from tux.h:69,
                 from sound.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx: At global scope:
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from st
ring constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx:37: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx: In member function â€˜void SoundSystem::change_track(char*)â€™:
sound.cxx:55: warning: deprecated conversion from string constant to â€˜char*â€™
sound.cxx: In constructor â€˜SoundSystem::SoundSystem()â€™:
sound.cxx:104: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c starwing.cxx
In file included from tux.h:69,
                 from starwing.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
starwing.cxx: In member function â€˜void StarWing::strategy(float*)â€™:
starwing.cxx:127: warning: â€˜nearest[2]â€™ may be used uninitialized in this function
starwing.cxx:127: warning: â€˜nearest[1]â€™ may be used uninitialized in this function
starwing.cxx:127: warning: â€˜nearest[0]â€™ may be used uninitialized in this function
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c status.cxx
In file included from tux.h:69,
                 from status.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void start_stopwatch()â€™:
status.cxx:50: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void stop_stopwatch()â€™:
status.cxx:63: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void drawHelpText()â€™:
status.cxx:168: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:169: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:170: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:171: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:172: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:176: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:177: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:178: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:179: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:180: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:181: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:182: warning: deprecated conversion from string c
onstant to â€˜char*â€™
status.cxx:183: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:184: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:188: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:189: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:190: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void drawTitleText()â€™:
status.cxx:197: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:198: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:200: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:203: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:205: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void drawDeathText()â€™:
status.cxx:212: warning: deprecated conversion from string constant
 to â€˜char*â€™
status.cxx:214: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void drawIntroText()â€™:
status.cxx:226: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:230: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: At global scope:
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249
: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:249: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void drawVersionsText()â€™:
status.cxx:293: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void drawAboutText()â€™:
status.cxx:302: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:310: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: At global scope:
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â
€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:330: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void drawCreditsText()â€™:
status.cxx:339: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx:347: warning: deprecated conversion from string constant to â€˜char*â€™
status.cxx: In function â€˜void drawStatusText
()â€™:
status.cxx:435: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c surf_rev.cxx
In file included from tux.h:69,
                 from surf_rev.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c tux.cxx
In file included from tux.h:69,
                 from tux.cxx:1:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
tux.cxx: In function â€˜int main(int, char**)â€™:
tux.cxx:143: warning: deprecated conversion from string constant to â€˜char*â€™
tux.cxx:146: warning: deprecated conversion from string constant to â€˜char*â€™
tux.cxx:149: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c tuxstate.cxx
In file included from tux.h:69,
                 from tuxstate.cxx:2:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
tuxstate.cxx: In member function â€˜void TuxState::gasp()â€™:
tuxstate.cxx:87: warning: deprecated conversion from string constant to â€˜char*â€™
tuxstate.cxx: In member function â€˜void TuxState::blub()â€™:
tuxstate.cxx:95: warning: deprecated conversion from string constant to â€˜char*â€™
tuxstate.cxx: In member function â€˜void TuxState::print()â€™:
tuxstate.cxx:347: warning: deprecated conversion from string constant to â€˜char*â€™
tuxstate.cxx:348: warning: deprecated conversion from string constant to â€˜char*â€™
tuxstate.cxx:349: warning: deprecated conversion from string constant to â€˜char*â€™
tuxstate.cxx: In member function â€˜float TuxState::getIsectData(float*, float*, float*, float*, int)â€™:
tuxstate.cxx:515: warning: deprecated conversion from string constant to â€˜char*â€™
tuxstate.cxx:626: warning: deprecated conversion from string constant to â€˜char*â€™
tuxstate.cxx: In member function â€˜void TuxState::update()â€™:
tuxstate.cxx:1232: warning: deprecated conversion from string constant to â€˜char*â€™
tuxstate.cxx:1241: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c whale.cxx
In file included from tux.h:69,
                 from whale.cxx:1:
tuxstate.h: In member function â€˜void TuxState::ouch(float)â€™:
tuxstate.h:199: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamRun.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamCodeGen.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamExpression.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slam.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamStatement.cxx
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated con
version from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx:35: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx: In member function â€˜int SLAM_Program::pushIfStatement()â€™:
slamStatement.cxx:133: warning: deprecated conversion from string constant to â€˜char*â€™
slamStatement.cxx: In member function â€˜int SLAM_Program::pushCompoundStatement()â€™:
slamStatement.cxx:244: warning: deprecated conversion from string constant to â€˜char*â€™
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamSymbols.cxx
c++ -DPACKAGE=\"tux_aqfh\" -DVERSION=\"1.0.14\" -DHAVE_LIBGLU=1 -DHAVE_LIBGLUT=1 -DSTDC_HEADERS=1 -DHAVE_GL_GL_H=1 -DHAVE_GL_GLU_H=1 -DHAVE_GL_GLUT_H=1 -DLINUX_JOYSTICK_IS_PRESENT=1 -DTUX_AQFH_DATADIR=\"/usr/share/games/tux_aqfh\"  -I. -I.      -g -O2 -O6 -Wall -c slamToken.cxx
c++  -g -O2 -O6 -Wall  -o tux_aqfh  camera.o components.o fade_out.o feature.o gfx.o globalstate.o gui.o hooks.o score.o isect.o level.o material.o ocean.o orca.o penguin.o rocket.o sound.o starwing.o status.o surf_rev.o tux.o tuxstate.o whale.o slamRun.o slamCodeGen.o slamExpression.o slam.o slamStatement.o slamSymbols.o slamToken.o  -lplibsl -lplibssg -lplibpu -lplibfnt -lplibsg -lplibul -lglut -lGLU    -lSM -lICE -lpthread -lX11 -lXi -lXext -lXmu  -lm
gui.o: In function `
GUI::joystickInput()':
/tmp/tux_aqfh-1.0.14--20101126145045/tux_aqfh-1.0.14/src/gui.cxx:276: undefined reference to `jsJoystick::read(int*, float*)'
gui.o: In function `GUI':
/tmp/tux_aqfh-1.0.14--20101126145045/tux_aqfh-1.0.14/src/gui.cxx:172: undefined reference to `jsJoystick::jsJoystick(int)'
/tmp/tux_aqfh-1.0.14--20101126145045/tux_aqfh-1.0.14/src/gui.cxx:172: undefined reference to `jsJoystick::jsJoystick(int)'
collect2: ld returned 1 exit status
make[1]: Leaving directory `/tmp/tux_aqfh-1.0.14--20101126145045/tux_aqfh-1.0.14/src'
make[1]: *** [tux_aqfh] Error 1
make: *** [all-recursive] Error 1
```What should I do to make this compile?
I really want to test this game out.
Thanks in advance
I have never compiled anything before, just followed a guide I found

---

### Post by VuRp0 on 2010-11-29
Bump..

---

### Post by VuRp0 on 2010-12-03
Solved, by changing line 1362 in 'configure' to:
plib_suffix="-lplibsl -lplibssg -lplibpu -lplibfnt -lplibsg -lplibul -lplibjs"

---

