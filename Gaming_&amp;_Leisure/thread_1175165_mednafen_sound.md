---
title: "mednafen sound"
date: 2009-05-31
forum: Gaming &amp; Leisure
---

### Post by sidious1741 on 2009-05-31
I'm having trouble with mednafen sound.  I've done a lot of searching and know more about the problem but I have not found a solution.  My biggest question would be "What's the difference between '-sounddriver' and '-sounddevice'?"  Mplayer works fine with alsa and pulse.  I know that the alsa driver works but I'm not sure about the sounddevice ("sexyal-literal-default")

```
timothy@timothy-desktop:/media/WD Passport/Tim's HP Backup/home/timothy/Desktop$ mednafen Metroid\ -\ Fusion\ #\ GBA.GBA -sounddriver alsa
Starting Mednafen 0.8.A
 Loading settings from "/home/timothy/.mednafen/mednafen.cfg"...
 Compiled against SDL 1.2.13, running with SDL 1.2.13

 Initializing joysticks...
 Loading Metroid - Fusion # GBA.GBA...

  ROM:       8192KiB
  ROM CRC32: 0x6c75479c
  ROM MD5:   0xaf5040fc0f579800151ee2a683e2e5b5

  Loading cheats from /home/timothy/.mednafen/cheats/gba.cht...
   Error opening file: No such file or directory

 Initializing sound...
  Using "ALSA" audio driver with device "sexyal-literal-default":ALSA Error: snd_pcm_hw_params_any(alsa_pcm, hw_params) Operation not permitted
Error opening a sound device.
Initializing video...
get fences failed: -1
param: 6, val: 0
  Video Mode: 720 x 480 x 32 bpp
  OpenGL: Yes
   Pixel shader: none
  Fullscreen: No
  Special Scaler: None
  Scanlines: Off
  Destination Rectangle: X=0, Y=0, W=720, H=480
  OpenGL Implementation: Tungsten Graphics, Inc Mesa DRI Intel(R) 945G GEM 20090326 2009Q1 RC2 x86/MMX/SSE2 1.4 Mesa 7.4
  Checking extensions:
   GL_ARB_texture_non_power_of_two found.
  Using non-power-of-2 sized textures.
  Checking maximum texture size...
   Apparently it is at least: 2048 x 2048
FLASH emulation disabled by write to:  0e007fe0 0000004d

```

What should I use for the sound device?

---

### Post by BoyOfDestiny on 2009-06-01
> -sounddriver x	string	default	Select sound driver. The following choices are possible, sorted by preference when "default" driver is used, but dependent on being compiled in:

    * oss
    * alsa
    * dsound
    * sdl not recommended, but here if anyone/platform needs it :)
    * jack 

-sounddevice x	string	default	Select sound output device.

ALSA NOTE: When using the alsa driver, the "default" translates to "hw", not "default", before being sent to the ALSA API. This is necessary because ALSA's "default" audio device has very poor buffering control capabilities. If you really want to use ALSA's "default" device, use "sexyal-literal-default".

[http://mednafen.sourceforge.net/documentation/#using-cli](http://mednafen.sourceforge.net/documentation/#using-cli)

When you find the one that works for you, you can change the settings in ~/.mednafen/mednafen.cfg instead of just passing it to commandline every time.

---

### Post by sidious1741 on 2009-06-01
> **BoyOfDestiny said:**
> [http://mednafen.sourceforge.net/documentation/#using-cli](http://mednafen.sourceforge.net/documentation/#using-cli)

When you find the one that works for you, you can change the settings in ~/.mednafen/mednafen.cfg instead of just passing it to commandline every time.

thanx.  I know that.  I just dont know what "sexyal-literal-default" wont work.  alsa works fine on everything else.

---

### Post by wipmonkey on 2009-06-16
I created the file 

~/.asoundrc
```

pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
}

```

base on [http://pulseaudio.org/wiki/PerfectSetup]("http://pulseaudio.org/wiki/PerfectSetup")

That was the only part I did.

Then you must to log out then log in.  It seems that ubuntu's implementation of pluseaudio still isn't quite right.  but is still better than 8.10 :D

tested on 9.04 32bit

---

### Post by BoyOfDestiny on 2009-07-08
You never said if you've got it worked out?

In your mednafen.cfg (here is how mine is.... You can of course try the sexy-literal-default if this still doesn't work)
[quote=mednafen.cfg]
;Select sound driver.
sounddriver default

;Select sound output device.
sounddevice default
[/quote]

Fire up terminal (I prefer to do it this way, you could do it via gui as well)

make a folder called bin in your /home.
```
mkdir bin
```

make a file called mednafen
```
nano mednafen
```

Put this in it
```
#!/bin/bash
pasuspender mednafen "$1"
exit
```

Save (ctrl + o, ctrl + x)

make the file executible 
```
chmod 777 mednafen
```

From now on, running the command mednafen will launch this script, which suspends pulse audio temporarily, and load whatever parameters and/or rom file you pass to it.

P.S. Mednafen 0.8.C is out, you might as well update it too. [http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

---

### Post by sidious1741 on 2009-07-09
Sorry, I kinda forgot about this post.  I tried what you said and that didnt work.  Wont Ubuntu updates take care of mednafen?  The most frustrating thing is that I remember not having these problems before Jaunty (though Jaunty fixed another problem I was having).  When I open System>Preferences>Sound I have the options of

Autodetect
HDA Intel ALC888 Analog (ALSA)
HDA Intel ALC888 Analog (OSS)
HDA Intel ALC888 Analog (OSS)
ALSA
OSS
PulseAudio Sound Server

OSS does not work (It says "Could not test, being used by another application").  ALSA works.  I dont know what Pulse is but I dont see an option for that driver in mednafen.  So since "-sounddriver alsa -sounddevice sexyal-literal-default" wont work, I dont know what to do next.  Do I need to download a different driver?  Or why did mednafen sound work in Intrepid and not Jaunty?

---

### Post by BoyOfDestiny on 2009-07-09
The thing is Ubuntu will only give updates for security stuff, for regular upgrades, you'd have to wait for the next Ubuntu release. 

mednafen 0.8.C in the changelog says it has fixed some sound output problems... 

Here is a deb from me, I've moved to Ubuntu 9.10 alpha though (should still be fine for jaunty at this point...)

[http://rapidshare.com/files/253799846/mednafen_0.8.C-1_i386.deb.html](http://rapidshare.com/files/253799846/mednafen_0.8.C-1_i386.deb.html)

---

### Post by sidious1741 on 2009-07-09
thanks a lot.  Sound now works (without any command line args).  So I have 2 questions still.  What about the new mednafen file or whatever I have from your post two times ago?  What is that?  I'm not a very experienced Ubuntu users but I want to get better.  Should I delete the file?  And where do I learn more about stuff like that?  (I know that's more than 2 but that's actually 1)  Secondly, what was the package you gave me a link to?  I looked on the mednafen site and couldn't find a package, only source (I've had source compieling problems in the past).  I did update synaptic but the latest version was still 0.8.A.

---

### Post by BoyOfDestiny on 2009-07-09
Well, that file (a bash script) before was just a hack, I was thinking the problem was with pulse audio (which I must say is actually working problem free, no tricks needed.) 
The ~/bin folder lets you put scripts and/or executibles there, then run them from any location. 
So that little trick would run the command to suspend pulse audio temporarily, launch mednafen, and the "$1" would pass the parameters (i.e. the rom you wanted to load.)

As for the file I put on rapidshare. I built the latest medafen release from source, used a program called checkinstall to make the deb. The only downside with checkinstall, is that it doesn't list dependencies. So if you didn't have the old mednafen before (including the files it needed to run) it wouldn't fetch them. The nice thing with the deb of course is synaptic is aware of it. So if the next Ubuntu has a newer mednafen, it will update that one seamlessly.

Sorry if this is a bit confusing, I've been using Ubuntu since it came out, so I've learned some tricks over the years, especially when it used to have short comings (i.e. cdrom button doesn't eject when pressed. Laughable nowadays right?)

If you are interested in any of this, I'd say google bash scripting, pulse audio, compilation, and checkinstall. That should about cover it. :) Oh yes, you can delete the file (the .deb you mean?) or the one in ~/bin? You can always recover it from the Trash.

Also, if you need more info just keep asking in the ubuntuforums, people here are very friendly, and will help you.

Cheers.

---

### Post by BatPenguin on 2010-01-27
Just posting to an older thread in case somebody else has problems with Mednafen sounds. I didn't get sound at first and these suggestions didn't work for me. This is with Karmic 64-bit. What did it for me was simply editing the config file and putting "spdif" as the audio device.

Just posting this in case somebody else might have problems with that.

---

### Post by nsacco on 2010-02-14
I'm using Karmic 64, and 'spdif' doesn't work, even though that should be what I'm using anyways.

---

### Post by nsacco on 2010-02-16
I have seemed to gotten a little further; I set my sound device to 'pulse', and now I can see that mednafen is finding the sound correctly.. the game will just freeze on the first frame on the game.

I *sorta* got it all to work once, when I was messing around in the Sound control panel, to see if mednafen would be listed in there while running. It did, and the first time, the game actually ran and I got sound.. for a short time. Then it realized that it was working, and remembered that it doesn't want to work, and stopped itself.

I don't want to try the bash pulse hack posted earlier, because I'm afraid it'll mess with XBMC. That's the entire point I'm doing this; I need an NES emulator than can be launched from XBMC into fullscreen. FCEU(X) fails in this because it won't go to fullscreen correctly from XBMC, but mednafen(fe) does. But I can't get the sound to work. Hell, FCEU(X) are being a pain about that too.. it's all a mess.

---

### Post by bedek on 2011-01-17
Hi,

To start other applications (in my case zsnes and mednafen) I'm using [http://code.google.com/p/xbmc-launcher/](http://code.google.com/p/xbmc-launcher/)

But my problems with XBMC and mednafen are:

1) it doesn't want to run in full screen mode (yes I'm using fs 1 start parameter)
2) sound is not working
3) even if I will start it I don't how to quit it from remote

When I try to run game from command line (when XBMC is turned off) then the game start in full screen mode (fs 1) and sound works fine, also the emulator performance is fine. Looks like XBMC is taking over the control and other apps can't work properly or not performing well.

As workaround I'm planning to be able to choose at startup of my media centre to choose if I want to run XBMC or Emulator - I'm just not sure what app can be used to be able to choose from remote.

---

### Post by bedek on 2011-01-17
I'll also create new thread - maybe someone will have some fresh idea how to solve this problem:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1669047](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1669047)

---

### Post by bedek on 2011-01-17
> **bedek said:**
> I'll also create new thread - maybe someone will have some fresh idea how to solve this problem:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1669047](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1669047)

I've found this solution on xbmc forum, looks promising:
[http://forum.xbmc.org/showthread.php?t=86630&page=2](http://forum.xbmc.org/showthread.php?t=86630&page=2)

---

### Post by bedek on 2011-01-17
> **bedek said:**
> I've found this solution on xbmc forum, looks promising:
[http://forum.xbmc.org/showthread.php?t=86630&page=2](http://forum.xbmc.org/showthread.php?t=86630&page=2)

And one more describing how to shut down emulator (from gamepad)
[http://forum.xbmc.org/showthread.php?t=86630](http://forum.xbmc.org/showthread.php?t=86630)

---

### Post by bedek on 2011-01-18
> **bedek said:**
> And one more describing how to shut down emulator (from gamepad)
[http://forum.xbmc.org/showthread.php?t=86630](http://forum.xbmc.org/showthread.php?t=86630)

Also have a look to this thread, it resolved most of the problems:
[http://forum.xbmc.org/showthread.php?p=659443#post659443](http://forum.xbmc.org/showthread.php?p=659443#post659443)

---

