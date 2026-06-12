---
title: "I'm New to Ubuntu, and need help! (Linux versions of Windows programs)"
date: 2005-10-19
forum: Desktop Environments
---

### Post by dsnow on 2005-10-19
Hello! My name is daniel, and I am new to ubuntu. In fact, I'm new to Linux, and any type of open source software. I was wondering if the programs I had with windows will work with Ubuntu. I have some music production softwares, and some graphic softwares. If it helps, I will list them below, maybe they've already been tried. Thanks for your help!  dsnow
 Softwares:
 WinAmp
 Reason 3.0.4
 Rebirth 2.0.1
 Recycle 2.1
 Adobe Photoshop 7
 Blender 2.4 (open source!)
 3D studio max 5

---

### Post by Ampersand on 2005-10-19
xmms and beep-media player are both quite similar to winamp, there are also a few other music/media players available.
Blender is also available from the ubuntu repositories.
For the others, you might be able to get open source equivelents, the Gimp (which comes preinstalled) is probably the closest to photoshop. Some of the programs may work in Wine or one of the other windows emulators, see this thread for details: [http://ubuntuforums.org/showthread.php?t=56892](http://ubuntuforums.org/showthread.php?t=56892).

---

### Post by dsnow on 2005-10-19
I checked out that link, and it helped a lot! thanks for hooking me up! I didn't know there was anything like that out there!

                                                                 -dsnow

---

### Post by az on 2005-10-19
You may also use the package manager (it is called synaptic) to search the package database for software you need.

Instead of searching for certain titles, enter generic terms (like "browser" or "web") instead of names of proprietary software and you will see what you can install in a few clicks.  Enable the universe repository to access something like 13000 packages.

A lot of what is available in free software is in universe.

---

### Post by mrmcctt on 2005-10-19
You could also try [this site.]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")  It has a lot of what I think is good info on windows equivelant software for linux.

---

### Post by abou on 2005-10-19
For Photoshop there are several versions of The GIMP that can be used. There is vanilla GIMP, a version of GIMP modified to look a lot like Photoshop (cannot remember website), and the fork CinePaint, which was formerly known as FilmGIMP.

While they are not as "easy" to use as Photoshop, they really are just as good, if not better considering CinePaint is used in many motion picture studios - including WETA.

---

### Post by Sirin on 2005-10-19
[QUOTE=dsnow]Hello! My name is daniel, and I am new to ubuntu. In fact, I'm new to Linux, and any type of open source software. I was wondering if the programs I had with windows will work with Ubuntu. I have some music production softwares, and some graphic softwares. If it helps, I will list them below, maybe they've already been tried. Thanks for your help!  dsnow
 Softwares:
 WinAmp
 Reason 3.0.4
 Rebirth 2.0.1
 Recycle 2.1
 Adobe Photoshop 7
 Blender 2.4 (open source!)
 3D studio max 5[/QUOTE]

You can install these from Synaptic. Note that you must first have the Universe repositories enabled.

 WinAmp = XMMS
 Reason 3.0.4 = Audacity (Unsure, but in relation to)
 Rebirth 2.0.1 = Audacity (Unsure, but in relation to)
 Recycle 2.1 = Audacity
 Adobe Photoshop 7 = The GIMP (Preinstalled on your system - 'Applications -> Graphics -> GIMP Image Editor)
 Blender 2.4 (open source!) = Well, Blender actually. :D  
 3D studio max 5 = Blender

---

### Post by Cathbard on 2005-10-20
There are quite a few sequencing/recording packages around for Linux. Here's some with their links.

[Muse]("http://muse-sequencer.org/") - Audio and midi         
[Rosegarden]("http://www.rosegardenmusic.com/") - Audio and midi  
[Ardour]("http://www.ardour.org/") - Audio (multi-track)  
[Hydrogen]("http://www.hydrogen-music.org/?p=main") - Drum machine 

Have a look at Sourceforge, there is a plethora of toys to play with. The two links below will take you straight to the section you are interested in.
[Sourceforge Sound/Audio]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=113")
[Sourceforge MIDI]("http://sourceforge.net/softwaremap/trove_list.php?form_cat=248")

You will also want to hjave a look at the [Jackd server]("http://www.djcj.org/LAU/jack/") to tie them all together. 

Have fun

---

### Post by Cathbard on 2005-10-20
If I can just add...........

I struggled with recording on Winblows for years and there are two things that REALLY irritated me.
1. Latency.......any type of low latency in windows comes at a HUGE price which leads me to annoyance 2
2. Windows was forever deciding that it had things to do that were more important than my recording and would just go off and do it. Do you know how annoying it is to play that inspired lead break only to have it destroyed because XP thought it was time to flush the swap file or look for an update or report home or......... ?

A friend of mine still uses an Atari with version 2 of Cubase because it doesn't hiccup all the time like his windows box. One day I'll get him into linux but that's another story. Another friend went and spent squillions on a mac for the same reason.

Linux will give you a low latency system that will do what YOU want, not what Bill Gates thinks you need. It may take you a while to get the hang of it all but persevere, it's worth it. I have a lot to learn about it too.

There is also a distro you may want to have a squizz at. It is called [Musix]("http://www.musix.org.ar/"). It is a live cd that comes bundled with heaps of music apps pre-packaged. It is an Argentinian distro so it is hard to get support in English but there is an [Englkish wiki]("https://www.musix.org.ar/wiki/index.php/Documentation"). It's based on knoppix/kanotix so you can run it as a live cd and it will detect just about anything. Alternatively you can install it on another partition as an alternate boot to your Ubuntu. It may be worth downloading just so you can have a play before changing your current system in any way.

---

