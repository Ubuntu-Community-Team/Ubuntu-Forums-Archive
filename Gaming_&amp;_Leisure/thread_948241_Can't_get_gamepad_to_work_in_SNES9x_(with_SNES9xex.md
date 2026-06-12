---
title: "Can't get gamepad to work in SNES9x (with SNES9xexpress)"
date: 2008-10-15
forum: Gaming &amp; Leisure
---

### Post by TheOrangePeanut on 2008-10-15
I'm using the snes9xexpress front-end to snes9x and I can't get my gamepad to work.  I can configure the pad in the gui, but when I actually "power on" the machine, I get error code 1.  If I disable the pad, the game plays fine (but playing with a keyboard is not my idea of fun).  Any idea what the problem may be?

[PHP]snes9x -joydev1 /dev/input/js0 -joymap1 1 2 0 3 4 5 8 9 /media/SEA_DISC/Roms/SNES/Megaman7.smc
snes9x: S9xUsage: snes9x <options> <rom image filename>

Where <options> can be:

-sound or -so                   Enable digital sound output
-nosound or -ns                 Disable digital sound output
-soundskip or -sk <0-3>         Sound CPU skip-waiting method
-soundquality, -sq, or -r <num> Set sound playback quality
                                  0 - off, 1 - 8192, 2 - 11025, 3 - 16500,
                                  4 - 22050 (default), 5 - 29300, 6 - 36600,
                                  7 - 44000
-altsampledecode or -alt        Use alternate sample decoder
-stereo or -st                  Enable stereo sound output (implies -sound)
-mono                           Enable monaural sound output (implies -sound)
-soundsync or -sy               Enable sound sync to CPU at startup
-soundsync2 or -sy2             Alternate method to sync sound
-threadsound or -ts             Use a separate thread to output sound
-interpolatedsound or -is <0-3> Select sound interpolation method
                     Reading config file /etc/snes9x/snes9x.conf
             0=none, 1=linear, 2=cubic, 3=gaussian
-echo or -e                     Enable DSP echo effects at startup
-noecho or -ne                  Disable DSP echo effects at startup
-envx or -ex                    Enable volume envelope height reading
-nosamplecaching, -nsc, or -nc  Disable sample caching
-nomastervolume or -nmv         Disable master volume setting
-fix                            'Fix' sound frequencies

-conf <filename>                Use specified conf file (after standard files)
-nostdconf                      Do not load the standard config files
-hdma or -ha                    Enable HDMA emulation at startup
-nohdma or -nh                  Disable HDMA emulation at startup
-transparency or -tr            Enable transparency effects
-notransparency or -nt          Disable transparency effects at start
-windows                        Enable graphic window effects
-nowindows or -nw               Disable graphic window effects
-im7                            Enable Mode 7 interpolation effects
-displayframerate or -dfr       Display the frame rate counter
-aidoshm <shmid>                Run in AIDO mode, with specified SHM ID

-hires or -hi                   Enable support for hi-res and interlace modes
-frameskip or -f <num>          Screen update frame skip rate
-frametime or -ft <float>       Milliseconds per frame for frameskip auto-adjust

-hirom, -hr, or -fh             Force Hi-ROM memory map
-lorom, -lr, or -fl             Force Lo-ROM memory map
-bs                             Use BS Satellite System ROM mapping
-bsxbootup                      Boot up BS games from BS-X
-nointerleave or -ni            ROM image is not in interleaved format
-interleaved or -i              ROM image is in interleaved format
-interleaved2 or -i2            ROM image is in interleaved 2 format
-interleavedgd24 or -gd24       ROM image is in interleaved gd24 format
-header, -he, or -hd            Force the detection of a ROM image header
-noheader or -nhd               Force the detection of no ROM image header
-ntsc or -n                     Force NTSC timing (60 frames/sec)
-pal or -p                      Force PAL timing (50 frames/sec)
-superfx or -sfx                Force detection of the SuperFX chip
-nosuperfx or -nosfx            Force detection of no SuperFX chip
-dsp1                           Force detection of the DSP-1 chip
-nodsp1                         Force detection of no DSP-1 chip

-nopatch                        Do not apply any available IPS patches
-cheat                          Apply saved cheats
-nocheat                        Do not apply saved cheats
-gamegenie or -gg <code>        Supply a Game Genie code
-actionreplay or -ar <code>     Supply a Pro-Action Reply code
-goldfinger or -gf <code>       Supply a Gold Finger code

-nomp5                          Disable emulation of the Multiplayer 5 adapter
-nomouse                        Disable emulation of the SNES mouse
-nosuperscope                   Disable emulation of the Superscope
-nojustifier                    Disable emulation of the Konami Justifier
-port# <control>                Specify which controller to emulate in port 1/2
      Controllers: none            No controller
                   pad#            Joypad number 1-8
                   mouse#          Mouse number 1-2
                   superscope      Superscope (not useful with -port1)
                   justifier       Blue Justifier (not useful with -port1)
                   one-justifier   ditto
                   two-justifiers  Blue & Pink Justifiers
                   mp5:####        MP5 with the 4 named pads (1-8 or n)

-net                            Enable netplay
-port or -po <num>              Use port <num> for netplay
-server or -srv <string>        Use the specified server for netplay

-nojoy or -j                    Disable joystick reading
-joydev1 <string>               Specify joysick device 1
-joydev2 <string>               Specify joysick device 2
-joydev3 <string>               Specify joysick device 3
-joydev4 <string>               Specify joysick device 4
-buffersize, -bs, or -b <num>   Sound playback buffer size in bytes
-loadsnapshot <file>            Load snapshot file at start
-sdd1-pack <file>               Use named S-DD1 graphics pack

-set-repeat or -no-set-repeat   Whether to allow altering keyboard auto-repeat
-y or -y1                       Enable 'TV mode' (implies -16 -hires -tr)
-y2                             Enable Kreed's Super 2xSaI image processing
-y3                             Enable Kreed's Super Eagle image processing
-y4                             Enable Kreed's 2xSaI image processing
-y5                             Enable Kreed's software bi-linear filtering
-GUI.interpolate<num>           Same as -y<num>
-scale or -sc                   Scale image to fit window
-nomodeswitch or -nms           Don't switch modes in fullscreen mode
-fullscreen or -fs              Begin in fullscreen mode

ROM image needs to be in Super MagiCom (*.smc), Super FamiCom (*.sfc),
*.fig, or split (*.1, *.2, or sf32527a, sf32527b, etc) format and can be
compressed with zip, gzip, or compress.

snes9x returned error code 1
[/PHP]

---

### Post by FranMichaels on 2008-10-15
Have you given zsnes a try. snes9x may be portable, but it's essentially *dead* development wise.

Anyway to try to help, specify the joypad as /dev/input/js0

Oh yeah, snes9xpress is a version behind the last release of snes9x (1.4.2 vs 1.5.1 I believe.) And it's an abandoned front-end.

So again, I'd say give zsnes a go.

---

### Post by grossaffe on 2008-10-15
or use the GTK port of SNES9x.  its a very nice front-end.

---

### Post by TheOrangePeanut on 2008-10-15
I did use zsnes last night, but I don't like it at all.  The interface is terrible and it crashed when I tried to play it fullscreen, which sucks.

What is the name of the gtkport of snes9x?  How much development does an snes emulator need anyway, if it plays all the games the way its supposed too?  I've used snes9x 1.4.2 for a very, very long time.

---

### Post by FranMichaels on 2008-10-15
You don't like the horribly dated zsnes gui? 
Well, the next version they will offer a QT gui. 

As for the emulators, supporting features of some of the carts with special chips in them (like the superfx chip), filters, minor niceties, and higher accuracy (perhaps less "hacks" needed to get games to work properly.) 

**If snes9x runs all you care to run with it, then keep using it. **

I was just offering an additional reason to give zsnes a go, as it's still actively developed. 
rambling
Even though I'm a gtk person, I'm still looking forward to the new version, the old gui will still be an option I think. It grows on you when you've used zsnes for like 10 years. It was the same in the dos version believe it or not. 
/rambling

EDIT: I was looking at the original post
```
snes9x -joydev1 /dev/input/js0 -joymap1 1 2 0 3 4 5 8 9 /media/SEA_DISC/Roms/SNES/Megaman7.smc
```

In the error output, I see no mention of the joymap1 parameter... Does it work as expected with just
```
snes9x -joydev1 /dev/input/js0 /media/SEA_DISC/Roms/SNES/Megaman7.smc
```

---

### Post by TheOrangePeanut on 2008-10-15
I did try launching it without -joymap1 and it runs, but my buttons aren't configured (obviously).  My d-pad works but none of the other buttons.

For now I'll just use zsnes.  It is working well enough; it turned out it was crashing because it was set on a video mode that uses OGL (which crashes my computer every time, no matter what app it is).  

Any idea when the QT version is coming out?  I looked on their website but it hasn't been updated since January 07...

---

### Post by mister_k81 on 2008-10-16
> **grossaffe said:**
> or use the GTK port of SNES9x.  its a very nice front-end.


Yeah... the GTK port definitely needs to get more attention :) : 

Link here: [http://www.snes9x.com/phpbb2/viewtopic.php?p=22874](http://www.snes9x.com/phpbb2/viewtopic.php?p=22874)
PPA: [https://launchpad.net/~bearoso/+archive](https://launchpad.net/~bearoso/+archive)

---

