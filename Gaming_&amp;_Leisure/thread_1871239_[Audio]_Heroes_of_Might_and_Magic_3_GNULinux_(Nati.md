---
title: "[Audio] Heroes of Might and Magic 3 GNU/Linux (Native)"
date: 2011-10-28
forum: Gaming &amp; Leisure
---

### Post by askrym on 2011-10-28
Hi all,

 I have (i386) ubuntu 10.10 on a small netbook.

 I decided to install the Linux version of the game Heroes of Might and Magic 3, I downloaded and installed without any problems. But then when I started I noticed that there was no audio. I tried to launch the game from the terminal
output:
 "Couldn't open audio:"

 I searched a lot on the internet and as far as i've understood; the problem is due to the fact that when the game was ported to Linux, the sound daemon was different from what it's now.

 Is there a way to make it work?
 (I even tried the windows version on wine but I get problems with the integrated Intel GPU .. the game does not even launch)

 Thanks in advance.:KS

---

### Post by askrym on 2011-10-29
I kept searching through google and I think I found something but it is in French and I did not understand very well by translating it with google-translator. But it seems that the guy who posted says he has finally solved the problem.

does somebody clearly understand what he did to make the sound work?
[http://forum.ubuntu-fr.org/viewtopic.php?id=408386](http://forum.ubuntu-fr.org/viewtopic.php?id=408386)     :confused:

----
i tried running the game with padsp as well, but i get the same error regarding audio.
"Couldn't open audio:"

---

### Post by Frenziefrenz on 2011-10-29
I don't know anything about what kind of sound architecture the game is expecting, but it might be simpler (albeit less "pure") to run the game in Wine or DOSBox? (Assuming the CD-ROM comes with both)

---

### Post by askrym on 2011-10-29
I've already tried running it by Wine, personally I just want it to be working, don't care if through wine or using the linux version.

The problem when i try running it through wine is this :

fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
...
...


basically it isn't running because of intel cards having cheap and poor drivers compared to their windows counterparts and thus not completely supported for 3d stuff, so i'm getting this error in wine.

Thus i decided to focus on the linux version since it's at least launching fine, and only audio is not working.

---

### Post by Frenziefrenz on 2011-10-29
When you tried padsp did you try something like this? Does the game specify anywhere whether it expects OSS or ALSA?

```
padsp -n Heroes -d heroes3
```

Where -n names it so you can see it in e.g. pavucontrol and -d does debugging output.

---

### Post by askrym on 2011-10-29
> -----------------------
(1) SYSTEM REQUIREMENTS
-----------------------
  Linux capable computer, Pentium class processor or better
  Linux kernel version 2.2.x
  32 MB RAM
  4x CD-ROM drive
  Video card capable of 800x600 resolution
  XFree86 version 3.2 or newer at 16 bpp.
  /dev/dsp sound device for audio
    (the Enlightenment Sound Daemon is supported as well).
  150 MB free hard disk space


```
padsp -n Heroes -d ./homm3.sh 
Couldn't open audio:
```

I've also tried pasuspender by the way:

```
pasuspender -- ./homm3.sh
Couldn't open audio: 
X Error:  BadValue
  Request Major code 129 (XFree86-VidModeExtension)
  Request Minor code 10 ()
  Value 0x4e00013
  Error Serial #163
  Current Serial #165
```

---
killing all pulseaudio does not any better as well.

---

### Post by Frenziefrenz on 2011-10-29
> /dev/dsp sound device for audio
 (the Enlightenment Sound Daemon is supported as well).
The first sounds like padsp should work, the second sounds like PA itself should work, possibly with the aid of esdcompat. I've never used the latter, however; I only have (some) experience with padsp. It seems to me that the game should have some kind of configuration file in order to choose between /dev/dsp and ESD?

---

### Post by askrym on 2011-10-29
the only reference to sound stuff I've found while reading the readme file of the game is this:

> - DMA sound from the latest SDL (better performance). If your card supports
      this (most SB compatible cards do), you can enable it by setting the
      SDL_AUDIODRIVER environment variable to 'dma', i.e. :

      export SDL_AUDIODRIVER=dma

but i had already given it a try , setting it to esd (yes i have the SDL ESD libs installed).

it still says it cannot open sound. :(

---

### Post by Frenziefrenz on 2011-10-30
I found some stuff that might help.

[http://ubuntuforums.org/showthread.php?t=743723](http://ubuntuforums.org/showthread.php?t=743723) (it speaks of applying some kind of patch; also from it I conclude that configuration files should reside in ~/.loki)
[http://forum.vcmi.eu/portal.php](http://forum.vcmi.eu/portal.php)

---

### Post by askrym on 2011-10-30
luckily mine has already been patched up to 1.3.1a   :)

about ~./loki/...

i've found just saved games, game preferences (those set through the option menu within the game i think) , stack trace for bug reports and other stuff . nothing about setting which mode to launch with for audio.

I've looked up on vcmi website and downloaded the archive, it contains windows stuff , unfortunatly it's kind of useless for my system since wine isnt launching any games for that videocarddriver thing.
I'm still google-ing to find a way to redirect the game audio access to pulse or so.

---

### Post by mateo14 on 2011-10-30
> **askrym said:**
> I've looked up on vcmi website and downloaded the archive, it contains windows stuff , unfortunatly it's kind of useless for my system since wine isnt launching any games for that videocarddriver thing.
I'm still google-ing to find a way to redirect the game audio access to pulse or so.

[https://vcmi.svn.sourceforge.net/svnroot/vcmi/trunk/README.linux](https://vcmi.svn.sourceforge.net/svnroot/vcmi/trunk/README.linux)

---

