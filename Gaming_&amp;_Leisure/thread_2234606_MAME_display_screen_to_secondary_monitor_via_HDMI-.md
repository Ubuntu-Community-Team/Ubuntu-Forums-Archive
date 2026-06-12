---
title: "MAME display screen to secondary monitor via HDMI-0"
date: 2014-07-15
forum: Gaming &amp; Leisure
---

### Post by Heinrich_Evers on 2014-07-15
Okay, so here it goes...


I decided to migrate over to Ubuntu 14.04 Gnome 3 from a very stable windows build that I was using for an XBMC media center. I figured the stability and added XBMC support would be nice.

Everything went over fine with the exception of my emulation collection. The problem that I'm having is that I have two physical monitors connected to this machine, a 22" for my primary and a 46" smart tv for my secondary display.

What I'd like to do is get MAME to load onto my secondary display when I execute it in XBMC. The XBMC settings are fine so I know it's my MAME config or my actual Linux config thats causing the problems.

I'd like to keep my 22" screen as my primary display for everything else and I'd like to make the secondary display for everything XBMC related including MAME.

I use dual-SLI Nvidia GTX660 OC for my graphics cards and I'd like to do this without creating a screen1 for the secondary display as I don't know linux well enough to configure a seperate session login for the secondary screen.

Below is my current mame.ini configuration that is stored in my /home/user/.mame folder. Any help would be greatly appreciated!

&#65279;#
# CORE CONFIGURATION OPTIONS
#
readconfig                1
writeconfig               0

#
# CORE SEARCH PATH OPTIONS
#
rompath                   $HOME/mame/roms;/usr/local/share/games/mame/roms;/usr/share/games/mame/roms;/media/heinrich/MyPassport2TB/XBMConsole/MAME/roms
hashpath                  /usr/share/games/mess/hash
samplepath                $HOME/mame/samples;/usr/local/share/games/mame/samples;/usr/share/games/mame/samples
artpath                   $HOME/mame/artwork;/usr/local/share/games/mame/artwork;/usr/share/games/mame/artwork
ctrlrpath                 /etc/mess/ctrlr
inipath                   $HOME/.mame;/etc/mame
fontpath                  .
cheatpath                 $HOME/mame/cheat;/usr/local/share/games/mame/cheat;/usr/share/games/mame/cheat
crosshairpath             $HOME/mame/crosshair;/usr/local/share/games/mame/crosshair;/usr/share/games/mame/crosshair

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
aviwrite                  
wavwrite                  
snapname                  %g/%i
snapsize                  auto
snapview                  internal
statename                 %g
burnin                    0

#
# CORE PERFORMANCE OPTIONS
#
autoframeskip             0
frameskip                 0
seconds_to_run            0
throttle                  1
sleep                     1
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
use_cpanels               1
use_marquees              1

#
# CORE SCREEN OPTIONS
#
brightness                1.0
contrast                  1.0
gamma                     1.0
pause_brightness          0.65
effect                    none

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
coin_lockout              1
ctrlr                     
mouse                     1
joystick                  1
lightgun                  0
multikeyboard             0
multimouse                0
steadykey                 0
ui_active                 0
offscreen_reload          0
joystick_map              auto
joystick_deadzone         0.3
joystick_saturation       0.85
natural                   0
joystick_contradictory    0
coin_impulse              0

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
update_in_pause           0
debug                     0
debugscript               
debug_internal            0

#
# CORE MISC OPTIONS
#
drc                       1
drc_use_c                 0
bios                      
cheat                     0
skip_gameinfo             0
uifont                    default
ramsize                   
confirm_quit              0
ui_mouse                  0
autoboot_command          
autoboot_delay            2
autoboot_script           
http                      0
http_port                 8080
http_path                 /usr/share/games/mess/web/

#
# DEBUGGING OPTIONS
#
oslog                     0
watchdog                  0

#
# PERFORMANCE OPTIONS
#
multithreading            1
numprocessors             auto
sdlvideofps               0
bench                     0

#
# VIDEO OPTIONS
#
video                     opengl
numscreens                1
window                    0
maximize                  1
keepaspect                1
unevenstretch             1
centerh                   1
centerv                   1
waitvsync                 0
syncrefresh               0
scalemode                 none

#
# OpenGL-SPECIFIC OPTIONS
#
filter                    1
prescale                  1
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

#
# PER-WINDOW VIDEO OPTIONS 
#
screen                    HDMI-0
aspect                    auto
resolution                auto
view                      auto
screen0                   HDMI-0
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
audio_latency             2

#
# SDL KEYBOARD MAPPING
#
keymap                    0
keymap_file               keymap.dat
uimodekey                 SCRLOCK

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

---

### Post by dannyboy79 on 2014-07-16
you need to figure out what mame thinks your secondary display name is and then change the setting within the # PER-WINDOW VIDEO OPTIONS. that's my guess anyway, i don't use mame but thought i'd take a stab at helping

---

### Post by Heinrich_Evers on 2014-07-25
> **dannyboy79 said:**
> you need to figure out what mame thinks your secondary display name is and then change the setting within the # PER-WINDOW VIDEO OPTIONS. that's my guess anyway, i don't use mame but thought i'd take a stab at helping


It's HDMI-0; however,  my xorg.conf merges both monitors as a single desktop for twinview which makes starting the emulator to the secondary impossible to do unless I name it as my primary monitor. I did try to configure it as a second screen and enable xinerama from nvidia-settings, but I haven't been successful in getting two independant displays for one session that can perform twinview operations, which is what I'd like to do. 

I can think of more applications to use this for other than emulation gaming. I also use XBMC as my DLNA server for sharing my videos and PVR functionality to my other televisions in the house via my wireless network. It would be nice to be able tohave XBMC running in fullscreen mode on the secondary display as well.

---

