---
title: "Mupen64+ 1.99.4 GUI frontend (Cutemupen?)"
date: 2011-02-12
forum: Emulators
---

### Post by mips on 2011-02-12
Anybody know (has used it) of a good GUI frontend to Mupen64Plus v1.99.4? Looking for something that will handle controller config.

Also how does one configure CuteMupen, I have no idea where to point it for all the folders it wants except for the rom folder?
Stuff like core library file, data directory etc.

---

### Post by mips on 2011-02-12
Ok, think I figured it out so I'll make a mini guide for 64-bit users, 32-bit should be the same.

First install Mupen64Plus **v1.5** from the repos, there is method to this madness!
```
sudo apt-get install mupen64plus
```


Open Mupen64+, go Options -> Configure --> Plugins Tab --> Select "blight's SDL input plugin" --> Click Config and setup your gamepad/controller --> Apply changes & test that it works in a few games, exit mupen64+


Now we have to backup that config file for the gampad/controller.
```
cp ~/.config/mupen64plus/blight_input.conf ~/Desktop

```

Verify the file is on your desktop and that it contains the settings for you controller.


Now we can uninstall mupen64+,
```
sudo apt-get purge mupen64plus
```

Check to see that the config files were removed as well, if they are still there you can do,
```
rm -r ~/.config/mupen64plus
```

So why did we just go through this whole exercise? Well currently there is no GUI frontend you can use to setup your gamepad/controller for Mupen64+ v1.99.4. The application itself no longer has a GUI (cli only) and the available frontends out there do not support configuration of the controller as yet so we need a backup copy of our v1.5 config file for later use.




Lets get on to installing mupen64+ v1.99.4

First lets add the developers PPA to our repos,
```
sudo add-apt-repository ppa:sven-eckelmann/ppa-mupen64plus
```


Next we do an update and install the app,
```
sudo apt-get update
sudo apt-get install mupen64plus
```


Run mupen64+ so it creates a config folder and file,
```
mupen64plus
```



Next we install [CuteMupen]("http://sourceforge.net/projects/cutemupen/") front end, **[COLOR="Red"]get the 32-bit version if you are using 32-bit OS, check for newer files![/COLOR]** [http://sourceforge.net/projects/cutemupen/files/](http://sourceforge.net/projects/cutemupen/files/)
```
wget http://sourceforge.net/projects/cutemupen/files/0.1.0/cutemupen-linux64-0.1.0.tar.bz2
tar xvfj cutemupen-linux64-0.1.0.tar.bz2
```


Add CuteMupen to your menu,
Right click on Applications toolbar --> Edit Menus --> Games --> New Item
Type: Application
Name: CuteMupen
Cammand: /home/*username*/cutemupen-linux64-0.1.0/cutemupen


Open CuteMupen, it's going to prompt you for some default files & folder locations.

**Core libabrary file:** /usr/lib/libmupen64plus.so.2
**Plugins:** /usr/lib/mupen64plus   (or /home/**username**/.config/mupen64plus/plugins and copy the contents of /usr/lib/mupen64plus into it which is what I have done.)
**Data:** /home/**username**/.config/mupen64plus/data
**Config:** /home/**username**/.config/mupen64plus
**ROMs:** Wherever you have your ROM files stored.
If the folders don't exist create them.


Quit and restart CuteMupen. You can now setup your plugins and their setting to suite your needs.


If your controller/gamepad does not work out of the box you will have to edit your /usr/share/mupen64plus/InputAutoCfg.ini file with information from the ~/Destop/blight_input.conf file we backed up earlier.

Here are some examples that show how,
[http://www.emutalk.net/showthread.php?t=49731](http://www.emutalk.net/showthread.php?t=49731)
[http://code.google.com/p/mupen64plus/wiki/ControllerSetup](http://code.google.com/p/mupen64plus/wiki/ControllerSetup)


This post was compiled with info taken from:
[http://sourceforge.net/project/screenshots.php?group_id=308021&ssid=124559](http://sourceforge.net/project/screenshots.php?group_id=308021&ssid=124559)
[http://www.emutalk.net/forumdisplay.php?f=113](http://www.emutalk.net/forumdisplay.php?f=113)
[http://code.google.com/p/mupen64plus/w/list](http://code.google.com/p/mupen64plus/w/list)

---

### Post by mips on 2011-02-13
Just some feedback, this has worked out really well, I've been playing N64 games for the last two days now :D

Wish they sold the N64 here back in the day. I find the games better than most PSX games.

This is really fun, who says gaming on linux is boring! :D

---

### Post by ubuntu-freak on 2011-03-09
Cheers for posting.

Edit: Are you able to edit the Glide64 video settings in CuteMupen? I can edit all but that one. A message pops up stating "Couldn't find parameters in Video-Glide64 section."

Edit 2: Never mind, sorted it now. Glide64 options weren't in the mupen64plus.cfg file, so I used the "mupen64plus --saveoptions" command to fill it with more options and then did it again after changing the default video plugin to Glide64, which then added Glide64 options to the config file. Nice.

---

### Post by mips on 2011-03-10
> **ubuntu-freak said:**
> Cheers for posting.

Edit: Are you able to edit the Glide64 video settings in CuteMupen? I can edit all but that one. A message pops up stating "Couldn't find parameters in Video-Glide64 section."

Edit 2: Never mind, sorted it now. Glide64 options weren't in the mupen64plus.cfg file, so I used the "mupen64plus --saveoptions" command to fill it with more options and then did it again after changing the default video plugin to Glide64, which then added Glide64 options to the config file. Nice.

Hi,

Could you please give a more detailed description of what you have done, ie full commands you executed.

Thanks

---

### Post by ubuntu-freak on 2011-03-10
> **mips said:**
> Hi,

Could you please give a more detailed description of what you have done, ie full commands you executed.

Thanks

Well, at first I just executed the command:

**mupen64plus --saveoptions ~/Games/Hexen.n64**

The config file is quite empty for some reason by default, plus a game has to be started with the "--saveoptions" command for Mupen64+ to send all the options available to the config file.

However, because the video plugin was set as Rice, no Glide64 options were sent to the config file, so I still couldn't edit them in CuteMupen. I went into the config file and changed the video plugin to "mupen64plus-video-glide64.so" and saved the file. I executed the "--saveoptions" command again and Mupen finally sent the Glide64 options to the config file.

If anyone finds the Rice plugin to be slow, try setting the "ScreenUpdateSetting" to 7 instead of 1. It speeds up Rice but didn't really cause any problems in the game I tested.

---

### Post by ubuntu-freak on 2011-03-12
Might as well post what I've discovered here, in case it helps anyone.

First of all, if your audio is choppy and slow, don't waste time adjusting the primary audio buffers, cos' it won't help. However, changing the secondary buffer to 512 DID help with my sound issues somewhat. Adjusting the video options and using Glide64 was the most helpful though.

Here's the best Glide64 options I came up with:

[Video-Glide64]

# Card ID
card_id = 0
# Use custom INI settings
custom_ini = True
# Vertical sync
vsync = True
# FPS counter
show_fps = True
# Detect CPU writes
detect_cpu_write = False
# Buffer clear on every frame
buff_clear = False
# Framebuffer read every frame
fb_read_always = False
# Framebuffer read alpha
fb_read_alpha = False
# Smart framebuffer
fb_smart = False
# Get framebuffer info
fb_get_info = False
# Depth buffer render
fb_render = False
# Use framebuffer objects
fbo = False

Setting anything currently "False" to "True" (after setting "custom_ini" to "False") will override the custom Glide.ini options for supported games, which is useful for troubleshooting when you have a problematic one. I've left the eye-candy options out cos' I think they're unnecessary, as Glide64 makes smart default choices for those. The options above may help if the custom ones aren't quite right. "fbo = True" may help with some games and "fb_read_always" may help with others, but only if your GPU is powerful. It's pretty pointless and slow for me. It's a good idea for "fb_get_info" to be enabled if you disable the custom option too.

Glide64 was the fastest plugin for me, the others were slow and lacked game compatibility.

Hope this info will be useful to someone.

---

### Post by mips on 2011-03-13
> **ubuntu-freak said:**
> Might as well post what I've discovered here, in case it helps anyone.

Thanks, definitely. Would encourage others to do the same so we can improve the Mupen64+ experience.

---

### Post by ubuntu-freak on 2011-03-13
> **mips said:**
> Thanks, definitely. Would encourage others to do the same so we can improve the Mupen64+ experience.

Updated it a bit. Forgot to mention that changing the secondary audio buffer to 512 from the default 2048 did actually help improve the sound.

---

### Post by mips on 2011-03-13
> **ubuntu-freak said:**
> Updated it a bit. Forgot to mention that changing the secondary audio buffer to 512 from the default 2048 did actually help improve the sound.

Are your sound problems of a general nature or for specific games?
I have not experienced sound issues yet but then again I've only really been playing Rayman 2.

---

### Post by ubuntu-freak on 2011-03-13
You know what? Forget the options I posted.

I wondered why Glide64 was painfully slow without me adding those settings to the config file in ~/.config/mupen64plus/mupen64plus.cfg, so I checked the Glide64.ini file in /usr/share/mupen64plus to try and figure it out. At first I thought that "fb_read_always" was on for everything, cos' every game was so slow without the above settings, but that wasn't the answer. I noticed something missing in the Glide.ini file and got curious. Turns out the only option I need in the Glide64 video options (mupen64plus.cfg) is "card_id = 0" and "custom_ini = True". That's all. Every game ran fine after just adding that one option, except for the ones with currently unfixed bugs of course. Now I can let the Glide64.ini use it's custom fixes for problematic games without me having to muck around with different options.

Not sure if it's worth keeping those settings/options posted on the first page now.

Edit: I've slimmed down the settings/options on the first page now.

---

### Post by ubuntu-freak on 2011-03-13
> **mips said:**
> Are your sound problems of a general nature or for specific games?
I have not experienced sound issues yet but then again I've only really been playing Rayman 2.

Not quite sure why I have sound issues. My graphics card isn't even a proper graphics card, just an integrated Intel one. I've had static on some sounds in general, which I think is a bug with the Linux kernel, possibly not PulseAudio. But yeah, some games are worse than others. The music in Wave Race sounds fine, but usually the music in roms sounds crap on my system. Sound effects have some static.

---

### Post by mips on 2011-03-30
Anybody know if you can use hi-res textures with Glide plugin?

Rice plugin is giving me problems:

```
xxxx@obelix:/media/160GB_WD/emulation/roms/n64$ mupen64plus "Legend of Zelda, The - Ocarina of Time (U) (V1.2) [!].z64"
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Mupen64Plus Console User-Interface Version 1.99.4

UI-console: attached to core library 'Mupen64Plus Core' version 1.99.4
            Includes support for Dynamic Recompiler.
Core: Goodname: Legend of Zelda, The - Ocarina of Time (U) (V1.2) [!]
Core: Name: THE LEGEND OF ZELDA
Core: MD5: 57A9719AD547C516342E1A15D5C28C3D
Core: CRC: 693ba2ae b7f14e9f
Core: Imagetype: .z64 (native)
Core: Rom size: 33554432 bytes (or 32 Mb or 256 Megabits)
Core: Version: 1449
Core: Manufacturer: 43000000
Core: Country: Unknown (0x245)
UI-Console: Cheat codes disabled.
UI-console: using Video plugin: 'Mupen64Plus OpenGL Video Plugin by Rice' v1.99.4
UI-console: using Audio plugin: 'Mupen64Plus SDL Audio Plugin' v1.99.4
Input: N64 Controller #1: Using SDL joystick 0 ('USB Gamepad ')
UI-console: using Input plugin: 'Mupen64Plus SDL Input Plugin' v1.99.4
UI-console: using RSP plugin: 'Hacktarux/Azimer High-Level Emulation RSP Plugin' v1.99.4
Input: N64 Controller #1: Using SDL joystick 0 ('USB Gamepad ')
Input: 1 controller(s) found, 1 plugged in and usable in the emulator
Input Warning: No rumble supported on N64 joystick #1
Input: Mupen64Plus SDL Input Plugin version 1.99.4 initialized.
Video: SSE processing enabled.
Video: Found ROM 'THE LEGEND OF ZELDA', CRC aea23b699f4ef1b7-45
Video: Enabled hacks for game: 'THE LEGEND OF ZELDA'
Video: Texture loading option is enabled. Finding all hires textures
Video Warning: RGB and alpha texture size mismatch: /home/xxxx/.local/share/mupen64plus/hires_texture/THE LEGEND OF ZELDA/HUD/Magic Meter/THE LEGEND OF ZELDA#54492A28#3#1_a.png
Video Error: GetImageInfoFromFile() error: couldn't read first 8 bytes of file '/home/xxxx/.local/share/mupen64plus/hires_texture/THE LEGEND OF ZELDA/Garde Gerudo/THE LEGEND OF ZELDA#0A9E15D6#4#1_all.png'
Video Warning: Cannot get image info for file: THE LEGEND OF ZELDA#0A9E15D6#4#1_all.png
Video Warning: RGB and alpha texture size mismatch: /home/xxxx/.local/share/mupen64plus/hires_texture/THE LEGEND OF ZELDA/Fontaine/THE LEGEND OF ZELDA#F2F31CB3#3#0_a.png
Video: Initializing OpenGL Device Context.
Core: Setting 32-bit video mode: 1440x1026
Video: Using OpenGL: NVIDIA Corporation - GeForce 9600 GT/PCI/SSE2 : 3.3.0 NVIDIA 260.19.06
Video: OpenGL Combiner: Fragment Program
Audio: Initializing SDL audio subsystem...
/dev/mixer: : No such file or directory
Core: Starting R4300 emulator: Dynamic Recompiler
Core: R4300: starting 64-bit dynamic recompiler at: 0x7f21a64e1200
/dev/mixer: : No such file or directory
/dev/mixer: : No such file or directory
*** glibc detected *** mupen64plus: malloc(): memory corruption: 0x00007f21a72daac0 ***
======= Backtrace: =========
/lib/libc.so.6(+0x774b6)[0x7f21a3cbd4b6]
/lib/libc.so.6(+0x7b55f)[0x7f21a3cc155f]
/lib/libc.so.6(__libc_calloc+0xc4)[0x7f21a3cc4254]
/usr/lib/nvidia-current/libnvidia-glcore.so.260.19.06(+0xefbc29)[0x7f219f1b0c29]
/usr/lib/nvidia-current/libnvidia-glcore.so.260.19.06(+0xefbfcc)[0x7f219f1b0fcc]
/usr/lib/nvidia-current/libnvidia-glcore.so.260.19.06(+0xd8597f)[0x7f219f03a97f]
/usr/lib/nvidia-current/libnvidia-glcore.so.260.19.06(+0xd8fb7e)[0x7f219f044b7e]
/usr/lib/mupen64plus/mupen64plus-video-rice.so(+0x36e80)[0x7f219a73be80]
/usr/lib/mupen64plus/mupen64plus-video-rice.so(+0x54194)[0x7f219a759194]
/usr/lib/mupen64plus/mupen64plus-video-rice.so(+0x4c3ba)[0x7f219a7513ba]
/usr/lib/mupen64plus/mupen64plus-video-rice.so(+0x4db15)[0x7f219a752b15]
/usr/lib/mupen64plus/mupen64plus-video-rice.so(+0x48cb9)[0x7f219a74dcb9]
/usr/lib/mupen64plus/mupen64plus-video-rice.so(ProcessDList+0x36)[0x7f219a7b19f6]
/usr/lib/mupen64plus/mupen64plus-rsp-hle.so(DoRspCycles+0x1fe)[0x7f2199d6f85e]
/usr/lib/libmupen64plus.so.2(+0x22ac8)[0x7f21a1723ac8]
[0x7f21a6a8f2cd]
======= Memory map: ========
40304000-40306000 r-xs 00000000 08:02 675851                             /tmp/glJ0pKEs (deleted)
4180e000-41874000 rw-p 00000000 00:05 4456                               /dev/zero
7f218c000000-7f218c030000 rw-p 00000000 00:00 0 
7f218c030000-7f2190000000 ---p 00000000 00:00 0 
7f2191992000-7f2191a2d000 r--p 00000000 08:02 528416                     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
7f2191a2d000-7f2191a2e000 ---p 00000000 00:00 0 
7f2191a2e000-7f219222e000 rw-p 00000000 00:00 0 
7f219222e000-7f219222f000 ---p 00000000 00:00 0 
7f219222f000-7f2192a2f000 rw-p 00000000 00:00 0 
7f2192a2f000-7f2196a30000 rw-s 00000000 00:10 246190                     /dev/shm/pulse-shm-462054702
7f2196a30000-7f2198a31000 rw-p 00000000 00:00 0 
7f2198f5d000-7f219915d000 rw-s 15afa6000 00:05 8932                      /dev/nvidia0
7f219915d000-7f219925d000 rw-s 1587b5000 00:05 8932                      /dev/nvidia0
7f219925d000-7f2199262000 r-xp 00000000 08:02 7680                       /usr/lib/libXfixes.so.3.1.0
7f2199262000-7f2199461000 ---p 00005000 08:02 7680                       /usr/lib/libXfixes.so.3.1.0
7f2199461000-7f2199462000 r--p 00004000 08:02 7680                       /usr/lib/libXfixes.so.3.1.0
7f2199462000-7f2199463000 rw-p 00005000 08:02 7680                       /usr/lib/libXfixes.so.3.1.0
7f2199463000-7f219946c000 r-xp 00000000 08:02 7700                       /usr/lib/libXrender.so.1.3.0
7f219946c000-7f219966b000 ---p 00009000 08:02 7700                       /usr/lib/libXrender.so.1.3.0
7f219966b000-7f219966c000 r--p 00008000 08:02 7700                       /usr/lib/libXrender.so.1.3.0
7f219966c000-7f219966d000 rw-p 00009000 08:02 7700                       /usr/lib/libXrender.so.1.3.0
7f219966d000-7f2199676000 r-xp 00000000 08:02 7672                       /usr/lib/libXcursor.so.1.0.2
7f2199676000-7f2199875000 ---p 00009000 08:02 7672                       /usr/lib/libXcursor.so.1.0.2
7f2199875000-7f2199876000 r--p 00008000 08:02 7672                       /usr/lib/libXcursor.so.1.0.2
7f2199876000-7f2199877000 rw-p 00009000 08:02 7672                       /usr/lib/libXcursor.so.1.0.2
7f2199877000-7f2199d6e000 r--p 00000000 08:02 16114                      /usr/lib/locale/locale-archive
7f2199d6e000-7f2199d7a000 r-xp 00000000 08:02 657966                     /usr/lib/mupen64plus/mupen64plus-rsp-hle.so
7f2199d7a000-7f2199f79000 ---p 0000c000 08:02 657966                     /usr/lib/mupen64plus/mupen64plus-rsp-hle.so
7f2199f79000-7f2199f7a000 r--p 0000b000 08:02 657966                     /usr/lib/mupen64plus/mupen64plus-rsp-hle.so
7f2199f7a000-7f2199f7b000 rw-p 0000c000 08:02 657966                     /usr/lib/mupen64plus/mupen64plus-rsp-hle.so
7f2199f7b000-7f2199f8c000 rw-p 00000000 00:00 0 
7f2199f8c000-7f2199f92000 r-xp 00000000 08:02 657965                     /usr/lib/mupen64plus/mupen64plus-input-sdl.so
7f2199f92000-7f219a192000 ---p 00006000 08:02 657965                     /usr/lib/mupen64plus/mupen64plus-input-sdl.so
7f219a192000-7f219a193000 r--p 00006000 08:02 657965                     /usr/lib/mupen64plus/mupen64plus-input-sdl.so
7f219a193000-7f219a194000 rw-p 00007000 08:02 657965                     /usr/lib/mupen64plus/mupen64plus-input-sdl.so
7f219a194000-7f219a2ff000 r-xp 00000000 08:02 12683                      /usr/lib/libsamplerate.so.0.1.7
7f219a2ff000-7f219a4fe000 ---p 0016b000 08:02 12683                      /usr/lib/libsamplerate.so.0.1.7
7f219a4fe000-7f219a4ff000 r--p 0016a000 08:02 12683                      /usr/lib/libsamplerate.so.0.1.7
7f219a4ff000-7f219a500000 rw-p 0016b000 08:02 12683                      /usr/lib/libsamplerate.so.0.1.7
7f219a500000-7f219a504000 r-xp 00000000 08:02 657963                     /usr/lib/mupen64plus/mupen64plus-audio-sdl.so
7f219a504000-7f219a703000 ---p 00004000 08:02 657963                     /usr/lib/mupen64plus/mupen64plus-audio-sdl.so
7f219a703000-7f219a704000 r--p 00003000 08:02 657963                     /usr/lib/mupen64plus/mupen64plus-audio-sdl.so
7f219a704000-7f219a705000 rw-p 00004000 08:02 657963                     /usr/lib/mupen64plus/mupen64plus-audio-sdl.so
7f219a705000-7f219a7c5000 r-xp 00000000 08:02 657970                     /usr/lib/mupen64plus/mupen64plus-video-rice.so
7f219a7c5000-7f219a9c4000 ---p 000c0000 08:02 657970                     /usr/lib/mupen64plus/mupen64plus-video-rice.so
7f219a9c4000-7f219a9c8000 r--p 000bf000 08:02 657970                     /usr/lib/mupen64plus/mupen64plus-video-rice.so
7f219a9c8000-7f219a9da000 rw-p 000c3000 08:02 657970                     /usr/lib/mupen64plus/mupen64plus-video-rice.so
7f219a9da000-7f219aa32000 rw-p 00000000 00:00 0 
7f219aa32000-7f219aa38000 r-xp 00000000 08:02 12565                      /usr/lib/libogg.so.0.7.0
7f219aa38000-7f219ac37000 ---p 00006000 08:02 12565                      /usr/lib/libogg.so.0.7.0
7f219ac37000-7f219ac38000 r--p 00005000 08:02 12565                      /usr/lib/libogg.so.0.7.0
7f219ac38000-7f219ac39000 rw-p 00006000 08:02 12565                      /usr/lib/libogg.so.0.7.0
7f219ac39000-7f219ac64000 r-xp 00000000 08:02 12800                      /usr/lib/libvorbis.so.0.4.4
7f219ac64000-7f219ae63000 ---p 0002b000 08:02 12800                      /usr/lib/libvorbis.so.0.4.4
7f219ae63000-7f219ae64000 r--p 0002a000 08:02 12800                      /usr/lib/libvorbis.so.0.4.4Aborted
```

---

### Post by mips on 2011-03-30
I need Hi-Res Texture support for glide64. Using Ubuntu 10.10 64-bit with Mupen64Plus v1.99.4 + CuteMupen GUI. 

Any simple guides for GlideHQ in Linux?

[http://www.emuxhaven.net/forums/search.php?searchid=4777](http://www.emuxhaven.net/forums/search.php?searchid=4777)

---

### Post by mips on 2011-04-19
Just an update. I managed to get hi-res textures to work.

You need to edit your  /home/<username>/.config/mupen64plus/mupen64plus.cfg file to enable high-res textures.

```

[Video-Rice]

# Frame Buffer Emulation (0=ROM default, 1=disable)
FrameBufferSetting = 0
# Frequency to write back the frame buffer (0=every frame, 1=every other frame, etc)
FrameBufferWriteBackControl = 0
# Render-to-texture emulation (0=none, 1=ignore, 2=normal, 3=write back, 4=write back and reload)
RenderToTexture = 0
# Control when the screen will be updated (0=ROM default, 1=VI origin update, 2=VI origin change, 3=CI change, 4=first CI change, 5=first primitive draw, 6=before screen clear, 7=after screen drawn)
ScreenUpdateSetting = 1
# Force to use normal alpha blender
NormalAlphaBlender = False
# Use a faster algorithm to speed up texture loading and CRC computation
FastTextureLoading = False
# Use different texture coordinate clamping code
AccurateTextureMapping = True
# Force emulated frame buffers to be in N64 native resolution
InN64Resolution = False
# Try to reduce Video RAM usage (should never be used)
SaveVRAM = False
# Enable this option to have better render-to-texture quality
DoubleSizeForSmallTxtrBuf = False
# Force to use normal color combiner
DefaultCombinerDisable = False
# Enable game-specific settings from INI file
EnableHacks = True
# If enabled, graphics will be drawn in WinFrame mode instead of solid and texture mode
WinFrameMode = False
# N64 Texture Memory Full Emulation (may fix some games, may break others)
FullTMEMEmulation = False
# Enable vertex clipper for fog operations
OpenGLVertexClipper = False
# Enable/Disable SSE optimizations for capable CPUs
EnableSSE = True
# Use GPU vertex shader
EnableVertexShader = False
# If this option is enabled, the plugin will skip every other frame
SkipFrame = False
# If enabled, texture enhancement will be done only for TxtRect ucode
TexRectOnly = False
# If enabled, texture enhancement will be done only for textures width+height<=128
SmallTextureOnly = False
# Enable hi-resolution texture file loading
**[COLOR="Red"]LoadHiResTextures = True[/COLOR]**
# Enable texture dumping
DumpTexturesToFiles = False
# Display On-screen FPS
ShowFPS = True
# Enable/Disable Mipmaping
EnableMipmaping = True
# Enable, Disable or Force fog generation (0=Disable, 1=Enable n64 choose, 2=Force Fog)
FogMethod = 1
# Force to use texture filtering or not (0=auto: n64 choose, 1=force no filtering, 2=force filtering)
ForceTextureFilter = 0
# Choose wich texture filtering method will be used by your graphic card(0=no filtering, 1=bilinear, 2=trilinear)
TextureFilteringMethod = 3
# Primary texture enhancement filter (0=None, 1=2X, 2=2XSAI, 3=HQ2X, 4=LQ2X, 5=HQ4X, 6=Sharpen, 7=Sharpen More, 8=External, 9=Mirrored)
TextureEnhancement = 2
# Secondary texture enhancement filter (0 = none, 1-4 = filtered)
TextureEnhancementControl = 0
# Color bit depth to use for textures (0=default, 1=32 bits, 2=16 bits)
TextureQuality = 0
# Z-buffer depth (only 16 or 32)
OpenGLDepthBufferSetting = 16
# Enable/Disable MultiSampling (0=off, 2,4,8,16=quality)
MultiSampling = 0
# Color bit depth for rendering window (0=32 bits, 1=16 bits)
ColorQuality = 0
# OpenGL level to support (0=auto, 1=OGL_1.1, 2=OGL_1.2, 3=OGL_1.3, 4=OGL_1.4, 5=OGL_1.4_V2, 6=OGL_TNT2, 7=NVIDIA_OGL, 8=OGL_FRAGMENT_PROGRAM)
OpenGLRenderSetting = 0
# Enable/Disable Anisotropic Filtering for Mipmaping (0=no filtering, 2-16=quality). This is uneffective if EnableMipmaping is false. If the given value is to high to be supported by your graphic card, the value will be the highest value your graphic card can support. Better result with Trilinear filtering
AnisotropicFiltering = 0

```

If you are having problems copy&paste the entire [Video-Rice] section. These are probably not optimal settings but you can play around with them, there are some guides out there.


Download the textures you want and extract them to /home/<username>/.local/share/mupen64plus/hires_texture/

You have to make sure the texture folder name is IDENTICAL to that of the actual ROM. In order to get the correct rom name start the game from the cli,

```
<username>@obelix:/media/160GB_WD/emulation/roms/n64$ mupen64plus "Legend of Zelda, The - Ocarina of Time (U) (V1.2) [!].z64"
 __  __                         __   _  _   ____  _             
|  \/  |_   _ _ __   ___ _ __  / /_ | || | |  _ \| |_   _ ___ 
| |\/| | | | | '_ \ / _ \ '_ \| '_ \| || |_| |_) | | | | / __|  
| |  | | |_| | |_) |  __/ | | | (_) |__   _|  __/| | |_| \__ \  
|_|  |_|\__,_| .__/ \___|_| |_|\___/   |_| |_|   |_|\__,_|___/  
             |_|         http://code.google.com/p/mupen64plus/  
Mupen64Plus Console User-Interface Version 1.99.4

UI-console: attached to core library 'Mupen64Plus Core' version 1.99.4
            Includes support for Dynamic Recompiler.
Core: Goodname: Legend of Zelda, The - Ocarina of Time (U) (V1.2) [!]
Core: Name: **[COLOR="red"]THE LEGEND OF ZELDA[/COLOR]**
```

So if you have hi-res textures for Legend of Zelda Occarina of Time the folder they reside in will be named,

```
/home/<username>/.local/share/mupen64plus/hires_texture/**[COLOR="red"]THE LEGEND OF ZELDA[/COLOR]**
```


I prefer the Glide64 plugin but Rice is working ok. If I figure out how to get high-res textures to work with Glide64 I will update this thread.

---

### Post by Je Et on 2011-05-02
> **mips said:**
> Ok, think I figured it out so I'll make a mini guide for 64-bit users, 32-bit should be the same.

First install Mupen64Plus **v1.5** from the repos, there is method to this madness!
```
sudo apt-get install mupen64plus
```Open Mupen64+, go Options -> Configure --> Plugins Tab --> Select "blight's SDL input plugin" --> Click Config and setup your gamepad/controller --> Apply changes & test that it works in a few games, exit mupen64+


Now we have to backup that config file for the gampad/controller.
```
cp ~/.config/mupen64plus/blight_input.conf ~/Desktop

```Verify the file is on your desktop and that it contains the settings for you 
controller.




Now we can uninstall mupen64+,
```
sudo apt-get purge mupen64plus
```Check to see that the config files were removed as well, if they are still there you can do,
```
rm -r ~/.config/mupen64plus
```So why did we just go through this whole exercise? Well currently there is no GUI frontend you can use to setup your gamepad/controller for Mupen64+ v1.99.4. The application itself no longer has a GUI (cli only) and the available frontends out there do not support configuration of the controller as yet so we need a backup copy of our v1.5 config file for later use.




Lets get on to installing mupen64+ v1.99.4

First lets add the developers PPA to our repos,
```
sudo add-apt-repository ppa:sven-eckelmann/ppa-mupen64plus
```Next we do an update and install the app,
```
sudo apt-get update
sudo apt-get install mupen64plus
```Run mupen64+ so it creates a config folder and file,
```
mupen64plus
```Next we install [CuteMupen]("http://sourceforge.net/projects/cutemupen/") front end, get the 32-bit version depending on your OS, check for newer files!
```
wget http://sourceforge.net/projects/cutemupen/files/0.1.0/cutemupen-linux64-0.1.0.tar.bz2
tar xvfj cutemupen-linux64-0.1.0.tar.bz2
```Add CuteMupen to your menu,
Right click on Applications toolbar --> Edit Menus --> Games --> New Item
Type: Application
Name: CuteMupen
Cammand: /home/*username*/cutemupen-linux64-0.1.0/cutemupen


Open CuteMupen, it's going to prompt you for some default files & folder locations.

**Core libabrary file:** /usr/lib/libmupen64plus.so.2
**Plugins:** /usr/lib/mupen64plus   (or /home/**username**/.config/mupen64plus/plugins and copy the contents of /usr/lib/mupen64plus into it which is what I have done.)
**Data:** /home/**username**/.config/mupen64plus/data
**Config:** /home/**username**/.config/mupen64plus
**ROMs:** Wherever you have your ROM files stored.
If the folders don't exist create them.


Quit and restart CuteMupen. You can now setup your plugins and their setting to suite your needs.


If your controller/gamepad does not work out of the box you will have to edit your /usr/share/mupen64plus/InputAutoCfg.ini file with information from the ~/Destop/blight_input.conf file we backed up earlier.

Here are some examples that show how,
[http://www.emutalk.net/showthread.php?t=49731](http://www.emutalk.net/showthread.php?t=49731)
[http://code.google.com/p/mupen64plus/wiki/ControllerSetup](http://code.google.com/p/mupen64plus/wiki/ControllerSetup)


This post was compiled with info taken from:
[http://sourceforge.net/project/screenshots.php?group_id=308021&ssid=124559](http://sourceforge.net/project/screenshots.php?group_id=308021&ssid=124559)
[http://www.emutalk.net/forumdisplay.php?f=113](http://www.emutalk.net/forumdisplay.php?f=113)
[http://code.google.com/p/mupen64plus/w/list](http://code.google.com/p/mupen64plus/w/list)

Followed the guide and everything installed, but my input plugin is not showing up in **Cutemupen** and I don't have a **InputAutoCfg.ini** file anywhere on my machine. I found a **Glide64.int**. I have reinstalled three times with no success. Could you copy your **InputAutoCfg.ini **file and post it?  Maybe I could get this to work then. Using **Game Stop 360** pad.

---

### Post by Je Et on 2011-05-11
Found the answer to why I didn't have a **InputAutoCfg.ini** file. When I install using your instructions, I can** not** get cutemupen to run, unless I run in **root**, and then I can't see the '.files'.  So I installed the ones from** Get Deb**,  and everything installs and runs but **doesn't **generate any ini files. I still have no pad control for Mupen64plus, however my next move is to compile everything from source and see how thins work from there.:confused:

---

### Post by mips on 2011-05-12
I see you are running 11.04 which might be the cause of the problems. I'm still on 10.10 and won't be moving any time soon so I cannot test it.

I'm attaching the InputAutoCfg.ini file I backed up during installation as I have overwritten the original removing all the stuff that does not apply to my controller. Just remove the .txt and replace with .ini

---

### Post by Je Et on 2011-05-17
> **mips said:**
> I see you are running 11.04 which might be the cause of the problems. I'm still on 10.10 and won't be moving any time soon so I cannot test it.

I'm attaching the InputAutoCfg.ini file I backed up during installation as I have overwritten the original removing all the stuff that does not apply to my controller. Just remove the .txt and replace with .ini

Thanks for the reply and the file.  I am so used to c&ping,...  that is what I did, even though you posed that I should use the version for my computer.  


```
wget http://sourceforge.net/projects/cutemupen/files/0.1.0/cutemupen-linux**64**-0.1.0.tar.bz2
tar xvfj cutemupen-linux**64**-0.1.0.tar.bz2
```

I changed it to this,

```
wget http://sourceforge.net/projects/cutemupen/files/0.1.0/cutemupen-linux**32**-0.1.0.tar.bz2
tar xvfj cutemupen-linux**32**-0.1.0.tar.bz2
```

and all went well.  For your unselfish help,I have decided to reward you with the secret of human flight!  These instructions must be followed** to the letter.**    You must throw yourself at the ground... and miss.  Very simple...   **if you follow the instructions correctly**.

---

### Post by mips on 2011-05-17
> **Je Et said:**
> Thanks for the reply and the file.  I am so used to c&ping,...  that is what I did, even though you posed that I should use the version for my computer.

But thou should read the instructions clearly squire :D


> **mips said:**
> 
Next we install [CuteMupen]("http://sourceforge.net/projects/cutemupen/") front end, **[COLOR="Red"]get the 32-bit version depending on your OS[/COLOR]**, check for newer files!

Repeat after me x100, "I shalt not blindly copy & paste"

Glad it all worked out for you ;)

---

### Post by Condor Cluster on 2011-06-05
Hmm, I wonder if 1.99.4 will solve my choppy audio problems.

Would this guide for Mupen64Plus 1.99.4 and CuteMupen work on 10.04?

Cheers.

---

### Post by mips on 2011-06-06
> **Condor Cluster said:**
> Hmm, I wonder if 1.99.4 will solve my choppy audio problems.

Would this guide for Mupen64Plus 1.99.4 and CuteMupen work on 10.04?

Cheers.

I don't think the PPA has packages for Lucid. No harm in trying or you could always just compile from source.

Edit: For 10.04 you can look here [http://www.playdeb.net/updates/Ubuntu/10.04/?category=Emulator](http://www.playdeb.net/updates/Ubuntu/10.04/?category=Emulator), they seem to have both apps packaged so just modify the above install procedure.
Alternatively, [http://code.google.com/p/mupen64plus/](http://code.google.com/p/mupen64plus/)

---

### Post by Condor Cluster on 2011-06-06
Tried the playdeb.net links, say 1.99.4 and 10.04, but only installs 1.5 (the same as package manager)

Thanks anyway

---

### Post by Rytron on 2011-06-13
I've pointed the library path to the wrong place and now cannot start CuteMupen.

```
cutemupen
```

Output:
```
dlopen('/usr/lib/mupen64plus') error: /usr/lib/mupen64plus: cannot read file data: Is a directory
Segmentation fault
```

Can I start CuteMupen in safe mode?

---

### Post by mips on 2011-06-13
I'm not sure I know what you mean but can you not simply edit the /home/*username*/.config/CuteMupen/CuteMupen.conf file?

Mupen64Library=/usr/lib/libmupen64plus.so.2 should be the correct entry.

---

### Post by Rytron on 2011-06-13
> **mips said:**
> I'm not sure I know what you mean but can you not simply edit the /home/*username*/.config/CuteMupen/CuteMupen.conf file?

Mupen64Library=/usr/lib/libmupen64plus.so.2 should be the correct entry.

Hi mips. I did that. Here is the situation now.

My input:
```
cutemupen
```

My output:
```
dlopen('/usr/lib/libmupen64plus.so.2') error: /usr/lib/libmupen64plus.so.2: cannot open shared object file: No such file or directory
Segmentation fault
```

---

### Post by Goveynetcom on 2011-06-14
Curious, has anyone been successful at fixing the choppy audio? I'm not a emulation noob, but I have no idea what optimal settings for the sound plugin are.

---

### Post by mips on 2011-06-15
> **Rytron said:**
> Hi mips. I did that. Here is the situation now.


No idea, I suck at fixing broken things so maybe try removing and reinstalling.

---

### Post by mips on 2011-06-15
> **Goveynetcom said:**
> Curious, has anyone been successful at fixing the choppy audio? I'm not a emulation noob, but I have no idea what optimal settings for the sound plugin are.

I don't have choppy audio and I don't think I changed any of the default settings. I'm using the mupen64plus-audio-sdl.so plugin

[IMG]https://lh4.googleusercontent.com/55ifZMCoYBdHmi5F8xERPGjS0aA65W2ZzPpOOrJssjW2U-UOeRIR7TbaR8YM9WTNAyRsbP6uoQCR5rRGx_6MHXGoZg=s512[/IMG]

---

### Post by messie on 2011-08-31
Greetings I have done all the above, yet I have not copied the input configuration file. can anyone share his with me? :lolflag: any working keyboard configuration file will do

---

### Post by jzemeocala on 2012-01-18
Hello Everyone. I am currently trying to run this setup on the listed minimum requirements (dell inspiron 5000 with pIII 600mhz and 256MB ram) and im using Bohdi Linux (based on Lucid) with a blank openbox session. SO... I should theoretically be able to run this thing if I can configure it perfectly. however, in practice, I have yet to get it going above 20FPS using the rice plugin with it configured according to another site, and I cant seem to get the glide64 plugin going faster than 1FPS with it configured optimally according to this thread. there are a couple configurations with the glide64 plugin where it SOUNDS as though its playing at a decent FPS but there is no video and i have to kill the process to stop it which means I lose the configuration. Any help would be much appreciated.

Thanks in advance

---

### Post by mips on 2012-01-18
What GPU do you have?

I think mupen requires hardware accelerated opengl.

---

### Post by jzemeocala on 2012-01-18
I have an ATI 3D Rage Mobility-P with 8MB vRAM and as recommend in another forum I checked my direct rendering capabilities via "glxinfo | grep direct" which responded with an affirmative.

---

### Post by mips on 2012-01-19
> **jzemeocala said:**
> I have an ATI 3D Rage Mobility-P with 8MB vRAM and as recommend in another forum I checked my direct rendering capabilities via "glxinfo | grep direct" which responded with an affirmative.

I cannot find any reference to the system requirements for Mupen64Plus. I looked at the Project64 requirements (yes I know it's not the same thing but I think they use the same plugins and your GPU just does not cut it.

EDIT: I went on to the mupen64+ developer IRC channel and according to feedback there your hardware specs are to low, especially the GPU. Recommend a rv350 (Radeon 9600) with >=64MB RAM.

So it looks like you are out of luck there.

---

### Post by jzemeocala on 2012-01-19
bummer........Thanks for the help though. On a slightly unrelated note, Do you suppose I would have any better luck with playstation emulation (e.g. pcsX) on this machine. I know I meet the CPU and RAM requirements but I couldnt find anything related to video card requirements.

---

### Post by MadmanRB on 2012-05-24
Cutemupen sucks, its bug ridden, barely works and is next to impossible to configure a controller in it.
I personally use wine and Project64.

---

### Post by thatguruguy on 2012-05-24
> **MadmanRB said:**
> Cutemupen sucks, its bug ridden, barely works and is next to impossible to configure a controller in it.
I personally use wine and Project64.

I'm sure if you keep looking around, you can find some other old threads about Mupen64 so you can keep posting the same thing.

Mupen64+ works great on my HTPC running MythTV. But then, I don't use individual front-ends for any of my emulators; I have them all set up in MythTV.

---

### Post by mips on 2012-05-25
> **MadmanRB said:**
> Cutemupen sucks, its bug ridden, barely works and is next to impossible to configure a controller in it.
I personally use wine and Project64.

Cutemupen worked fine for me if you first configured your controller in mupen64+ v1.5. Had no big issues that I can recall. That said cutemupen no longer seems to be developed and there is another newer frontend that is up to date but it has some dependency issues.

I will write a new guide for this once I get round to sorting out the frontend part.

---

