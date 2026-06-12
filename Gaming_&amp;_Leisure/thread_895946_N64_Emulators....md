---
title: "N64 Emulators..."
date: 2008-08-20
forum: Gaming &amp; Leisure
---

### Post by zx6r1033 on 2008-08-20
I am having some issues with any of the N64 emulators I have tried. I started with Mupen64, which decided it hates me and won't work anymore. Then I moved on to Project64, which won't allow me to configure my gamepad. 

Does anyone have any good working emulators that will run either in Linux or through Wine?

---

### Post by linuxguymarshall on 2008-08-20
I use project 64 with all my gamepads. What gamepad are you using?

---

### Post by tuxxy on 2008-08-20
damn I wanna play Goldeneye now! maybe I need a game pad too :lolflag:

---

### Post by linuxguymarshall on 2008-08-20
Just hack a gamepad togeather. I hacked my N64 controller into a USB controller with easy to switch end pieces so I can go from N64 controller jack to USB in a second

---

### Post by tuxxy on 2008-08-20
> **linuxguymarshall said:**
> Just hack a gamepad togeather. I hacked my N64 controller into a USB controller with easy to switch end pieces so I can go from N64 controller jack to USB in a second

Damn, I have an N64 pad here too! how did you convert it to USB exactly

---

### Post by linuxguymarshall on 2008-08-20
I originally had a converter but that broke so I stripped the wires and looked inside the converter to see how it worked. I just built a more ghetto version. Google "Turn Xbox controller into USB" I have not done it in a while but I am pretty sure it is the same concept.

---

### Post by linuxguymarshall on 2008-08-20
zx6r, 

I just found a nice emulator called Mupen. It is working amazingly. Might want to try that out

---

### Post by zx6r1033 on 2008-08-20
The gamepad is a generic PS2-clone I found on eBay. It works good with my nes/snes/genisis/ps1/ps2 emulators as well as linux and windows games, so that rules out a faulty pad. 

linuxguy - I started off with Mupen64. I tried to correct the problems I was having for two days before I abandoned it. It looked nice, though.

---

### Post by FranMichaels on 2008-08-20
Instead of using Mupen64, try [Mupen64Plus]("http://code.google.com/p/mupen64plus/") it is much much better and actively updated.

---

### Post by grossaffe on 2008-08-20
mupen64 is discontinued, look for mupen64plus.

---

### Post by doorknob60 on 2008-08-20
+1 for Mupen64plus :)

---

### Post by zx6r1033 on 2008-08-20
I tried Mupen64plus. It won't even let me change the input plugin, test, or configure. :(

---

### Post by FranMichaels on 2008-08-21
What does that mean though?

I've successfully used it with a ps2 controller with usb converter and logitech dual shock (and keyboard/mouse...)

Also, how did you install mupen64plus? Built from source, a deb from some site? What version did you try. Please be more specific in your posts, you will get better help this way.

Anyway, it's a very nice emulator. 

Here is a snapshot of my configuration settings, try those, and see if that helps. :KS

P.S. "Config" works fine with that input plugin, a window pops up and lets you assign buttons etc...

---

### Post by zx6r1033 on 2008-08-21
I've been trying to run Mupen64Plus 1.4.  I can't change the configuration on the input. It is locked on the standard mupen input. It won't let me do anything at all with it. 

I didn't install it. I asked about installing in another thread, and the collective responses were that the program doesn't get installed... you run it from whatever file you download. 

I got it from [Here.]("http://http://code.google.com/p/mupen64plus/")

---

### Post by FranMichaels on 2008-08-21
A good place to get it, as that's mupen64plus homepage :) I got the source release from that site and compiled instead, but... 

Looking at the README included with the binary release, I'd suggest those that replied to your question read it. Always, always, read the README.

As there is a file called install.sh. The readme has instructions for installing the one you downloaded.

[I]*Binary Distribution*

To install the binary distribution of Mupen64Plus, su to root and run the provided install.sh script:[/I]

```

  su
  ./install.sh
  exit 

```

*The install script will copy the executable to /usr/local/bin and a directory called /usr/local/share/mupen64plus **will be created to hold plugins and other files used by mupen64plus**.*

Emphasis mine.

Hope that resolves it.

---

### Post by zx6r1033 on 2008-08-21
Still can't do anything with the configuration.   I think it's a lost cause.

---

### Post by FranMichaels on 2008-08-21
Darn, I see. 
Does running ```
mupen64plus
``` from terminal provide any sort of output when you try doing the configuration?

---

### Post by Orlsend on 2008-08-21
for me Mupen ran ok... a Bit laggy..., MupenPlus dint even ran in any of my Linux distros....Project64 on wine is the thing i got to emulate...

---

### Post by zx6r1033 on 2008-08-21
> **FranMichaels said:**
> Darn, I see. 
Does running ```
mupen64plus
``` from terminal provide any sort of output when you try doing the configuration?

Sure does. It gives me a "failed to load" on all of the input drivers. 


I tried reinstalling... no luck.

---

### Post by FranMichaels on 2008-08-21
Hmm. How about after installing,

```
sudo ldconfig
```

---

### Post by doorknob60 on 2008-08-22
Crap double post ](*,)

---

### Post by doorknob60 on 2008-08-22
*sigh*
```
sudo aptitude install libsdl-ttf2.0-0
```

---

### Post by Modax42 on 2008-09-06
I too am unable to get any N64 emulators to work.  I have tried Mupen64, Mupen64plus, and Project64 under WINE, and haven't even gotten as far as a title screen with any of them.

Back when this computer was running Windows XP, I used the project64 emulator all the time, so I know that I have the necessary hardware.  When I run Mupen64plus in the terminal and try to play Super Mario 64, the emulator immediately crashes and I get the following message in the terminal:

Compression: Uncompressed
Imagetype: .z64 (native)
Rom size: 8388608 bytes (or 8 Mb or 64 Megabits)
MD5: 20B854B239203BAF6C961B850A4A51A2
80 37 12 40
ClockRate = f
Version: 1444
CRC: 635a2bff 8b022326
Name: SUPER MARIO 64
Manufacturer: Nintendo
Cartridge_ID: 4d53
Country: USA
PC = 80246000
EEPROM type: 0
init timer!
memory initialized
[RiceVideo] SSE processing enabled.
[blight's SDL input plugin]: version 0.0.10 initialized.
[RiceVideo] SSE processing enabled.
[RiceVideo] Found ROM 'SUPER MARIO 64', CRC ff2b5a632623028b-45
InitExternalTextures
Initializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 640x480...
Warning, xpress200 detected.
DRI R300 Project - Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL : 1.3 Mesa 7.0.3-rc2
[RiceVideo] OpenGL Combiner: Basic OGL
[JttL's SDL Audio plugin] version 1.4 initalizing.
[JttL's SDL Audio plugin] Initializing SDL audio subsystem...
[JttL's SDL Audio plugin] Allocating memory for audio buffer: 65536 bytes.
Could not construct face from /usr/share/mupen64plus/fonts/font.ttf
Starting r4300 emulator
R4300 Core mode: Dynamic Recompiler
mupen64plus: r300_emit.c:403: r300EmitArrays: Assertion `((inputs_bitset)[((_TNL_ATTRIB_COLOR0) / (sizeof (GLuint) * 8))] & (1 << ((_TNL_ATTRIB_COLOR0) % (sizeof (GLuint) * 8))))' failed.
Aborted


I've tried playing with every single option in the program's gui, but no dice.  I'm totally at a loss.  :confused:

P.S   Why the hell did smilies show up in the error message when i copied it here?

---

### Post by Modax42 on 2008-09-07
As I mentioned before I've also tried running project64 under WINE, but my results haven't been much better.  With the standard plugins, playing Mario 64 gives me working sound and responsive controls, but no picture.

So then I tried the gln64 graphic plugin, but when i run any game i get the error message  "Win32 exception 0x80000101 occured in gln64 v0.4.1" and the emulator crashes.

I also tried using the ricevideo plugin, but when I installed it under WINE, Project64 gives me the error message "Failed to load plugin"

I'm really stuck here!

---

### Post by doorknob60 on 2008-09-07
> **Modax42 said:**
> I too am unable to get any N64 emulators to work.  I have tried Mupen64, Mupen64plus, and Project64 under WINE, and haven't even gotten as far as a title screen with any of them.

Back when this computer was running Windows XP, I used the project64 emulator all the time, so I know that I have the necessary hardware.  When I run Mupen64plus in the terminal and try to play Super Mario 64, the emulator immediately crashes and I get the following message in the terminal:

Compression: Uncompressed
Imagetype: .z64 (native)
Rom size: 8388608 bytes (or 8 Mb or 64 Megabits)
MD5: 20B854B239203BAF6C961B850A4A51A2
80 37 12 40
ClockRate = f
Version: 1444
CRC: 635a2bff 8b022326
Name: SUPER MARIO 64
Manufacturer: Nintendo
Cartridge_ID: 4d53
Country: USA
PC = 80246000
EEPROM type: 0
init timer!
memory initialized
[RiceVideo] SSE processing enabled.
[blight's SDL input plugin]: version 0.0.10 initialized.
[RiceVideo] SSE processing enabled.
[RiceVideo] Found ROM 'SUPER MARIO 64', CRC ff2b5a632623028b-45
InitExternalTextures
Initializing OpenGL Device Context
(II) Initializing SDL video subsystem...
(II) Getting video info...
(II) Setting video mode 640x480...
Warning, xpress200 detected.
DRI R300 Project - Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL : 1.3 Mesa 7.0.3-rc2
[RiceVideo] OpenGL Combiner: Basic OGL
[JttL's SDL Audio plugin] version 1.4 initalizing.
[JttL's SDL Audio plugin] Initializing SDL audio subsystem...
[JttL's SDL Audio plugin] Allocating memory for audio buffer: 65536 bytes.
Could not construct face from /usr/share/mupen64plus/fonts/font.ttf
Starting r4300 emulator
R4300 Core mode: Dynamic Recompiler
mupen64plus: r300_emit.c:403: r300EmitArrays: Assertion `((inputs_bitset)[((_TNL_ATTRIB_COLOR0) / (sizeof (GLuint) * 8))] & (1 << ((_TNL_ATTRIB_COLOR0) % (sizeof (GLuint) * 8))))' failed.
Aborted


I've tried playing with every single option in the program's gui, but no dice.  I'm totally at a loss.  :confused:

P.S   Why the hell did smilies show up in the error message when i copied it here?

Did you read the post above you? Looks like it might fix the issue, not positive though.
```
sudo aptitude install libsdl-ttf2.0-0
```

---

### Post by Modax42 on 2008-09-07
Thank you very much; I only just now realized that this was applicable to my problem and that I am a MORON for ignoring it. :biggrin: This command improves the situation, but I had to decrease the resolution to 320x240  and enable frame-skipping to get a playable frame rate, there are various rendering artifacts on the screen, and the audio cuts in and out, but I guess its better than nothing!

---

### Post by Steveway on 2008-09-07
> **Modax42 said:**
> Thank you very much; I only just now realized that this was applicable to my problem and that I am a MORON for ignoring it. :biggrin: This command improves the situation, but I had to decrease the resolution to 320x240  and enable frame-skipping to get a playable frame rate, there are various rendering artifacts on the screen, and the audio cuts in and out, but I guess its better than nothing!

The bad performance is because you do use Mesa:
> DRI R300 Project - Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL : 1.3 Mesa 7.0.3-rc2
You need to install another driver that can use the opengl-capabilities of your graphics-card.

---

### Post by Modax42 on 2008-09-07
> **Steveway said:**
> The bad performance is because you do use Mesa:

You need to install another driver that can use the opengl-capabilities of your graphics-card.

That's good to know :) 
Does anyone know where I might find such drivers?



However, I just found out that the emulator only functions when I'm logged into the root account.  In my regular account we're back to square 1, with the emulator crashing as soon as I launch the game. ](*,) I may be a newbie but I _have_ gathered that its not a good practice to be logged in as root all the time!

---

### Post by hessiess on 2008-09-07
> Does anyone know where I might find such drivers?

what card have you got?

---

### Post by Modax42 on 2008-09-07
> **hessiess said:**
> what card have you got?

Oh, right.  Its a radeon xpress 200m.  I'm looking at ATI's site.  They only have Linux drivers for radeon xpress 200, not the 200m.  Will that do? Otherwise I guess I'll have to try installing the Linux drivers under WINE.  But won't those only be of use for games under WINE like Project64?  Maybe P64 will work once I have those windows drivers...

---

### Post by Modax42 on 2008-09-07
Still no luck.  I tried installing the WinXP drivers for my xpress200m under WINE, but project64 still doesn't get a picture, and trying to end the emulation causes my system to lock up and I need to do a hard reboot.

I also installed the catalyst drivers for Linux, but now Mupen64plus doesn't work at all.  Even weirder, whenever I launch a ROM now, the screen goes blank and it throws me right out of my session, and dumps me at the login screen.

What's going on here? :confused:

---

### Post by hessiess on 2008-09-08
Drivers won't work under WINE, it runs in user space, not kernal space(has no direct acsess to the hardwere)

Have you tryed the ristricted drivers from the restricted drivers manager or or the envy script?

I dont have any expiriance with ATI cards, as ive always explicitly avoided them, due to the large number of 'ati driver problem' related threds on this and outher forums. Intel and NVidia cards tend to have the best drivers.

---

### Post by Modax42 on 2008-09-10
Well I got the 'Envy' thing which is supposed to automatically get the drivers for my graphics from the synaptic package manager, but still no dice.

Just as an experiment, I tried downloading some 3D linux games from the repos, and, no surprise, 3D performance on this computer is still non-existent.

It doesn't make sense because when this computer was running xp, I could play Neverwinter Nights, Homeworld 2, and Project64 without any trouble.

I've been thinking about getting a new pre-installed ubuntu laptop from System 76 or Dell for a while now.  But I would first really like to know if these computers can have the same sorts of issues with 3D support before I buy anything.

---

### Post by hessiess on 2008-09-10
> **Modax42 said:**
> Well I got the 'Envy' thing which is supposed to automatically get the drivers for my graphics from the synaptic package manager, but still no dice.

Just as an experiment, I tried downloading some 3D linux games from the repos, and, no surprise, 3D performance on this computer is still non-existent.

It doesn't make sense because when this computer was running xp, I could play Neverwinter Nights, Homeworld 2, and Project64 without any trouble.

I've been thinking about getting a new pre-installed ubuntu laptop from System 76 or Dell for a while now.  But I would first really like to know if these computers can have the same sorts of issues with 3D support before I buy anything.

basicly, ATI's Linux drivers suck:(, stick with nvidia for the time being. a pre-installed laptop should work OK.

---

### Post by phantom3113 on 2008-12-14
Hi all, after reading these posts I went and got Mupen64Plus and tried it out some. It's working alright, but I was just wondering if there was a way to fix screen flicker? I've got an ATI Radeon X1200 and I'm aware of all the ATI problems and such. Just thought I'd ask in case there was a way.

---

