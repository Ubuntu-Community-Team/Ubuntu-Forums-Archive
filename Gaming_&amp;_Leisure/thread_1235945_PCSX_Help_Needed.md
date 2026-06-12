---
title: "PCSX Help Needed"
date: 2009-08-09
forum: Gaming &amp; Leisure
---

### Post by jashuff on 2009-08-09
I am trying to use PCSX, but I am encountering some problems.

First, my keyboard will not work and when I run the progam at the command line, I get the following output:

[B][SIZE=2]Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFIso.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
RGB not found.  Using YUV.
DFInput error: could not open device /dev/input/js0!
DFInput warning: device already initialized.[/SIZE][/B]


The second problem I am having is that while the game is playing the video, I have no sound.  The sound played once the first time I ran the program, but both the video and sound were sped up to about 1.5x their normal speed.  The video looks normal now, but no sound.

The only game I have to run at the moment is Final Fantasy Tactics, so I cannot check if it is the same on all other games.  Some of what I've seen on the internet suggests using pSX, but I cannot even get that program to run for various reasons.

I have been searching the internet for hours to find a solution, and and nothing has worked.  Please help me out!

---

### Post by BoyOfDestiny on 2009-08-09
What are your video settings under the pcsx-df configuration menu? Are you using xv, opengl? Have you tried changing the settings? 
Tick an option regarding frame skip limiting or auto frameskip (fps?)

Are you running PAL (50hz) games or NTSC (60hz)? 

As for the sound, try a different plugin?

---

### Post by jashuff on 2009-08-09
The driver is apparently XVideo Driver 1.1.17.  I'm using NTSC, and I've tried playing with the settings.  I ticked the frame skipping option and it didn't do anything to the video.  Like I said though, the video isn't so much of a problem as the sound and the controller.  I've tried searching for another plugin for sound, but I must be stupid or something because I can't find anything online.  

As to the controller, I have more information now.  When I try to change the keymap, nothing changes and I get this error in the terminal.

Configuring plugin - 8
Configuring plugin /home/jashuff/.pcsx/plugins/libDFInput.so
DFInput: could not open device /dev/input/js0, errno=2
DFInput: no usable input received.

Also, I'm not able to change the bios.  I downloaded a bios, put it in the bios folder, but it won't let me choose it.  I wouldn't be surprised if it's something I'm doing because I can't find anything about it online either.

---

### Post by coldReactive on 2009-08-09
> **jashuff said:**
> Also, I'm not able to change the bios.  [SIZE="7"]I downloaded a bios[/SIZE], put it in the bios folder, but it won't let me choose it.  I wouldn't be surprised if it's something I'm doing because I can't find anything about it online either.

Sorry, but that's illegal.

---

### Post by jashuff on 2009-08-09
Oh?  I wasn't aware.  I'll delete it then.

---

### Post by BoyOfDestiny on 2009-08-10
You can legally dump your own psx bios (one backup), look online for instructions. Luckily, pcsx has a free implementation of the sony bios (called HLE) that works pretty well. So you don't really need the official bios for most games.

Now as for the sound or what not, pcsx-df should come with the plugins you need. I would recommend, backing up your .pcsx folder (press ctrl + h in the file manager to show hidden directories.)

If you delete that folder, it will set the pcsx settings afresh, since you said sound worked once. So with clean settings, try setting the video driver and sound, see how it goes. You aren't stupid, it could be an Ubuntu sound setting or something with pcsx. Hard to tell. It is nice when these things just work, but sometimes just doesn't happen that way I guess...

Sadly, ubuntu has an out of date version of pcsx-df.
[http://pcsx-df.sourceforge.net/](http://pcsx-df.sourceforge.net/)
If you need help building it from source, I can walk you through it.

There has been an update request filed.
[https://bugs.launchpad.net/ubuntu/+source/pcsx-df/+bug/403635](https://bugs.launchpad.net/ubuntu/+source/pcsx-df/+bug/403635)

I'd advise all users who want the latest version in the next Ubuntu, subscribe to this bug.

---

