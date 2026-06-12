---
title: "[SOLVED] xmame- I give up"
date: 2008-03-24
forum: Gaming &amp; Leisure
---

### Post by the2ndgenesis on 2008-03-24
Sup everyone, recent convert from XP and huge MAME fan here. I apologize for the noobish and whining tone this thread is about to take, but I'm afraid I'm at the end of my rope.

After wrestling with xMAME and various packages for about three hours last night I still am not able to get the damn thing to run. Installing a GUI to ease the transition didn't seem to help either (kxMAME and gxMAME didn't seem to want to work for me, in keeping with what I've read about them). I've read as many threads as I can regarding xMAME and the proper installation thereof, but I really can't take the tedium of going through the whole installation process again.

Basically, I want to start my MAME life on Linux with a clean slate: everything smacking of xMAME has been removed from this computer. I'm looking for a clean install of any MAME client that will work on this computer, with a GUI or otherwise. Any help anyone could offer me on this subject would be much appreciated, and again, I apologize for the complaint.

(If it helps, my computer's specs can be found in the attached image.)

---

### Post by solitaire on 2008-03-24
I ran Mame without the GUI. 
I find for the most part it's not really required.

What errors were you getting when you try and run a game?
That may help fixing the problem.

---

### Post by BigSilly on 2008-03-24
Have you tried [SDLMame for Ubuntu?]("http://wallyweek.altervista.org/") It's constantly updated alongside MAME itself, and just the same as the Windows variant. Xmame is quite old now. Give it a try, and if you need any help let us know. I will say though, that SDLMame helped me switch completely from Windows to Linux. It's that good!

---

### Post by disturbedite on 2008-03-24
don't use xmame, its dead & has been since mame 0.106.  mame is now at 0.124, so you can how outdated xmame is.

sdlmame is the program to use; it is still actively developed.  it is in hardy already, but if you're not running hardy, you can grab ubuntu packages at the link BigSilly posted above ^.

use kxmame with it.  don't install the kxmame package in the ubuntu repo, its outdated & doesn't work with sdlmame.
install DoktorSeven's kxmame package here:
[http://sdcofer.googlepages.com/home](http://sdcofer.googlepages.com/home)

---

### Post by the2ndgenesis on 2008-03-24
OK, I've installed SDLMAME and DoktorSeven's package. My problem now is that I think my directories are configured incorrectly (e.g: I've told the program to look in my old ROM folder for games, but nothing is available when I refresh the game list). 

I realize that a lot of these are pointing to a non-functional xMAME directory, but I'm still lost as to where to set them for SDLMAME... any advice you could offer would be a great help.

Attached are screenshots of my current directories/paths.

---

### Post by BigSilly on 2008-03-24
Did you not try out SDLMame? It looks like you are still trying to configure XMame from your shots. If you do have sdlmame installed, you'll need to edit your mame.ini file in order to point it at your roms. Open a terminal and paste this in -

```
sudo gedit /etc/sdlmame/mame.ini
```

Enter your password, and this should bring up your text file. Mine looks like this - 

```
#
# CORE CONFIGURATION OPTIONS
#
readconfig                1

#
# CORE SEARCH PATH OPTIONS
#
rompath                   /media/sda5/MAME Stuff/roms
samplepath                /media/sda5/MAME Stuff/samples
artpath                   /media/sda5/MAME Stuff/artwork
ctrlrpath                 /etc/sdlmame/ctrlr
inipath                   /etc/sdlmame
fontpath                  /var/games/sdlmame;/usr/share/games/sdlmame

#
# CORE OUTPUT DIRECTORY OPTIONS
#
cfg_directory             /var/games/sdlmame/cfg
nvram_directory           /var/games/sdlmame/nvram
memcard_directory         /var/games/sdlmame/memcard
input_directory           /var/games/sdlmame/inp
state_directory           /var/games/sdlmame/sta
snapshot_directory        /var/games/sdlmame/snap
diff_directory            /var/games/sdlmame/diff
comment_directory         /var/games/sdlmame/comments

#
# CORE FILENAME OPTIONS
#
cheat_file

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
throttle                  1
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
multithreading            0
sdlvideofps               0

#
# VIDEO OPTIONS
#
video                     opengl
numscreens                1
window                    0
keepaspect                1
unevenstretch             1
effect                    none
centerh                   1
centerv                   1
waitvsync                 0
yuvmode                   none

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
keymap                    0
keymap_file

#
# SDL JOYSTICK MAPPING
#
remapjoys                 1
remapjoyfile              /etc/sdlmame/joymap.dat

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

I've not done a lot of alterations, but as you can see, I'm pointing it at my spare partition (sda5), where my roms are stored. When you've done that, type ```
sdlmame
``` into a terminal to run it and see where you are. It should list all the roms you have if it's worked.

You can make a launcher if you wish, instead of typing sdlmame into a terminal, but this will get you started if you need help.

Let us know how you get on anyway. It all seems really complicated, but it's not, honest!

---

### Post by the2ndgenesis on 2008-03-24
Thanks, Big Silly, that seemed to work!

All that's left now is to make sure my ROMs are compatible and in the right directory. I think this thread can be closed now.

---

### Post by BigSilly on 2008-03-25
Really glad that worked for you. I absolutely adore SDLMame, and as I say it was instrumental in helping me switch completely to Linux from Windows. You can't whack a bit of SF2 Turbo!

Have fun. :)

---

### Post by disturbedite on 2008-03-25
> **the2ndgenesis said:**
> Thanks, Big Silly, that seemed to work!

All that's left now is to make sure my ROMs are compatible and in the right directory. I think this thread can be closed now.
also, as i said before, xmame's last version was 0.106, (sdl)mame is at 0.124.  (sdlmame is simply mainline mame ported to sdl, so it stays current to the version of mainline mame).  if your romset is 0.106 or even older, a lot games prolly will not work & you will need to upgrade your romset to 0.124 to take full advantage of the newest mame version.

---

### Post by _Stevie_ on 2008-04-06
err, i have a bit of a problem with playing the roms.
i got some bunch of roms in zip format when i unpack them, there are
a lot of files with numbers, bins and roms inside. how do i launch those roms? 
i already tried them in zipped and unpacked condition.
any tips?

---

### Post by the2ndgenesis on 2008-04-07
Stevie: MAME uses the roms in their native zipped form. You don't have to touch them unless a rom is missing a file you need to add to the .zip.

Have you made sure that your directories are properly set and that the version of MAME you're using is compatible with your roms?

---

### Post by _Stevie_ on 2008-04-08
Hey the2ndgenesis!

Thanks for your reply.

> **the2ndgenesis said:**
> Stevie: MAME uses the roms in their native zipped form. You don't have to touch them unless a rom is missing a file you need to add to the .zip.

I actually thought so, SNES and other roms work the same way. But I wasn't sure anymore, since none of the roms was found.

> **the2ndgenesis said:**
> 
Have you made sure that your directories are properly set and that the version of MAME you're using is compatible with your roms?

Actually yes, I tried it on another machine with kxmame and put a game in zip-format in the appropriate folder. Then I re-scanned the games, but this
particular one couldn't be found. Then I deleted it and put another one in the folder and that one could be found. I have the feeling, that some of the roms
have the wrong zip name and therefore can#t be found. That's a bit odd :(
Can anyone confirm this?

---

### Post by disturbedite on 2008-04-08
your roms may be outdated.  people should be using sdlmame 0.124, which means that their romset should also be from 0.124.

---

### Post by _Stevie_ on 2008-04-08
hmm that explains it. my romset is called v0.103.
i didnt know the roms are getting modified for each mame version!

---

### Post by disturbedite on 2008-04-09
yes they do and they always have been.

---

### Post by _Stevie_ on 2008-04-09
thanks for the info :D
seems working well now

---

### Post by disturbedite on 2008-04-09
no prob.

---

### Post by SunnyRabbiera on 2008-04-16
My question is... how do I get my joystick to work for the games, it seems not to work.
Do I have to use the keboard or something?
I rather use my controller if possible.

---

### Post by disturbedite on 2008-04-16
i'm pretty sure you have to map the keys you want in the config like with almost every emulator!  its easiest to do in the ingame menu.  (map the keys in the Input (general) section).

---

### Post by SunnyRabbiera on 2008-04-26
alright, but I still cant use kxmame as a frontend to sdlmame, I did what was said on the first page but it did not work... I still get this error:
No good rom's found.
Please make sure, you have configured your ini files and directories properly.
SDLMAME Hint: Configure your ~/.mame/sdlmame.ini for your executable'

---

### Post by SunnyRabbiera on 2008-04-29
hello anybody?

---

### Post by Crandes on 2008-04-29
> **SunnyRabbiera said:**
> alright, but I still cant use kxmame as a frontend to sdlmame, I did what was said on the first page but it did not work... I still get this error:
No good rom's found.
Please make sure, you have configured your ini files and directories properly.
SDLMAME Hint: Configure your ~/.mame/sdlmame.ini for your executable'

Hello,

install sdlmame-tools which creates default config to /etc/sdlmame/mame.ini. Edit the file for your rom directories, launch kxmame and voila. Atleast that did the trick for me.

Another thing which caused me some hairloss was spaces in the path like /path/Mame/Roms 0.124/. I did a symlink 'ln -s /path/Mame/Roms 0.124/ ~/mamedir' and used that in the mame.ini and kxmame started to find roms.

---

