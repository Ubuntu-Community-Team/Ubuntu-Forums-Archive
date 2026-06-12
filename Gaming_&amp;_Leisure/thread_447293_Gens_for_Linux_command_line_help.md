---
title: "Gens for Linux command line help?"
date: 2007-05-17
forum: Gaming &amp; Leisure
---

### Post by Shawn Dineley on 2007-05-17
Hello
   
   I'm trying to use Gens for Linux from the command line in Full Screen. I don't want the gui. I've got it installed and running. I'm also using the opengl version. 

   Well anyways I've now got Gens to open a game from the command line. But it goes back to a window and the gens gui opens. I'm using the --fs option which from what I've read should enable Full screen without a gui. And it does go back to full screen if I use my mouse to minimize the gui screen.

So does anyone know a way to do this??? Please Help

                                                  Thanks

---

### Post by Shawn Dineley on 2007-05-18
Bump

---

### Post by Naegling23 on 2007-05-18
I also would like to do this, so that I could use it connected to mythtv

As far as I know, you cannot run gens from the command line without patching it.  I've been using xe to play genesis games in mythtv, which sucks because xe is a great emulator, but doesnt support save states :-(

---

### Post by Shawn Dineley on 2007-05-18
Thanks, I knew someone else also had to be having the same problem. Now we just need someone with the answer to chime in.

---

### Post by ShirishAg75 on 2007-05-19
Shawn a link to the game would also be good if you are looking for answer as well as what the game is about.

---

### Post by DoktorSeven on 2007-05-19
This is the [Gens emulator for Genesis/Mega Drive](http://ubuntuforums.org/showthread.php?t=166980&highlight=gens).

[This version](http://mythtv.wbond.net/gens_for_linux_mythgame_edition/) might be useful to you; I haven't tested it myself though.

---

### Post by Shawn Dineley on 2007-05-19
Yes that is the version I'm using with the patch that should fix the command line stuff without a gui. But I can't get it to work without the gui coming up. 

Thanks though

---

### Post by acoustibop on 2007-05-20
Well, here's a list of switches for Gens, Shawn:
> $ gens --help
Gens for Linux v2.12-rc4
Usage : gens [options]
--help : print this help
--game : ROM to load
--rompath : Path where your roms are stored
--savepath : Path where to save your states files
--srampath : Path where to save your SRAM files
--brampath : Path where to save your BRAM files
--dumppath : unused
--dumpgympath : Path where to save your GYM files
--screenshotpath : Path where to save your screenshot files
--patchpath : Path where to save your patch files
--ipspath : Path where to save your IPS files
--gcofflinepath : unused
--gensmanualpath : unused
--genesisbios : Genesis bios
--usacdbios : US cd bios
--europecdbios : European cd bios
--japancdbios : Japan cd bios
--32x68kbios : 32X Genesis bios
--32xmsh2bios : 32X Master SH2 bios
--32xssh2bios : 32X Slave SH2 bios
--contrast : Contrast (-100 -> 100)
--brightness : Brightness (-100 -> 100)
--window-mode : window mode
Normal : 1
Double : 2
Interpolated : 3
Full Scanline : 4
Scanline 50% : 5
Scanline 25% : 6
Interpolated Scanline : 7
Interpolated Scanline 50% : 8
Interpolated Scanline 25% : 9
2XSai Kreed : 10
AdvanceMAME Scale2x : 11
HQ2X : 12)

--fs-mode : Full screen mode : See window mode for a list of available mode
--frameskip : Frameskip (0 -> 9)
--soundrate : Soundrate (11025, 16000, 22050, 32000, 44100, 48000 kHz)
--msh2-speed : Master SH2 speed
--ssh2-speed : Slave SH2 speed
--ramcart-size : Ram cart size
--enable-stretch, --disable-stretch : Stretch mode
--enable-swBlit, --disable-swBlit : Software blitting
--enable-greyscale, --disable-greyscale : Greyscale
--enable-invert, --disable-invert : Invert color
--enable-spritelimit, --disable-spritelimit : Sprite limit
--enable-sound, --disable-sound : Sound
--enable-soundstereo, --disable-soundstereo : Stereo
--enable-z80, --disable-z80 : Z80
--enable-ym2612, --disable-ym2612 : Yamaha 2612
--enable-psg, --disable-psg : psg
--enable-dac, --disable-dac : Digital to analogic converter
--enable-pcm, --disable-pcm : pcm
--enable-pwm, --disable-pwm : pwm
--enable-cdda, --disable-cdda : cdda
--enable-improved-psg, --disable-improved-psg : psg improved
--enable-improved-ym2612, --disable-improved-ym2612 : ym2612 improved
--enable-improved-dac, --disable-improved-dac : dac improved
--enable-perfectsynchro, --disable-perfectsynchro : Perfect Synchro
--enable-fastblur, --disable-fastblur : Fast blur
--enable-fps, --disable-fps : Frame per second
--enable-message, --disable-message : Message
--enable-led, --disable-led : SegaCD led
--enable-fixchksum, --disable-fixchksum : Fix checksum
--enable-autopause, --disable-autopause : Auto-pause
However, trying --fs-mode followed by one of the window-mode numbers (as indicated) doesn't work for me.

---

### Post by Shawn Dineley on 2007-05-20
It Didn't work for me either.

---

### Post by Shawn Dineley on 2007-05-23
I give up fighting with gens and found that dgen worked much easier. For what I was using it for. But Thanks any ways.

---

