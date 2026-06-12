---
title: "sdlmame cpu usage problems, very strange"
date: 2009-07-03
forum: Gaming &amp; Leisure
---

### Post by mocha on 2009-07-03
I'm having a lot of problems with sdlmame from the Jaunty repo.  It always uses 100% to 200% CPU on my dual core.  The usage fluctuates as a game is in progress.  This leads to jitters and sound stuttering.  I'm using an nvidia card and opengl rendering with vsync enabled.  I don't understand why so much CPU is being consumed for games that I used to play just fine on a 233 MHz AMD box 10 years ago.  If anyone out there is not having this problem would you mind posting your mame.ini as well as a brief description of your video card and and special xorg.conf setting such as "useevents" or "triplebuffer".  Thanks.

---

### Post by BoyOfDestiny on 2009-07-03
In your mame.ini, make sure video is set to opengl
```
#
# VIDEO OPTIONS
#
video                     opengl
```
Scroll down to opengl settings, set filter to 0
```
#
# OpenGL-SPECIFIC OPTIONS
#
filter                    0
```

---

### Post by mocha on 2009-07-03
Thanks, but that doesn't help, it also makes the video look ugly.

---

### Post by BoyOfDestiny on 2009-07-03
Odd that is makes it look ugly, perhaps its the uneven stretch setting, unless being pixely is ugly... 

Anyway, I don't have an nvidia card, are you using proprietary drivers for yours? Does toggling vsync make any difference? If the drivers are the culprit, you could try software rendering.

Set video to soft
or try setting scalemode to yuy2 to use xv for scaling...

These are all in the Video options of the ini...

Sorry I can't really troubleshoot this, I was hoping what worked for my bog standard onboard intel would help you.

---

### Post by Melcar on 2009-07-03
SDLMame always uses 100% of one of my cores and at times sound skips (usually when I have other things running in the background).

---

### Post by mocha on 2009-07-04
I've been playing with various settings and I *think* I may have found the problem.  I believe the extreme CPU usage and bizarre cycling up and down of the CPU (like starting at 50%, then 100%, then 200%, then back to 100%, and so on) has something to do with Pulseaudio.

I've been running sdlmame tonight exclusively with SDL_AUDIODRIVER="esd" instead of the Jaunty default SDL_AUDIODRIVER="alsa".  If someone else would like to test this, add the following to the end of your ~/.bashrc and logout/login.

```
export SDL_AUDIODRIVER="esd"
```

Or if you are using an sdlmame frontend and run it from your menu, change the launcher to the following:

```
env SDL_AUDIODRIVER="esd" frontend_binary
```

If you run sdlmame from the command line, when you run it with the -verbose switch, you should see in the terminal a line which indicates esd being used as the sdl audio driver.

I haven't done enough tests with enough games to satisfy myself that this is the fix, however, I can say that after this change I have not yet seen the CPU consumption issues anymore.  Quite the contrary, simpler/older games are only consuming around 30% steady, and only the higher emulation intensive games are consuming 100% (one core) and it stays steady.  There is no more video jitters or sound stuttering either.

I'd appreciate others feedback.  For reference here is my mame.ini, minus my machine specific file locations:

```
#
# CORE STATE/PLAYBACK OPTIONS
#
state                     
autosave                  1
playback                  
record                    
mngwrite                  
aviwrite                  
wavwrite                  
snapname                  %g/%i
snapsize                  auto
snapview                  internal

#
# CORE PERFORMANCE OPTIONS
#
autoframeskip             1
frameskip                 0
seconds_to_run            0
throttle                  1
sleep                     0
speed                     1.0
refreshspeed              0

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
flicker                   0.26

#
# CORE SOUND OPTIONS
#
sound                     1
samplerate                48000
samples                   1
volume                    -12

#
# CORE INPUT OPTIONS
#
coin_lockout              1
ctrlr                     
mouse                     1
joystick                  1
lightgun                  1
multikeyboard             0
multimouse                0
steadykey                 1
offscreen_reload          0
joystick_map              auto
joystick_deadzone         0.3
joystick_saturation       0.85

#
# CORE INPUT AUTOMATIC ENABLE OPTIONS
#
paddle_device             mouse
adstick_device            keyboard
pedal_device              keyboard
dial_device               mouse
trackball_device          mouse
lightgun_device           mouse
positional_device         keyboard
mouse_device              mouse

#
# CORE DEBUGGING OPTIONS
#
log                       0
verbose                   0
update_in_pause           1
debug                     0
debugscript               

#
# CORE MISC OPTIONS
#
bios                      
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
sdlvideofps               0

#
# VIDEO OPTIONS
#
video                     opengl
numscreens                1
window                    1
maximize                  1
keepaspect                1
unevenstretch             1
effect                    aperturescan1024
centerh                   1
centerv                   1
waitvsync                 1
scalemode                 none

#
# OpenGL-SPECIFIC OPTIONS
#
filter                    1
prescale                  1
gl_forcepow2texture       0
gl_notexturerect          1
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
# SDL KEYBOARD MAPPING
#
keymap                    0
keymap_file               keymap.dat

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
sixaxis                   0

#
# SDL LOWLEVEL DRIVER OPTIONS
#
videodriver               auto
audiodriver               auto
gl_lib                    auto
```

As you can see, I have audiodriver set to auto since I set the environment variable instead to control it.  I did this becuase the frontend gmameui doesn't parse the mame.ini file.

Also for reference, I'm using an nvidia 9500GT card with the 180.53 binary driver, opengl vsync and flipping enabled.  In case anyone is wondering, setting SDL_AUDIODRIVER="esd" doesn't seem to have any negative effects, applications like sdlmame still show up under the pulseaudio volume manager and can be individually controlled.

Finally, I'm not sure if this has any effect, but in my xorg.conf, I have the following nvidia specific options set:

```
Option         "UseEvents"          "True"
Option         "TripleBuffer"       "True"
```

I also have the Composite extension set to disabled, but that's because I'm using VDPAU video rendering with mplayer and MythTV.  I'm using the Gnome/Metacity desktop environment.

---

### Post by alex34567 on 2009-07-24
Thank you. Ever since I installed Jaunty, I've been fiddling with options, trying to get CPU usage down to a reasonable level. I replaced libsdl1.2debian-alsa with libsdl1.2debian-all and ran from the command line: env SDL_AUDIODRIVER="esd" sdlmame [options] and things are now just as they should be. Cheers.

---

### Post by mocha on 2009-07-27
alex,

Good to see I'm not the only one on earth that had this problem, now there are 2 of us!  Seriously, setting the driver to esd has worked great for me since making my post about it.  I think probably everyone is affected by this but there aren't many sdlmame users or they are "casual" and simply don't notice the problem.

---

### Post by apienk01 on 2009-09-28
Thanks, you helped me as well. So there are 3 of us :)

Strangely enough, as far as I know, native esd is not used anymore in Jaunty, and is just emulated by pulseaudio. So theoretically it shouldn't be much different from pulse or alsa. But actually it is, quite dramatically. Thanks! :KS

Now I can go back to Darkstalkers...

---

### Post by manysounds on 2009-10-23
Hello, I have this issue (I think) on my EEEpc900 with 9.1Karmic.
How do you implement this workaround?
Sorry I'm not n00b but this really isn't my field at all.

---

### Post by williamts99 on 2009-10-24
Same problem here but now running 9.10

Solution is to install libsdl1.2debian-pulseaudio

sudo apt-get install libsdl1.2debian-pulseaudio

From the following thread:
[http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=54940](http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=54940)

Best Regards,
Williamts99

---

### Post by kimme on 2009-10-24
Thanks for this tip on using mame on Ubuntu.

---

