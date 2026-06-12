---
title: "[SOLVED] GFCE emulator and Ur-Quan master draining ALL of my resources"
date: 2008-05-27
forum: Gaming &amp; Leisure
---

### Post by malachi1990 on 2008-05-27
I noticed it today, but neither the GFCE Nes emulator or the Ur-Quan Masters games work anymore.  I've used both of them before, but:

GFCE: Displays the window for the game, but stays black

Ur-Quan: the window briefly appears (~1 second) before closing.  

In both cases, however, they then take up all of my computer's (significant) resources.

I have a Geforce 7150 gpu, with the driver enabled.

Many thanks for any help I can get.

---

### Post by 4th guy on 2008-05-27
Could you please post the terminal output by running the games from the terminal?

To run games from terminal:
Applications > Accessories > Terminal

type uqm and press enter to run Ur-Quan Masters (and copy whatever output is given off and paste it here)

I don't know the command for the NES emulator, but someone who knows might come along.

---

### Post by acoustibop on 2008-05-27
Also, what are the specs of your machine, malachi1990?

---

### Post by malachi1990 on 2008-05-27
This is for the uqm:

The Ur-Quan Masters v0.6.2 (compiled Nov 25 2007 15:51:43)
This software comes with ABSOLUTELY NO WARRANTY;
for details see the included 'COPYING' file.

Netplay protocol version 0.3. Requiring remote UQM version 0.5.4.
Initializing base SDL functionality.
Using SDL version 1.2.12 (compiled with 1.2.11)
Using config dir '/home/jordan/.uqm/'
Using '/usr/share/games/uqm/content' as base content dir.
Saved games are kept in /home/jordan/.uqm/save/.
Initializing Pure-SDL graphics.
SDL driver used: x11
SDL initialized.
Initializing Screen.
Set the resolution to: 640x480x32
Screen scalers are using optimized C code
0 joysticks were found.
Initializing SDL audio subsystem.
ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave
SDL audio subsystem initialized.
Opening SDL audio device.
Unable to open audio device: No available audio device
Sound driver initialization failed.
This may happen when a soundcard is not present or not available.
NOTICE: Try running UQM with '--sound=none' option

My machine is an Hp Pavillion dv2000 with a dual core 3Ghz processor, 3GB ram, 250 GB hard drive, Geforce 7150 gpu, 64-bit AMD Turion,  need anything else?

---

### Post by arfink on 2008-05-27
A tip I found out of my machine- check what graphics drivers the program wants to use. I use mednafen for emulating things, and the openGL performance is bad. I choose to use the SDL option instead, since SDL gets hardware acceleration anyway. I think in both those games you can append a command line option or change their config files to use SDL instead of openGL. Running in the terminal can also reveal any other possible problems, as most programs will output error messages only to the terminal.

---

### Post by 4th guy on 2008-05-27
Hmmm, looks like problems with the sound. Does audio still play correctly in other programs?

Does the game run with uqm --sound=none ?

---

### Post by 4th guy on 2008-05-27
Hmmm, looks like problems with the sound. Does audio still play correctly in other programs?

Does the game run with uqm --sound=none ?

EDIT: Sorry for the double post. How do I delete it?

---

### Post by malachi1990 on 2008-05-27
Yeh, it runs without sound just fine, and every other application runs ok.  I've even turned off Rhythmbox and tried to start it, because my box is a bit temperamental about letting two programs that need sound run at the same time (at least in ubuntu, I didn't have that particular problem in kubuntu). The other odd thing is that I can only run it properly from terminal.

As to the double post, I haven't got a clue.

---

### Post by malachi1990 on 2008-05-27
Well, it seems that as long as I don't run anything else, these programs run fine.  Don't know what caused the change in behavior, though.

---

### Post by arfink on 2008-05-29
Yeah, the problem is that the programs are set to use OSS by default- OSS is really finnicky, and only allows one program to use the sound device at a time. Even using Alsa or PulseAudio simulation of OSS the programs that use it still complain, because it's required to share the sound card with other programs. It's just bad programming- maybe try another program instead, or bother the developers to fix their sound code.

---

