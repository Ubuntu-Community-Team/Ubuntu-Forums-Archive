---
title: "NES emulator with a GUI"
date: 2006-03-09
forum: Gaming &amp; Leisure
---

### Post by deathbyswiftwind on 2006-03-09
Hey I was just wondering if anyone has found a good nes emulator that has a gui. Ive tried many terminal ones but I would really like to find one with a gui because im gonna be setting up ubuntu on my dads computer and hes not really "computer smart".

---

### Post by akiro.yamamoto on 2006-03-09
You can try this:
[http://fms.komkon.org/iNES/](http://fms.komkon.org/iNES/)

---

### Post by albinoloverats on 2006-03-09
zsnes, either found in the repositories or [zsnes.com]("http://zsnes.com"), i believe it plays nes roms aswell as those for the snes.

---

### Post by daveg on 2006-03-09
[QUOTE=albinoloverats]zsnes, either found in the repositories or [zsnes.com]("http://zsnes.com"), i believe it plays nes roms aswell as those for the snes.[/QUOTE]

Incorrect albinoloverats, zsnes only plays Super Nintendo roms.

If you want to play NES roms, and you want an emulator with a GUI, you'll have to install [fakenes]("http://fakenes.sourceforge.net/"). I installed my copy from the [repositories on fbriere.net]("http://www.fbriere.net/debian/"). Add this into your /etc/apt/sources.list

```
deb http://www.fbriere.net/debian/dists/unstable ./
```

Then the usual apt-get update; apt-get install fakenes

---

### Post by blue cube on 2006-03-09
how the hell do you run it after its installed

(newbe here haha)

---

### Post by blue cube on 2006-03-09
[QUOTE=blue cube]how the hell do you run it after its installed

(newbe here haha)[/QUOTE]


EDIT - was tring to use it from su. durr.

---

### Post by deathbyswiftwind on 2006-03-09
I dunno if anyone is interested but I found a pretty nice emulator. Its called ROCKnes [http://rocknes.kinox.org/](http://rocknes.kinox.org/) . I tried the fakenes and it kept crashing my gdm dunno why but I didnt feel like messing with it :D So now I can play pirates and excite bike \\:D/

---

### Post by daveg on 2006-03-09
Just to note, to get RockNES going, I had to install liballegro4a

```
sudo apt-get install liballegro4a
```

---

### Post by BoyOfDestiny on 2006-03-09
Gotta recommend mednafen, it doesn't have a "GUI" persay, but you can configure stuff like inputs while in a game (similar to mame). Main things I like are soft-patching, fastfoward/rewind, and handles other systems (and runs well for me in 32 and 64-bit)

"Mednafen is a portable, utilizing OpenGL and SDL, argument(command-line)-driven multi-system emulator with many advanced features. The Atari Lynx, GameBoy, GameBoy Color, GameBoy Advance, NES, PC Engine(TurboGrafx 16), and SuperGrafx are emulated. Mednafen has the ability to remap hotkey functions and virtual system inputs to a keyboard, a joystick, or both simultaneously. Save states are supported, as is real-time game rewinding. Screen snapshots may be taken at the press of a button, and are saved in the popular PNG file format." GPL of course.

Here is a little screen cap:

[[IMG]http://img350.imageshack.us/img350/8647/screenshot28tp.th.png[/IMG]](http://img350.imageshack.us/my.php?image=screenshot28tp.png)

---

### Post by dpaint4 on 2006-03-10
[QUOTE=BoyOfDestiny]Gotta recommend mednafen, it doesn't have a "GUI" persay, but you can configure stuff like inputs while in a game (similar to mame). Main things I like are soft-patching, fastfoward/rewind, and handles other systems (and runs well for me in 32 and 64-bit)

"Mednafen is a portable, utilizing OpenGL and SDL, argument(command-line)-driven multi-system emulator with many advanced features. The Atari Lynx, GameBoy, GameBoy Color, GameBoy Advance, NES, PC Engine(TurboGrafx 16), and SuperGrafx are emulated. Mednafen has the ability to remap hotkey functions and virtual system inputs to a keyboard, a joystick, or both simultaneously. Save states are supported, as is real-time game rewinding. Screen snapshots may be taken at the press of a button, and are saved in the popular PNG file format." GPL of course.

Here is a little screen cap:

[[IMG]http://img350.imageshack.us/img350/8647/screenshot28tp.th.png[/IMG]](http://img350.imageshack.us/my.php?image=screenshot28tp.png)[/QUOTE]

I'd really like to try this. I've been looking for a good PC Engine emulator ever since I left XP last week. So far it's the only thing I'm really missing.

Says on their site that I need to add 'the testing repository' (there's only one?) to my apt sources list. I get what that means, but I don't know how to do that and the statement seems vague to me. It's a noob request I'm sure, but I'm a nice guy so I hope someone will humor me and point me in the right direction. I thought I'd enabled all available repositories via Synaptic Package Manager. How do I add the testing repository?

Thanks in advance! You're helping out a really big PC Engine fan.

---

### Post by daveg on 2006-03-10
I haven't tried out mednafen yet, but for PC Engine emulation, I've been using Hu-Go!

At this line to your /etc/apt/sources.list:
```
# Hu-Go!
deb http://www.zeograd.com/debian/ unstable main
```

Then apt-get install hugo

---

### Post by daveg on 2006-03-10
[QUOTE=dpaint4]Says on their site that I need to add 'the testing repository' (there's only one?) to my apt sources list. I get what that means, but I don't know how to do that and the statement seems vague to me. It's a noob request I'm sure, but I'm a nice guy so I hope someone will humor me and point me in the right direction. I thought I'd enabled all available repositories via Synaptic Package Manager. How do I add the testing repository?[/QUOTE]
Its talking about adding in the debian testing repository to your apt sources list, but you really don't want to add that in on a ubuntu box. Your only option is to either compile it from source, unless somebody has created a .deb package for ubuntu.

---

### Post by BoyOfDestiny on 2006-03-11
[QUOTE=dpaint4]I'd really like to try this. I've been looking for a good PC Engine emulator ever since I left XP last week. So far it's the only thing I'm really missing.

Says on their site that I need to add 'the testing repository' (there's only one?) to my apt sources list. I get what that means, but I don't know how to do that and the statement seems vague to me. It's a noob request I'm sure, but I'm a nice guy so I hope someone will humor me and point me in the right direction. I thought I'd enabled all available repositories via Synaptic Package Manager. How do I add the testing repository?

Thanks in advance! You're helping out a really big PC Engine fan.[/QUOTE]

I'm going to build a deb (from within dapper 64 [chroot]... should work :)) Here are the dependencies needed to build it (incase you'd like to try it yourself, and it will install the libs the app needs too...)

sudo apt-get install libcdio-dev libvorbisfile3 libogg-dev libvorbis-dev libsdl1.2-dev libsdl-net1.2-dev libsndfile1-dev zlib1g-dev


you install it like 

sudo dpkg -i mednafen_0.5.2-1_i386.deb

[http://www.safaribans.com/gpl/mednafen_0.5.2-1_i386.deb](http://www.safaribans.com/gpl/mednafen_0.5.2-1_i386.deb)

---

### Post by daveg on 2006-03-11
I'm getting this error when I try to run it :-( Was this built against dapper?
```
# mednafen
mednafen: error while loading shared libraries: libcdio.so.6: cannot open shared object file: No such file or directory
```

---

### Post by BoyOfDestiny on 2006-03-11
[QUOTE=daveg]I'm getting this error when I try to run it :-( Was this built against dapper?
```
# mednafen
mednafen: error while loading shared libraries: libcdio.so.6: cannot open shared object file: No such file or directory
```[/QUOTE]

Yeah... I did run an older version in breezy though... Try sudo apt-get install libcdio6? I didn't put in any dependencies for the deb (so it would just install), I think you should be able to get it done with what is  in the breezy repos... If it complains about other stuff, search for it in synaptic... I think that will do the trick :)

Here are the dependencies

Depends: libc6 (>= 2.3.4-1), libcdio6, libgcc1 (>= 1:4.0.2), libgl1-mesa | libgl1, libogg0 (>= 1.1.3), libsdl-net1.2, libsdl1.2debian (>> 1.2.7+1.2.8), libsndfile1, libstdc++6 (>= 4.0.2-4), libvorbis0a (>= 1.1.2), libvorbisfile3 (>= 1.1.2), libx11-6, zlib1g (>= 1:1.2.1)

I'm not sure if breezy has libstdc++6... Good luck though =)

Oh yeah... [http://www.safaribans.com/gpl/mednafen_0.3.2-1_i386.deb](http://www.safaribans.com/gpl/mednafen_0.3.2-1_i386.deb)
There is my old deb I built on my laptop while it had breezy... Several months out of date though... :(

---

### Post by dpaint4 on 2006-03-11
Wow thanks to everyone for the input and advice! Learned a lot. Saved a few text files of your notes and discussion. Gonna try Hu-Go. I've heard of that, and in fact I think the PC Engine emulator that I use on my GP2X is based on it, so if that's the case, then I already know the speed and compatibility are ace. 

Thanks again for the help.

---

### Post by pagefault on 2006-03-16
I would recommend fakenes.sourceforge.net

---

### Post by joshuapurcell on 2006-03-16
If you like fceUltra, then you may try this:
[http://ubuntuforums.org/showthread.php?t=107040](http://ubuntuforums.org/showthread.php?t=107040)

---

### Post by bleep on 2006-03-20
Hello, I have a few questions, I hope someone can help.

 I've been trying to figure out how to install mednafen for a few weeks now.  Is there a step by step guide somewhere?

Also, I saw FCE Ultra and Nestra in Synaptec, and installed them.  They work, I typed the name of the app and name of the rom and luckily that was the correct syntax, but I cannot get my controllers to work with them.

I have orginal NES controllers wired to the parallel port as indicated on many NES mod sites and this one text file I found.  I hope I didn't get them backwards as they aren't too specific about which side they are refering too.  I have a mini itx board inside a real NES case, so using original controllers is kind of the point.  I also installed a few things that looked like joystick drivers in synaptec, but that didn't help.  Not sure if I'm supposed to do something after installing them, or even where they installed to.

What is the most active and best working emulator for NES?  Is there a way to boot into a game select screen instead of Ubuntu Desktop, so that I don't have to have a keyboard connected to my NES?

---

### Post by tommygeorge on 2006-10-25
(I know it's been a long time, but in case someone else stumbles on this thread...)

bleep, 
I had the same problem when I first set up FCE Ultra. I had no idea how to set up the controllers.
I haven't checked into doing it from the command line, but with the Universe Repositories enabled, use Synaptic and search for "gfceu" (I think). It's a graphical front end that lets you select the rom file to run, and set up the mappings for controllers.

I haven't tried with a real controller yet, but with the keyboard (and I've only been using this for about 30 minutes) you select the controller to set up (generally number one, if it's just you playing) and a title bar will come up. Hit the button (on the keyboard/controller) that corresponds to the one named in the title bar.

 I think you have to hit it a second time to confirm... After it goes through all of the possible NES controller buttons, the title bar disappears, and you can hit "launch" or whatever - if you've already selected the ROM file.

---

### Post by Praill on 2009-07-24
Personally I use VirtualNES through wine. It runs flawlessly out-of-the-box with wine version 1.1.26. The only modification I had to make was in the virtualNES settings. I had to change sound from 8bits to 16bits to get clear sound.

You can download VirtualNES and every single nintendo game ever made from here:
[http://thepiratebay.org/torrent/4531936/NES_Emulator_for_PC_and_758_Games_(Kingdom-games_by_KloWn_](http://thepiratebay.org/torrent/4531936/NES_Emulator_for_PC_and_758_Games_(Kingdom-games_by_KloWn_))


PS. I hope I don't get any flak for this link. The NES franchise is 100% dead so I don't really consider this pirating.

---

