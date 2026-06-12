---
title: "MAME issue"
date: 2011-02-17
forum: Gaming &amp; Leisure
---

### Post by Programmerfromthehood on 2011-02-17
So, I've recently gotten sdlmame to work on ubuntu 10.10. But there's a tiny(but big, I guess) issue. Every game in mame goes at an okay rate of 40fps on full screen, the thing is I know that cps3 might have a few issues with it on this Acer Aspire One D250, but **everything** runs at 40fps, games like R-type leo and Elevator Action Returns, for example, are fairly old games still run at 40fps.It doesn't have any problems running other emulators at 60 fps(gens, snes9x,vba). I've also turned off compiz while running mame, and still the same frame rate for all the games. Is it just my crappy netbook or am I not doing something right here? 

Thanks in advance.

---

### Post by disturbedite on 2011-02-18
did you turn off throttling?

---

### Post by Programmerfromthehood on 2011-02-19
> **disturbedite said:**
> did you turn off throttling?
Sorry for my stupidness, I don't know if you're either saying I should leave on throttling if I have it on, or turn it off if I do.

I'll just post my mame .ini to let you see where I'm doing something wrong
```
#
# CORE CONFIGURATION OPTIONS
#
readconfig                1

#
# CORE SEARCH PATH OPTIONS
#
rompath                   $HOME/.mame/roms;/home/james/Games/MAME ROMS
samplepath                $HOME/.mame/samples;/usr/local/share/games/mame/samples
artpath                   $HOME/.mame/artwork;/usr/local/share/games/mame/artwork
ctrlrpath                 /etc/mame/ctrlr
inipath                   /etc/mame
fontpath                  /tmp;/usr/share/games/mame-common
cheatpath                 $HOME/.mame/cheat;$HOME/.mame/cheat/cheat;/usr/local/share/games/mame/cheat;/usr/local/share/games/mame/cheat/cheat
crosshairpath             $HOME/.mame/crosshair;/usr/local/share/games/mame/crosshair

#
# CORE OUTPUT DIRECTORY OPTIONS
#
cfg_directory             $HOME/.mame/cfg
nvram_directory           $HOME/.mame/nvram
memcard_directory         $HOME/.mame/memcard
input_directory           $HOME/.mame/inp
state_directory           $HOME/.mame/sta
snapshot_directory        $HOME/.mame/snap
diff_directory            $HOME/.mame/diff
comment_directory         $HOME/.mame/comments

#
# CORE STATE/PLAYBACK OPTIONS
#
state                     
autosave                  0
playback                  
record                    
mngwrite                  
wavwrite                  

#
# CORE PERFORMANCE OPTIONS
#
autoframeskip             0
frameskip                 0
seconds_to_run            0
throttle                  0
sleep                     1
speed                     1.0

#
# CORE ROTATION OPTIONS
#
rotate                    1
ror                       0
rol                       0
autoror                   0
autorol                   0
flipx                     0
flipy                     0

#
# CORE ARTWORK OPTIONS
#
artwork_crop              0
use_backdrops             1
use_overlays              1
use_bezels                1

#
# CORE SCREEN OPTIONS
#
brightness                1.0
contrast                  1.0
gamma                     1.0
pause_brightness          0.65

#
# CORE VECTOR OPTIONS
#
antialias                 1
beam                      1.0
flicker                   0

#
# CORE SOUND OPTIONS
#
sound                     1
samplerate                48000
samples                   1
volume                    0

#
# CORE INPUT OPTIONS
#
ctrlr                     
mouse                     1
joystick                  1
lightgun                  0
multikeyboard             0
multimouse                0
steadykey                 0
offscreen_reload          0
joystick_map              auto
joystick_deadzone         0.3
joystick_saturation       0.85

#
# CORE INPUT AUTOMATIC ENABLE OPTIONS
#
paddle_device             keyboard
adstick_device            keyboard
pedal_device              keyboard
dial_device               keyboard
trackball_device          keyboard
lightgun_device           keyboard
positional_device         keyboard
mouse_device              mouse

#
# CORE DEBUGGING OPTIONS
#
log                       0
verbose                   0

#
# CORE MISC OPTIONS
#
bios                      default
cheat                     0
skip_gameinfo             0

#
# DEBUGGING OPTIONS
#
oslog                     0

#
# PERFORMANCE OPTIONS
#
multithreading            1
sdlvideofps               1

#
# VIDEO OPTIONS
#
video                     opengl
numscreens                1
window                    0
keepaspect                0
unevenstretch             1
effect                    none
centerh                   1
centerv                   1
waitvsync                 1

#
# OpenGL-SPECIFIC OPTIONS
#
filter                    1
prescale                  0
gl_forcepow2texture       0
gl_notexturerect          0
gl_vbo                    1
gl_pbo                    1
gl_glsl                   0
gl_glsl_filter            1
glsl_shader_mame0         none
glsl_shader_mame1         none
glsl_shader_mame2         none
glsl_shader_mame3         none
glsl_shader_mame4         none
glsl_shader_mame5         none
glsl_shader_mame6         none
glsl_shader_mame7         none
glsl_shader_mame8         none
glsl_shader_mame9         none
glsl_shader_screen0       none
glsl_shader_screen1       none
glsl_shader_screen2       none
glsl_shader_screen3       none
glsl_shader_screen4       none
glsl_shader_screen5       none
glsl_shader_screen6       none
glsl_shader_screen7       none
glsl_shader_screen8       none
glsl_shader_screen9       none
gl_glsl_vid_attr          1

#
# PER-WINDOW VIDEO OPTIONS
#
screen                    auto
aspect                    auto
resolution                auto
view                      auto
screen0                   auto
aspect0                   auto
resolution0               auto
view0                     auto
screen1                   auto
aspect1                   auto
resolution1               auto
view1                     auto
screen2                   auto
aspect2                   auto
resolution2               auto
view2                     auto
screen3                   auto
aspect3                   auto
resolution3               auto
view3                     auto

#
# FULL SCREEN OPTIONS
#
switchres                 0
useallheads               0

#
# SOUND OPTIONS
#
audio_latency             3

#
# INPUT DEVICE OPTIONS
#

#
# SDL KEYBOARD MAPPING
#
# If you are using one of the available non-us keyboard layouts
# set keymap to 1 and uncomment the appropriate line below
keymap                    0
#keymap_file               /usr/share/games/mame-common/keymaps/km-be.txt
#keymap_file               /usr/share/games/mame-common/keymaps/km-ch.txt
#keymap_file               /usr/share/games/mame-common/keymaps/km-de.txt
#keymap_file               /usr/share/games/mame-common/keymaps/km-fr.txt
#keymap_file               /usr/share/games/mame-common/keymaps/km_it.txt

#
# SDL JOYSTICK MAPPING
#
joy_idx1                  auto
joy_idx2                  auto
joy_idx3                  auto
joy_idx4                  auto
joy_idx5                  auto
joy_idx6                  auto
joy_idx7                  auto
joy_idx8                  auto

#
# CORE COMMANDS
#

#
# CONFIGURATION COMMANDS
#

#
# FRONTEND COMMANDS
#
```

---

### Post by disturbedite on 2011-02-19
uh, no offense, but do you know the definition of throttling?
if you're having speed problems you should try turning it off but you already have it turned off though. so that apparently isn't helping.

i missed that you said you're using a netbook, my best guess (i'm a computer technician), knowing netbooks, is that it is insufficient to run some (a lot?) of mame games at full framerate (speed), regardless of its performance with other emulators. (you might post your system specs, or link to your netbook).
regardless of that though, looking at your config file...
you might try turning off 'waitvsync' (change the 1 to 0). you may get tearing but it might improve speed.
you could also try turning filter(ing) off.

if that doesn't help (enough), (you can re-enable vsync then) switch video from opengl to software. you should be able to get much more speed with the software renderer but it means sacrificing a lot of graphical bells and whistles (things may not look as nice).

---

### Post by Programmerfromthehood on 2011-02-20
> **disturbedite said:**
> uh, no offense, but do you know the definition of throttling?
if you're having speed problems you should try turning it off but you already have it turned off though. so that apparently isn't helping.

i missed that you said you're using a netbook, my best guess (i'm a computer technician), knowing netbooks, is that it is insufficient to run some (a lot?) of mame games at full framerate (speed), regardless of its performance with other emulators. (you might post your system specs, or link to your netbook).
regardless of that though, looking at your config file...
you might try turning off 'waitvsync' (change the 1 to 0). you may get tearing but it might improve speed.
you could also try turning filter(ing) off.

if that doesn't help (enough), (you can re-enable vsync then) switch video from opengl to software. you should be able to get much more speed with the software renderer but it means sacrificing a lot of graphical bells and whistles (things may not look as nice).
Thanks man for dealing with me, so I've tried both options, and I get little to no change, also, using the software renderer causes audio burps, werid.

Here are the specs for my netbook if that'll help any,
_Acer Aspire One D250_
Atom N270 1.6GHz
1GB RAM
160GB HDD

Also, another odd thing, when using Final Burn Alpha in wine (though windowed to around 320x???) it gives me 60 fps. Using mame windowed around that size still gives me the constant rate of 40fps.

---

### Post by disturbedite on 2011-02-20
if you get audio problems, try turning up the audio latency.

(everything i'm about to say is implied at full speed). your netbook is sufficient to run a lot of (older) mame games, based on your onboard graphics capability. the 1GB of RAM is woefully insufficient for playing a lot of newer games (again, at full speed). the onboard graphics combined with the amount of RAM won't cut it playing pretty much all newer 3D games.

and comparing mame to other emulators or games is useless. it's like comparing apples and grenades. mame is entirely different kind of animal.

sorry. knowing what i know, i would NEVER buy a netbook and expect it to be a source of playing modern games. better to go with a laptop if you wanna play games.

---

