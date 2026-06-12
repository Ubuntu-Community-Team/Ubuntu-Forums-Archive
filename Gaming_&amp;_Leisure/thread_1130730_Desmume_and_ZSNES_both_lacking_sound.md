---
title: "Desmume and ZSNES both lacking sound?"
date: 2009-04-20
forum: Gaming &amp; Leisure
---

### Post by Noise... on 2009-04-20
I'm guessing the issue isn't with the emulators, as both lack sound. 

What can I do to fix this? I have sound everywhere else in Ubuntu.

---

### Post by hikaricore on 2009-04-20
What kinda output do you get when you run them from a terminal?

---

### Post by Noise... on 2009-04-20
> **hikaricore said:**
> What kinda output do you get when you run them from a terminal?

I haven't tried. To be honest, I'm new to Linux, and have no idea how to do that. :(

---

### Post by Nevon on 2009-04-20
> **Noise... said:**
> I haven't tried. To be honest, I'm new to Linux, and have no idea how to do that. :(

If you installed from a package you should just be able to run
```
zsnes
```
or
```
desmume
```
respectively from the terminal. Also, you should probably install a newer version of desmume, as the one in the repositories is pretty old. For instructions on how to do that (there's even a precompiled package that may work for you), go [here]("http://www.blastfromthepast.se/blabbermouth/2009/04/console-emulation-in-linux-part-1-nintendo-family/#NDS") and scroll down to the part where it says "Installation".

However, the problem probably isn't with the emulators themselves. But running them from the terminal might give you some kind of error message that can tell you were the problem lies.

---

### Post by Noise... on 2009-04-20
Ok. Here's the output for both emulators.

```
desmume
Microphone successfully inited.
SoftRast Initialized
Already decrypted.

ROM serial: ANIMAL CROSS_ADME01

Changing master brightness outside of vblank
Changing master brightness outside of vblank
Changing texture or texture palette mappings outside of 3d vblank
Changing texture or texture palette mappings outside of 3d vblank
Changing texture or texture palette mappings outside of 3d vblank
Changing master brightness outside of vblank
Changing master brightness outside of vblank
Changing texture or texture palette mappings outside of 3d vblank
Changing texture or texture palette mappings outside of 3d vblank

```

The last line is repeated a lot more, but that's it.

```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event11. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.

```

Zsnes actually shows the Audio working, yet there's no sound.

Any ideas?

---

### Post by Nevon on 2009-04-20
> **Noise... said:**
> ```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event10. Make sure you have read permissions to it.
Unable to poll /dev/input/event11. Make sure you have read permissions to it.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 32000

ZSNES could not find any joysticks.

```

Zsnes actually shows the Audio working, yet there's no sound.

Any ideas?

On my machine the driver used is Simple DirectMedia Layer (SDL), but ALSA should work just fine. Have you tried going into the audio menu in the emulator and going crazy with the different options?

---

### Post by Noise... on 2009-04-20
> **Nevon said:**
> On my machine the driver used is Simple DirectMedia Layer (SDL), but ALSA should work just fine. Have you tried going into the audio menu in the emulator and going crazy with the different options?

Yes. Still nothing. It's just odd, as I have sound everywhere else - also in my NES emulator.

Also, I just tried VisualBoy Advanced, and it lacks sound as well. :(

---

### Post by wingnux on 2009-04-20
Try running: zsnes -ad sdl

---

### Post by Noise... on 2009-04-20
Nevermind on Visualboy. I only had my headphone jack turned on. 

I'll try that for Zsnes now.

---

### Post by Noise... on 2009-04-20
> **wingnux said:**
> Try running: zsnes -ad sdl

That worked for Zsnes. Will the normal Zsnes in my menu launch with sdl sound now, or will I need to launch from Terminal every time?

---

### Post by Nevon on 2009-04-20
> **Noise... said:**
> Will the normal Zsnes in my menu launch with sdl sound now, or will I need to launch from Terminal every time?

No. It won't launch with sound, however, the fix is very simple. Just right click on your applications menu and choose "edit menus". Then go to the games category and find Zsnes, right click on it and choose "properties". Now just change the command part from whatever it says to "zsnes -ad sdl" without the quotes.

---

### Post by Noise... on 2009-04-20
Ok. Great. Now Zsnes is fixed. How about DeSMume? Animal Crossing just isn't as much fun with no sound. :(

---

### Post by Grishka on 2009-04-20
> **Nevon said:**
> No. It won't launch with sound, however, the fix is very simple. Just right click on your applications menu and choose "edit menus". Then go to the games category and find Zsnes, right click on it and choose "properties". Now just change the command part from whatever it says to "zsnes -ad sdl" without the quotes.

hey, why did you say that? there's no need for such acrobatics. running zsnes once with this option will set it for good, it's written to the configuration file.

---

### Post by Noise... on 2009-04-20
> **Grishka said:**
> hey, why did you say that? there's no need for such acrobatics. running zsnes once with this option will set it for good, it's written to the configuration file.

He was actually correct. I did test it prior to the "acrobats" of the three clicks and entering 6 characters, and it didn't save.

Can anyone help me with DeSMume?

---

### Post by Grishka on 2009-04-20
> **Noise... said:**
> He was actually correct. I did test it prior to the "acrobats" of the three clicks and entering 6 characters, and it didn't save.

Can anyone help me with DeSMume?

uh? that's odd. it should write the configuration automatically to ~/.zsnes/zsnesl.cfg. it was always like that, maybe you got some other version or something. anyway, your desmume log shows no audio errors. you sure you clicked "enable audio" in the "emulation" tab? also, try a different game and see if it still gives no sound.

---

### Post by Noise... on 2009-04-21
Ok - I sort of solved DeSMume's issue. If I launch it from Terminal, it will have sound. If I launch it from the menu, it won't. I checked, and the command on it in the menu is the same exact thing I type in, but from the menu launcher, it lacks sound. 

I don't really mind launching it from terminal, but I am still curious on why it would have audio when launched from terminal and not when launched from the menu.

---

### Post by talz13 on 2009-05-02
I am also missing sound on zsnes... I installed from the 8.10 package ([http://packages.ubuntu.com/intrepid-updates/amd64/zsnes/download](http://packages.ubuntu.com/intrepid-updates/amd64/zsnes/download)), and everything looks great but sound.  When I launch it from the cli it doesn't even show anything about loading sound!

```
jeff@server:~/.zsnes$ zsnes -ad sdl
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 4 mice detected.
Using ManyMouse for:
Mouse 0: Honey Bee  Nostromo SpeedPad2 
Mouse 1: Logitech USB Receiver
Device 0 HORI CO.,LTD. REAL ARCADE PRO.3
  4 axis, 13 buttons, 1 hats, 0 balls
```

I noticed that if I use "zsnes -ad auto" it segfaults until I run it with -ad sdl again. -ad alsa, -ad oss, and -ad pulse all say that they are invalid audio driver selections, so it's either segfault or use sdl.

I have checked that zsnes does, in fact, have sound enabled, and that it is using the default settings (32kHz, gaussian, etc.)

---

