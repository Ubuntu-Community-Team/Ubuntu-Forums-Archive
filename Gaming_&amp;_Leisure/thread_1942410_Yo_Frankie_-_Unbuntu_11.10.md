---
title: "Yo Frankie - Unbuntu 11.10"
date: 2012-03-17
forum: Gaming &amp; Leisure
---

### Post by kamelie1706 on 2012-03-17
Hi,

I try the game but I just get the music and blue sky. I cannot do anything else than exit.

I have tried to launch it from command in a window
blenderplayer -w /usr/share/yofrankie-bge/levels/start_menu.blend
I get the following errors
```
read library: '/usr/share/yofrankie-bge/chars/butterfly.blend', '//../chars/butterfly.blend'
read library: '/usr/share/yofrankie-bge/chars/frankie.blend', '//../chars/frankie.blend'
read library: '/usr/share/yofrankie-bge/chars/frankie_actions.blend', '//../chars/frankie_actions.blend'
read library: '/usr/share/yofrankie-bge/chars/bird.blend', '//../chars/bird.blend'
read library: '/usr/share/yofrankie-bge/chars/momo_actions.blend', '//momo_actions.blend'
read library: '/usr/share/yofrankie-bge/chars/frankie_actions.blend', '//frankie_actions.blend'
Detected GL_ARB_texture_env_combine
Detected GL_ARB_texture_cube_map
Detected GL_ARB_multitexture
Detected GL_ARB_shader_objects
Detected GL_ARB_vertex_shader
Detected GL_ARB_fragment_shader
Detected GL_ARB_vertex_program
Detected GL_ARB_depth_texture
Detected GL_EXT_separate_specular_color
warning: could not open '/usr/share/yofrankie-bge/levels/start_menu.bgeconf'
Warning, sensor "menu_delay" has lost a link to a controller (link 2 of 3) from object "menu_logic"
        possible causes are partially appended objects or an error reading the file,logic may be incorrect
Warning, sensor "menu_delay" could not find its controller (link 3 of 3) from object "menu_logic"
        there has been an error converting the blender controller for the game engine,logic may be incorrect
Warning, sensor "sensor2" has lost a link to a controller (link 1 of 1) from object "butterfly_logic"
        possible causes are partially appended objects or an error reading the file,logic may be incorrect
Python module can't be imported - object 'menu_logic', controller 'init_options#CONTR#1':
Traceback (most recent call last):
  File "/usr/share/yofrankie-bge/levels/menu_scripts/__init__.py", line 20, in <module>
    import init
ImportError: No module named init
Warning: could not open marshal file
Python module can't be imported - object 'menu_logic', controller 'menu_logic#CONTR#3':
Traceback (most recent call last):
  File "/usr/share/yofrankie-bge/levels/menu_scripts/__init__.py", line 20, in <module>
    import init
ImportError: No module named init
Python module can't be imported - object 'joy_message', controller 'menu_joystick_message#CONTR#2':
Traceback (most recent call last):
  File "/usr/share/yofrankie-bge/levels/menu_scripts/__init__.py", line 20, in <module>
    import init
ImportError: No module named init
```

blender -v
returns
```
Blender 2.58 (sub 0)
        build date: 2011-08-01
        build time: 03:50:39
        build revision: unknown
        build platform: Linux
        build type: 
        build c flags: -g -O2  -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -fopenmp  -msse2  -msse -pipe -fPIC -funsigned-char -fno-strict-aliasing  -Wall -Wcast-align -Werror=declaration-after-statement -Werror=implicit-function-declaration -Werror=return-type -Wstrict-prototypes -Wno-char-subscripts -Wno-unknown-pragmas -Wpointer-arith -Wunused-parameter -Wwrite-strings -Wno-error=unused-but-set-variable
        build c++ flags: -g -O2  -D__STDC_CONSTANT_MACROS -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -fopenmp  -msse2  -msse -pipe -fPIC -funsigned-char -fno-strict-aliasing  -Wall -Wno-invalid-offsetof -Wno-sign-compare
        build link flags: -pthread
        build system: CMake

```

Any idea? The game looks really nice and my daughter is really waiting for it!

Thanks

---

### Post by BcRich on 2012-03-17
Hi 
This might not be the answer you were looking for but, is that error from a yofrankie installation via ubuntu repositories (universe)?

---

### Post by kamelie1706 on 2012-03-18
hi,

yes from official ubuntu:
yofrankie 1.1b~svn106-0ubuntu1

Just to make sure I have de-install and re-install it.

Reading the comment on the ubuntu software center, I am not the only one ...

*****
It doesn't seem to work on ubuntu 11.10. I don¡t know what's wrong with it but the main menu wont even appear. Al it does is play the same piece of music (5 sec) over and over again over a clouded background.
*****
buntu 10.10/Acer Aspire 2920Z. Loads a bit, then the same clouds. Would have been nice to see the game. Not many cute/girly games out there (for the (other)half of planet's population). I hope you get it right, devs!
*****

The game look very nice!

---

### Post by kamelie1706 on 2012-03-18
By the way, how do you check from which repository a specific package has been installed?

---

### Post by mastablasta on 2012-03-18
what graphics card do you have?

---

### Post by kamelie1706 on 2012-03-18
ATI Radeon HD 4250

Integrated to my motherboard M4A88TD-V EVO-USB3.

---

### Post by BcRich on 2012-03-18
> **kamelie1706 said:**
> hi,

yes from official ubuntu:
yofrankie 1.1b~svn106-0ubuntu1

Just to make sure I have de-install and re-install it.

Reading the comment on the ubuntu software center, I am not the only one ...

*****
It doesn't seem to work on ubuntu 11.10. I don¡t know what's wrong with it but the main menu wont even appear. Al it does is play the same piece of music (5 sec) over and over again over a clouded background.
*****
buntu 10.10/Acer Aspire 2920Z. Loads a bit, then the same clouds. Would have been nice to see the game. Not many cute/girly games out there (for the (other)half of planet's population). I hope you get it right, devs!
*****

The game look very nice!

Hi
That does seem pretty serious, perhaps the repo version might be out of date. I think the most recent version of yo frankie is 1.1 (2009, so even that is pretty much outdated). The main website yofrankie.org has instructions for installing this version, but the instructions for installing the crystalspace version uses zero-install and fails on my system (ubuntu 10.10). I have been able to get the BGE version working on my current system and on older ubuntu systems so you might want to try that version. You can download the 120MB file here [http://download.blender.org/apricot/yofrankie_1_1b_bge.zip](http://download.blender.org/apricot/yofrankie_1_1b_bge.zip) or follow the link to the download section at yofrankie.org.
This version (IMHO) doesn't look as pretty or run as smoothly as the one that uses the crystalspace engine. It stutters on my Radeon 6850HD so I think you will have to disable most of the effects like shadows and high res textures (if you do manage to get it working with your 4250)
Getting this version to work is a bit of overkill, so if you'll bear with me i'll try explain what's involved. The BGE (blender game engine) version is mainly intended for people that have blender installed, so you'll have to install Blender first. You'll need version 2.49 or greater. The BGE version has all the .blend files that are required to make the game work so if you are so inclined you can open those files in blender. But to keep things simple you'll need to
1) Install a version of Blender greater than 2.49 (through your package manager if possible)
2) Download above listed zip file
3) Extract contents of zip file to a location in your local directory (eg /home/kamelie1706/software/games/yofrankie_1_1b_bge/ )
4) Then run the yo_frankie_stub.blend file with the blenderplayer command eg
```
blenderplayer /home/kamelie1706/software/games/yofrankie_1_1b_bge/yo_frankie_stub.blend
```
and you should be able to play the game (albeit with unsmoothed graphics)

or...
(not recommended)
The developers of yofrankie also say that yofrankie can be started from within blender (but this does not work for me because the game is non-responsive to my keyboard). nonetheless if you want to try this method, start blender open the yo_frankie_stub.blend file and with your mouse hovering over the 3D viewport hit "p" on your keyboard.

I hope you manage to get it working.

PS. I use synaptic as my package manager. in synaptic if you click Settings > Preferences and under the General tab there is a checkbox for Appeareance (show package properties in the main window). when that option is checked the "Common" tab has a field called "Section" which indicates where the package is from.

---

### Post by kamelie1706 on 2012-03-18
Thanks!

Actually it did not work :-)

BUT

if I use the binary version "yofrankie-linux-386.bin" found in the archive it works ... but no sound so far.

I will did a bit the options from the config files.

---

