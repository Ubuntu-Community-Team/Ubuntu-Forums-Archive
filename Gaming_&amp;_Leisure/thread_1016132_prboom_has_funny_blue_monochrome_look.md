---
title: "prboom has funny blue monochrome look"
date: 2008-12-19
forum: Gaming &amp; Leisure
---

### Post by Mishabuntu on 2008-12-19
Please help me with the game prboom (like doom). The video has a funny blue and black monochrome look to it. 

I enabled the GL video mode and that looks fine, but runs too slow on this old laptop, so I need to have the video in the 8 bit mode.

In the 8 bit video mode it looks monochrome. (blue and black) I installed the game with the synaptic package manager on Xubuntu OS. It also installed all of the dependencies. Is there maybe some other graphics library that is needed? or something that needs to be added to the prboom command line? or does something need to be changed in a config file?

I've searched around and couldn't find any info on this problem.

Any help would be appreciated.
Thank you

---

### Post by Mishabuntu on 2008-12-30
Wow! One week and no replies yet? Could this problem have something to do with tft lcd laptop screen? Needing different settings? Libraries?

---

### Post by Dark Aspect on 2009-01-01
Probably won't help that much but since nobody is replying, have you try to load the game via terminal to get an output? Do you have your video drivers properly installed? Is compiz running?

---

### Post by Mishabuntu on 2009-01-02
Here's the output

mishabuntu@xubuntu:~$ prboom

prboom v2.4.7 ([http://prboom.sourceforge.net/](http://prboom.sourceforge.net/))
M_LoadDefaults: Load system defaults.
 default file: /home/mishabuntu/.prboom/prboom.cfg
 found /usr/share/games/doom/doom2.wad
IWAD found: /usr/share/games/doom/doom2.wad
PrBoom (built Jan  7 2008), playing: DOOM 2: Hell on Earth
PrBoom is released under the GNU General Public license v2.0.
You are welcome to redistribute it under certain conditions.
It comes with ABSOLUTELY NO WARRANTY. See the file COPYING for details.
V_Init: allocate screens.
 found /usr/share/games/doom/prboom.wad
D_InitNetGame: Checking for network game.
W_Init: Init WADfiles.
 adding /usr/share/games/doom/doom2.wad
 adding /usr/share/games/doom/prboom.wad
W_InitCache

M_Init: Init miscellaneous info.
R_Init: Init DOOM refresh daemon - 
R_LoadTrigTables: Endianness...ok.
R_InitData: Textures Flats Sprites 
R_Init: R_InitPlanes R_InitLightTables R_InitSkyMap R_InitTranslationsTables R_InitPatches 
P_Init: Init Playloop state.
I_Init: Setting up machine state.
I_InitSound:  configured audio device with 1024 samples/slice
I_InitSound: sound module ready
S_Init: Setting up sound.
S_Init: default sfx volume 8
HU_Init: Setting up heads up display.
I_InitGraphics: 640x480
I_UpdateVideoMode: 640x480 (fullscreen)
V_InitMode: using 8 bit video mode
I_SetRes: Using resolution 640x480
I_UpdateVideoMode: 0xe0000000, SDL buffer, direct access
ST_Init: Init status bar.
I_ShutdownMusic: removing /tmp/prboom-music-hT0qSV
I_ShutdownSound: 


################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
################################################################################
###########################       ##############################################
###################       ###########        ###################################
  #########  ###  ################# ##########   ##   ########################  
###  ##################################################   ##   #################
###########################       ##############################   ##   ########
###################       ###########   ##   #############################   ###
###########  #################################   ##   ##########################
###  ##################################################   ##   #################
################################################################   ##   ########
#####################################       ##############################   ###
  ####    ####    ################# ######### ######## #######################  
################################################################################
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
                                                                                
prboom v2.4.7 ([http://prboom.sourceforge.net/](http://prboom.sourceforge.net/))
mishabuntu@xubuntu:~$ 

The ####### ##### above are colored in the original output.
I hope that someone can help.
Thank you,
Mishabuntu

---

### Post by Butthead on 2009-01-02
It's been awhile since the old CGA video display days, but that eight bit video mode sounds kind of skimpy. :-k

I could have sworn the ancient Atari 2600 video game system could crank out more colors than that.

---

### Post by Mishabuntu on 2009-01-04
Ok, I'm thinking that maybe the problem is with SDL. The SDL is installed as one of prbooms dependencies. I have vga=771 as kernel option for FB. 

I read somewhere to try this command 
SDL_VIDEODRIVER=vesafb prboom

but get this output
prboom v2.4.7 ([http://prboom.sourceforge.net/](http://prboom.sourceforge.net/))
Could not initialize SDL [No available video device]

Not sure if I'm headed in the right direction.

Anyone have any ideas?

Maybe it's a video driver problem? Everything else seems to be working fine.
here's the display info from running lshw
*-display UNCLAIMED
             description: VGA compatible controller
             product: NM2200 [MagicGraph 256AV]
             vendor: Neomagic Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list
             configuration: latency=128 maxlatency=255 mingnt=16

---

### Post by Sera88 on 2009-04-19
I have the exact same problem. PrBoom and SDL Doom both give the blue-black display problem. I have IBM Thinkpad 600 with Neomagic NM2160 graphics chip running on Ubuntu 8.04 (kernel 2.6.24-16-generic).

I built the whole SDL library from source and after that the SDL Doom from source, but it didn't work - the colors were still messed up. I tried to start the X server with 8 bpp mode (**startx -- -depth 8**) but it didn't work - the colors were messed up, although now they were solarized so there were more colors than blue and black.

I have no other suggestions on this... Maybe we should try running XFree86 instead of Xorg?

EDIT: I tried a couple of things and now it's kinda working OK. So first you've got to start X with the command **startx -- -fbbpp 8**, then start PrBoom in a window (**prboom -window**), and slide your mouse on top of the PrBoom window. It then gets the right colors. In fullscreen this doesn't work, unfortunately. I'll play with this thing a bit more...

Yeah! I've got PrBoom and SDL Doom running nicely in fullscreen mode by moving the mouse cursor while the game initializes itself.

---

### Post by Mishabuntu on 2009-10-10
I still need a solution to this. Help!  ...anyone?

---

### Post by Mishabuntu on 2009-10-11
Ok, finally progress here.
I read up on some SDL information, then reinstalled all of the needed SDL packages and timidity package.

Then I also needed to edit audio permissions for user.

Then from the terminal within X  
$ **lsmod | grep fb**
and checked to see if vesafb and fbcon were loaded... they were.

Then $ **SDL_VIDEODRIVER=fbcon SDL_AUDIODRIVER=esd prboom** and there it is! Success! 

Also had to edit prboom.cfg to change screen size and to turn the music on.

Now, without even loading X I'm able to simply switch to a tty console, like say tty1 **<Ctrl+Alt+F1>** then Log in and type **prboom**

---

