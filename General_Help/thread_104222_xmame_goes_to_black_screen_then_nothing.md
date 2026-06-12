---
title: "xmame goes to black screen then nothing?"
date: 2005-12-15
forum: General Help
---

### Post by wargames on 2005-12-15
I have the fglrx drivers for my ATI card installed and 3ddesktop works ok but I then installed xmame and gxmame in order to play games and when I run gxmame the screen goes all black and then nothing happens. I have to hit "Ctrl-Alt-F1" and get to a login screen then I reboot the PC.  As it's shutting down in preparing to reboot it gives a error about "fglrx full frame buffer" or something like that.

Is this a video driver problem and is there anyway to fix it?

I have an ATI Xpress x200 with 128MB shared memory with an open PCIe slot.

I used this How to in order to install xmame and gxmame:
[http://www.ubuntuforums.org/showthread.php?t=86213&highlight=gxmame](http://www.ubuntuforums.org/showthread.php?t=86213&highlight=gxmame)

I also copied my roms and left them in the zip format to the /usr/share/games/xmame/roms directory also.

Any ideas what's wrong?

---

### Post by matthewn on 2005-12-16
I have had this problem on three different machines for what seem to be three different reasons. The mode that xmame uses by default to do full-screen effects (DGA) is problemmatic for different reasons with different drivers, and I've forgotten all the particulars. I do know, however, that this solution worked on all three of my boxes: add '-x11-mode 3' to your xmame command line. So if before you were doing:

xmame pacman

Now do:

xmame -x11-mode 3 pacman

Hope this helps.

---

### Post by wargames on 2005-12-16
Thanks for your reply, but it didn't work. :(

I've been trying different settings in the /etc/xmame/xmamerc file and different settings in the Multimedia Systems Selector but still nothing, just a black blank screen and I have to hit Ctrl-Alt-Backspace to get out of it. Maybe I just can't run xmame on my system for some reason.

---

### Post by wargames on 2005-12-16
Well, I just installed xmame-sdl and xmame-svga packages from the repositories and still nothing! This is making me crazy!!! ](*,) 

I get nothing, just a big black blank screen and the only way to get back to the desktop is Ctrl-Alt-Backspace and sometimes I have to hit Ctrl-Alt-F1 and restart the gdm.

I tried these commands I found online:
xmame -x11-mode 3 pacman
xmame.x11
xmame -x11 3 pacman

I also tried changing to the different settings in the MultiMedia Settings from SDL to No Xv to X11/Xshm/Xv just to see what would happen, even though I don't understand what or why there are all of these different settings. Nothing works. I have my ATI drivers installed right, and 3ddesktop application along with the screensavers all seem to work ok. So why won't xmame work at all? Is it a setting in xorg.conf? Is it some command line settings? I've spent many hours trying to get this fixed but still nothing.

Does anyone have any idea what's wrong? I have given up on this for now, and will have to use Windows just to play my Mame games. :(

Any suggestions?

---

### Post by matthewn on 2005-12-16
I don't know if this will help or not. I've got the xmame-common, xmame-sdl, and xmame-x packages installed from the repos, and the following is my $HOME/.xmame/xmamerc file. My xmame works as long as I don't let it kick into DGA mode.

### xmame running parameters ###
#
# Default xmame package configuration
# Last Updated for: 0.85
# This file is used by all xmame binaries

### Digital sound related ###
dsp-plugin            esound
timer                   0

### Sound mixer related ###
# sound-mixer-plugin    <NULL> (not set)

### Video Related ###
bpp                     0
arbheight               0
heightscale             1
widthscale              1
effect                  0
autodouble              1
scanlines               0
artwork                 0
use_backdrops           1
use_overlays            1
use_bezels              1
artwork_crop            0
artwork_resolution      0
frameskipper            1
throttle                1
frames_to_run           0
sleepidle               0
autoframeskip           1
maxautoframeskip        8
frameskip               1
brightness              1.000000
pause_brightness        0.650000
gamma                   1.000000
norotate                0
ror                     0
rol                     0
autoror                 0
autorol                 0
flipx                   0
flipy                   0

### Vector Games Related ###
# vectorres             <NULL> (not set)
beam                    1.000000
flicker                 0.000000
intensity               1.500000
antialias               1
translucency            1

### Video Mode Selection Related ###
keepaspect              1
displayaspectratio      1.330000

### Sound Related ###
sound                   1
samples                 1
samplefreq              22050
bufsize                 3.000000
volume                  -3
# audiodevice           <NULL> (not set)
# mixerdevice           <NULL> (not set)

### Input device options ###
joytype                 4
analogstick             1
joydevname              /dev/input/js
joyusb-calibrate        0
mouse                   0
ugcicoin                0
steadykey               0
a2d_deadzone            0.300000
# ctrlr                 <NULL> (not set)
digital                 none
usbpspad                0
rapidfire               0

### File I/O-related ###
rompath                 $HOME/.xmame/roms
samplepath              $HOME/.xmame/samples
inipath                 /etc/xmame/ini
cfg_directory           $HOME/.xmame/cfg
nvram_directory         $HOME/.xmame/nvram
memcard_directory       $HOME/.xmame/memcard
input_directory         $HOME/.xmame/inp
hiscore_directory       /var/games/xmame/hi
state_directory         $HOME/.xmame/sta
artwork_directory       /usr/share/games/xmame/artwork
snapshot_directory      /usr/share/games/xmame/snap
diff_directory          $HOME/.xmame/diff
ctrlr_directory         /etc/xmame/ctrlr
cheat_file              /usr/share/games/xmame/cheat.dat
hiscore_file            /usr/share/games/xmame/hiscore.dat
history_file            /usr/share/games/xmame/history.dat
mameinfo_file           /usr/share/games/xmame/mameinfo.dat
# record                <NULL> (not set)
# playback              <NULL> (not set)

### MAME Related ###
defaultgame             pacman
language                english
fuzzycmp                1
cheat                   0
skip_disclaimer         0
skip_gameinfo           0
crconly                 0
bios                    default
# state                 <NULL> (not set)

### Frontend Related ###
clones                  1

### For target specific options
# use the target specific file.
#
# X11: xmame-x11rc
# GL : xmame-xglrc
# SDL: xmame-SDLrc
# SVGA: xmame-svgalibrc

---

### Post by wargames on 2005-12-18
[QUOTE=matthewn]I don't know if this will help or not. I've got the xmame-common, xmame-sdl, and xmame-x packages installed from the repos, and the following is my $HOME/.xmame/xmamerc file. My xmame works as long as I don't let it kick into DGA mode.

### xmame running parameters ###
#
# Default xmame package configuration
# Last Updated for: 0.85
# This file is used by all xmame binaries

### Digital sound related ###
dsp-plugin            esound
timer                   0

### Sound mixer related ###
# sound-mixer-plugin    <NULL> (not set)

### Video Related ###
bpp                     0
arbheight               0
heightscale             1
widthscale              1
effect                  0
autodouble              1
scanlines               0
artwork                 0
use_backdrops           1
use_overlays            1
use_bezels              1
artwork_crop            0
artwork_resolution      0
frameskipper            1
throttle                1
frames_to_run           0
sleepidle               0
autoframeskip           1
maxautoframeskip        8
frameskip               1
brightness              1.000000
pause_brightness        0.650000
gamma                   1.000000
norotate                0
ror                     0
rol                     0
autoror                 0
autorol                 0
flipx                   0
flipy                   0

### Vector Games Related ###
# vectorres             <NULL> (not set)
beam                    1.000000
flicker                 0.000000
intensity               1.500000
antialias               1
translucency            1

### Video Mode Selection Related ###
keepaspect              1
displayaspectratio      1.330000

### Sound Related ###
sound                   1
samples                 1
samplefreq              22050
bufsize                 3.000000
volume                  -3
# audiodevice           <NULL> (not set)
# mixerdevice           <NULL> (not set)

### Input device options ###
joytype                 4
analogstick             1
joydevname              /dev/input/js
joyusb-calibrate        0
mouse                   0
ugcicoin                0
steadykey               0
a2d_deadzone            0.300000
# ctrlr                 <NULL> (not set)
digital                 none
usbpspad                0
rapidfire               0

### File I/O-related ###
rompath                 $HOME/.xmame/roms
samplepath              $HOME/.xmame/samples
inipath                 /etc/xmame/ini
cfg_directory           $HOME/.xmame/cfg
nvram_directory         $HOME/.xmame/nvram
memcard_directory       $HOME/.xmame/memcard
input_directory         $HOME/.xmame/inp
hiscore_directory       /var/games/xmame/hi
state_directory         $HOME/.xmame/sta
artwork_directory       /usr/share/games/xmame/artwork
snapshot_directory      /usr/share/games/xmame/snap
diff_directory          $HOME/.xmame/diff
ctrlr_directory         /etc/xmame/ctrlr
cheat_file              /usr/share/games/xmame/cheat.dat
hiscore_file            /usr/share/games/xmame/hiscore.dat
history_file            /usr/share/games/xmame/history.dat
mameinfo_file           /usr/share/games/xmame/mameinfo.dat
# record                <NULL> (not set)
# playback              <NULL> (not set)

### MAME Related ###
defaultgame             pacman
language                english
fuzzycmp                1
cheat                   0
skip_disclaimer         0
skip_gameinfo           0
crconly                 0
bios                    default
# state                 <NULL> (not set)

### Frontend Related ###
clones                  1

### For target specific options
# use the target specific file.
#
# X11: xmame-x11rc
# GL : xmame-xglrc
# SDL: xmame-SDLrc
# SVGA: xmame-svgalibrc[/QUOTE]

Well, at first I didn't have a ~/.xmame/xmamerc file, but after I did this:
xmame --showconfig > ~/.xmame/xmamerc

The screen went black again and then nothing as usual. I had to restart gnome and then went and checked and I had the xmamerc file. I checked it, everything looked ok I guess, very similar to yours except for a few different entries about X-11 video. I've tried everything I can find online and nothing works. Just a black blank screen and then I have to restart gnome. I installed all the xmame stuff, then uninstalled the sdl and svga xmame packages and tried again and nothing. I've now just totally uninstalled all the xmame packages since they simply don't work.

I've just given up. Nobody anywhere seems to have as answer since I've seen a few other people with the same problem. I'll just have to forget about xmame. I guess this package is busted for some strange reason on my system.  I've read where xmame 0.86 is very old and I wonder if this is the problem.  Anyway, I have to stick with Windows for mame. :(

---

### Post by wargames on 2005-12-23
Update: Fixed!! YES!!! :D 

Ok after many hours of pulling out my hair, I decided to start from scratch again. This time I was going to trying just installing xmame-sdl instead of xmame-x from the repositories. This worked! From what I've read (and correct me if I'm wrong here) but it appears that in order to use xmame-x you must insert modelines into your xorg.conf file in order for it to work, and since I didn't do that or even know how to do that, and adding modelines sounded complicated anyway, this might explain why the version of xmame called xmame-x would not work on my system. And it appears that xmame-sdl doesn't need the modeline entries. (please correct me if I'm wrong here)

So I decided to installed xmame-sdl and that worked just fine, except it was just in a window. So I enabled fullscreen and now it seems to work ok. I even got gxmame to work as well. Heck yeah!

Let's recap my solution just in case anyone else gets a black screen or whatever:

Follow this How to: except instead of installing xmame-x, install xmame-sdl instead.
[http://www.ubuntuforums.org/showthread.php?t=86213&highlight=xmame](http://www.ubuntuforums.org/showthread.php?t=86213&highlight=xmame)

Go ahead and install the gxmame from that How to: as well.

Now before you run gxmame or xmame do the following in order to create a configuration file in ~/.xmame called xmamerc.

$ xmame --showconfig > ~/.xmame/xmamerc

If you don't what to use gxmame then you can manually edit this config file with gedit.

Now I copied my roms into the /usr/share/games/xmame/roms directory and then ran gxmame and set your options if you want fullscreen, check sounds settings, etc.

If you want to use the command line instead, this is what I used to run pacman at fullscreen using xmame-sdl:

$ xmame -fullscreen -scale 2 pacman

or

$ xmame -fullscreen -scale 2 -ef 2 pacman

the -ef 2 is for a scanline filter.

Use "man xmame" for additional settings for -ef or whatever command line options you would like to use.

I hope someone will find this useful if they are having trouble installing xmame.

Later dudes.  :cool:

---

### Post by zi99y on 2006-03-25
If anyones interested I found the problem with the black screen on Mame - at least, this worked on my machine using KXMame. I believe the problem has to do with the DGA video mode when running an ATI graphics card with the fglrx drivers, which is buggy and/or broken.

I have been tweaking around with my xorg.conf file and made the following changes:

Under Section "Module"
```
	SubSection "extmod"
		Option "omit xfree86-dga" #Don't initialize the DGA extension
	EndSubSection

```
And commented out the extmod module with a #, like so
```
#	Load	"extmod"
```

Restarted X with a ctrl+alt+backspace and voila! I no longer get the black screen when launching kxmame/gxmame. It took quite a lot of investigation, I hope someone finds this useful.

---

### Post by asnesio on 2006-06-18
Worked nice. Thanks zi99y!

---

### Post by EL CHAVO on 2007-02-27
Thanks zi99y, worked for me as well!

---

### Post by MaindotC on 2007-12-03
Zinny you absolutely blow my mind, man.  Can you describe how you figured this out and the points you decided to hit in your troubleshooting?  I would like to understand your methodology.  Oh, btw, it works now :)

---

