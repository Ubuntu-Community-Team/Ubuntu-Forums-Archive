---
title: "Game Boy Advance Emulator?"
date: 2005-02-11
forum: Gaming &amp; Leisure
---

### Post by Jaivaz on 2005-02-11
I'm sorry if it's against the rules but...

I've been looking for some emulators but none of them work...Well actually... I just can't install them for some reason. I got pretty far on Gnome Boy Advance, but I needed to "Become root and run: python setup.py install" and...I couldn't do that, I did do "python <directory>/setup.py install" and I got this error...

> Traceback (most recent call last):
  File "/home/horace/Desktop/gnomeboyadvance/setup.py", line 11, in ?
    from distutils.core import setup
ImportError: No module named distutils.core


So..help please.

---

### Post by evangelion on 2005-02-11
Looks like you need to install a python module called "distutils". You can try your luck at using a Debian Patato package, [here](http://www1.apt-get.org/search.php?query=distutils&submit=&arch%5B%5D=i386&arch%5B%5D=all),  or you [build it yourself](http://www.python.org/sigs/distutils-sig/download.html).  The Patato package is a recent version, so I'd give that  a try first just because it's probably easier.

---

### Post by RastaMahata on 2005-02-12
Just download it from here: [http://vba.ngemu.com/downloads.shtml](http://vba.ngemu.com/downloads.shtml)

Place it in a folder (/home/NAME/vba/), and be happy.

The latest version with a Linux port is Version 1.7.1

[http://prdownloads.sourceforge.net/vba/VisualBoyAdvance-1.7.1-SDL-linux-glibc22.tar.gz?download](http://prdownloads.sourceforge.net/vba/VisualBoyAdvance-1.7.1-SDL-linux-glibc22.tar.gz?download)

---

### Post by Jaivaz on 2005-02-12
I've tried VisualBoyAdvance, but it closes the second it opens.

---

### Post by RastaMahata on 2005-02-13
its a command based version. go to the folder you decompressed it, and then run this:
```
$ ./VisualBoyAdvance rom.zip
```
replacing rom.zip for the rom you want to play. Sometimes savegames get corrupted, so you better use Shift+F[1-8] to save, and F[1-8] to load.
Be sure to check the commands available:
```
$ ./VisualBoyAdvance --help
```

---

### Post by Jaivaz on 2005-02-14
It works just fine now, but I can't get the sound to work and because of this the speed is..insane. (200+ o.o;)

---

### Post by Maelgwyn on 2006-02-13
I've attempted installing each and every emulator I can find in Synaptic, but even when it says they're installed, I can't find them to run anything with! :S

---

### Post by glisteringwaters on 2007-03-05
I'm using VisualBoyAdvance 1.7.2 and this is how I made the speed 100%:

Go to _O_ptions, _F_rameskip, _T_hrottle and select 100%.

If there is no 100% option, select _O_ther and type in 100%.

Regarding the sound problem, I have no idea which permutation of options would make the emulator sound "right".
I am able to play the .ogg files that came with my ubuntu distro so I guess I have to find out how to configure the emulator for my hardware.

This is how I installed my vba:
> **no1wantdthisname said:**
> ```
sudo apt-get install visualboyadvance
gvba
```

> **Jaivaz said:**
> It works just fine now, but I can't get the sound to work and because of this the speed is..insane. (200+ o.o;)

---

### Post by DoktorSeven on 2007-03-05
VBA is slow because of no hardware drawing to screen.  Try Mednafen.
[http://mednafen.sourceforge.net](http://mednafen.sourceforge.net)

---

### Post by glisteringwaters on 2007-03-05
DoktorSeven, thank you for suggesting an alternative to vba =)

I searched the forums and managed to learn how to install and run mednafen.
I'm really impressed by the quality delievered by mednafen.
In my opinion, the graphics and sound of gba roms emulated by mednafen are much better than that of vba on ubuntu linux.

However, I found it difficult to understand how to configure mednafen:

$ mednafen --help (this returns a lot of stuff that I don't really understand..)

Is there a way to manipulate saving and loading of a game like in vba?

For example, in vba I could speed up the game by depressing the space bar, create and load multiple save-states by pressing shift+F1/2/3/4 or ctrl F1/2/3/4 respectively.

Does mednafen provide similar, if not better functionality?

Through trial and error, I found out about some of the commands in mednafen for gba roms:
F1   toggle state rewinding functionality (?)
F2   "Press a command key now" (?)
F3   setup controls
F4   setup controls (also?)
F5   state (0) saved (save)
F6   (?)
F7   state (0) loaded (load)
F8   (?)
F9   snapshot
F10 reset
F11 reset
F12 quit (ESC also quits)

May I know where to find more digestable information on how to use mednafen?
(I feel really handicapped without a GUI user interface.. hehe)

-thanks

---

### Post by DoktorSeven on 2007-03-05
Speedup is the ~ key
States are set by pressing one of the number keys and F5/F7 saves/loads that state.

[http://mednafen.sourceforge.net/documentation/#using-keys](http://mednafen.sourceforge.net/documentation/#using-keys) has key information on mednafen :)

---

### Post by glisteringwaters on 2007-03-06
Thanks a lot!
I'm sure many people using ubuntu will benefit from this information when they want to replay their old cartridges/roms =D

---

### Post by Marche00 on 2007-11-18
sorry to dig up a old topic but how do you get medafen to run at all? its installed and in a file but how do I get it to go? I opened the file but there is no launcher and I typed "mednafern" into the terminal but all I got was:
Starting Mednafen 0.8.1
 Loading settings from "/home/marche/.mednafen/mednafen.cfg"...
No command-line arguments specified.

Usage: mednafen [OPTION]... [FILE]
        Please refer to the documentation for option parameters and usage.


im sorry but what do I do to get a rom going ): (gba please)

---

### Post by disturbedite on 2007-11-19
careful asking about roms, thats liable to get the thread locked.

but mednafen is a command line program, so you have to tell it what to do via commands you type in.

vba w/ vba express work fine for me.

---

### Post by itnet7 on 2010-06-06
Thanks for posting this, sound worked right off the bat, and it the application runs roms perfectly. 

I am currently using Lucid, and wanted to let everyone new that reads this thread no that mednafen is in the repos, and has been for quite a while, rmadison shows:

  mednafen | 0.8.7-1        | hardy/universe  | source, amd64, i386
  mednafen | 0.8.A-0ubuntu1 | jaunty/universe | source, amd64, i386
  mednafen | 0.8.C-0ubuntu1 | karmic/universe | source, amd64, i386
  mednafen | 0.8.C-0ubuntu2 | lucid/universe  | source, amd64, i386
  mednafen | 0.8.C-0ubuntu2 | maverick/universe | source, amd64, i386

It's awesome to see that they have already packaged it for Maverick! Thanks to DoktorSeven and glisteringwaters, without your suggestion and feedback, I would still be playing my emulators with less than good sound quality! 

:guitar: 

Chris Crisafulli
itnet7

---

