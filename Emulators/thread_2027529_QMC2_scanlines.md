---
title: "QMC2 scanlines"
date: 2012-07-16
forum: Emulators
---

### Post by nll on 2012-07-16
Hey, I'm trying to get QMC2 to play games with scanlines by going to tools>options>emulator>global settings>video>effect and choosing one of the attached pngs which I got from a MAME forum, but none of them is working. The only video settings I changed from the default were unchecking keepaspect and trading soft for opengl.

Does anyone know what could be going on?

---

### Post by nll on 2012-07-27
Well, did anyone at least have had success with another MAME frontend?

---

### Post by nll on 2012-08-04
I found out what the problem was! =)

For some reason, MAME can't get a full path to a effect file, just the name of the file when it's on /usr/local/share/games/mame/artwork. This is what I get in the commmand line:

```
nll@nll:~$ /usr/games/mame -rompath "/home/nll/.Roms/MAME" -gl_glsl -video opengl -nokeepaspect -effect /usr/local/share/games/mame/artwork/Scanlines25x4.png mvsc
Unable to load effect PNG file '/usr/local/share/games/mame/artwork/Scanlines25x4.png'
```I can only get overlay effects when I run the game with this command:
```
nll@nll:~$ /usr/games/mame -rompath "/home/nll/.Roms/MAME" -gl_glsl -video opengl -nokeepaspect -effect Scanlines25x4.png mvsc
```So, as a temporary workaround, we can get QMC2's output, fix the effect name and run it in the terminal. (Edit: I tried adding just Scanlines25x4 instead of /usr/local/share/games/mame/artwork/Scanlines25x4.png in the QMC2 effect options and it worked too, so there's no need for terminals if we just copy the overlay pngs to the right folder. =])
  
It looks like a bug. I'll see where I can report it.

(And yes, I do own an original mvsc arcade. ;D)

---

### Post by nll on 2012-08-04
While I was looking for a solution for this problem, I also found out about GLSL CRT shaders. In case anyone is interested in them, here's what I done.

1- Get the latest version of cgwg's shader called CRT-geom-20120130.zip [here]("http://www.sendspace.com/file/gctlod") and unzip it in ~/.mame/CRT.
2- Get MAME's source for your version from [http://mamedev.org/]("http://mamedev.org/,"), unzip it and copy the contents of mame/src/osd/sdl/shader folder in ~/.mame/CRT/shader.
                                  [FONT=Ubuntu]3- In QMC2's global settings tab in Emulator options, check gl_glsl and gl_glsl_filter, and add /home/username/.mame/CRT/shader/glsl_plain to glsl_shader_mame0 and /home/username/.mame/CRT/CRT-geom to glsl_shader_mame1. [/FONT][FONT=Ubuntu]
[/FONT]
[FONT=Ubuntu](Thanks to [eldiau]("http://forum.arcadecontrols.com/index.php/topic,120205.msg1274848.html#msg1274848") for the hint.) 
[/FONT]
 [FONT=Ubuntu]The best thing about this is that cwgw's shader is highly customizable. There's a very detailed guide to customizing it [here]("http://filthypants.blogspot.com.br/2012/07/customizing-cgwgs-crt-pixel-shader.html"). The only problem with it is it's very cpu intensive. I have an Intel HD3000 and an Nvidia GT520M, and neither GPU could run higher than 70 %. I also couldn't run any CPS-1 and CPS-2 games, just CPS-3 and Neo Geo You'll need a very powerfull GPU to play games using this shader.
[/FONT]

---

### Post by wingnux on 2012-10-10
It's not working for me at all =/ 
Any help?

[[IMG]http://imageshack.us/a/img96/9881/snapshot144j.png[/IMG]](http://imageshack.us/photo/my-images/96/snapshot144j.png/)

EDIT: It works now! Had to change the video renderer from sdl to opengl =)

---

