---
title: "Lemming ball z problem"
date: 2010-12-05
forum: Gaming &amp; Leisure
---

### Post by DMKryl on 2010-12-05
Hi again, looking around the sites the forum suggested, i found this game, lemming ball z ```
http://www.youtube.com/watch?v=asaM6J4JpYI&feature=player_embedded
``` i downloaded but it doesn't run looks like it lacks of something but i couldn't find what is

```
kryl@Sasha:~/Desktop/lbz3d$ bash lbzrun
LBZ LINUX build 8460 starting....
Version date: Sun Nov  9 16:14:02 CET 2008
can't gzopen tmp/updatorOutput.xml.gz
Suspicious responce, canceling update!
Added "lbz data directory". 945 new, 0 overwritten, 945 total, 0 errors.
Added "patch data". 5 new, 0 overwritten, 950 total, 0 errors.
Testing network-relevant game files...
Game tested: LibCRC 9138EB27(13) GameCRC 60F470D8(628)
Compiling all LGS scripts:..........OK
Attempting to detect joysticks: 0 detected.
Setting OpenGL window: 1024x768
Setting up opengl....
Writing out hardware info to 'hardware.txt'
OpenGL version: 2.1 Mesa 7.9-devel
OpenGL vendor: Tungsten Graphics, Inc
OpenGL renderer: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2
Texture units: 8
Maximum texture size: 4096, windowsize: 1024
Texture compression enabled.
[COLOR="Indigo"]Your hardware looks ok to me! :)[/COLOR]
Vertex Buffer Object extension enabled.
w00t! running on high-end hardware with GLSL! :)
loading vertex shaders.
loading pixel shaders.
Setting up soundsystem using: OSS
FSOUND: Sound Error: Error initializing output device.
Setting sound volume to 50
loading sounds.
loading textures.
compiling game code:
building level list:
LEVEL: space
LEVEL: namek
LEVEL: cave
LEVEL: hill
LEVEL: desert
LEVEL: coldworld
LEVEL: hbtc
LEVEL: Beachparty
LEVEL: asteroids
LEVEL: lost
LEVEL: earth
LEVEL: destroyednamek
LEVEL: vortex
LEVEL: cellarena
building character list:
CHARACTER: Broly
CHARACTER: Raditz
CHARACTER: Cell
CHARACTER: Vegeta
CHARACTER: Piccolo
CHARACTER: Gotenks
CHARACTER: Trunks
CHARACTER: MajinBuu
CHARACTER: Freeza
!!!FATAL EXCEPTION!!!

To enable debugger run 'debuglbz.bat'. (or 'debuglbz.sh')
This will generate more information that will help the DEVELOPER. (AnalyticaL)

sh: kdialog: not found
```

i also tried the debug version and the only different thing was
```
******************************************** DEBUG: ********************************************

Version 8460 made a Boo Boo :(
    Watches:
      Curtex==187
      Curscript==119
    Watches done.
Memory protection error in:
File:"lbz/draw.cpp" Function:"DrawGLSCENE" ->
File:"lbz/game.cpp" Function:"CalculateGameVars" ->
File:"lbz/data.cpp" Function:"loadallstuff" ->
File:"lbz/data.cpp" Function:"parsechars" ->
File:"lbz/XmlParser.cpp" Function:"t_XmlParser::Parse" ->
File:"lbz/XmlParser.cpp" Function:"t_XmlParser::Parse" ->
Trace ended somewhere after line 191

************************************************************************************************

```

---

### Post by GenLinux on 2011-01-08
I know this post is old, I got the same issue, just take a look at the official forums of lbz3d and you can see an announcement saying the GNU/Linux version is facing problems all the time: Official fix? Use Wine....

Maybe sooner or later they'll fix this issue and release the LBZAlpha for GNU/Linux, Until that just don't play lbz3d :)

---

