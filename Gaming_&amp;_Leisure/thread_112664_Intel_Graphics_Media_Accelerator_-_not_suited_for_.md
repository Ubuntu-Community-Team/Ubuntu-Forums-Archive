---
title: "Intel Graphics Media Accelerator - not suited for gaming on Linux?"
date: 2006-01-04
forum: Gaming &amp; Leisure
---

### Post by Wermut on 2006-01-04
With my graphics card (Intel GMA) I can play Age of Empires 3 on Windows with decent performance, but I wonder why I can't get 3D games working nicely in Ubuntu. DeusEx with Cedega is simply unplayable. I tried running a native Linux game (Nexuiz), the performance is the same.
Running glxgears gives me ~5000 FPS, is that good or bad?
On the Intel Website I can download their drivers for XFree86. Are they going to improve 3D performance? Can I install them with X.org? Or is it impossible to play 3D games with my card at a reaseonable frame rate on Linux?

---

### Post by slux on 2006-01-06
5000fps from glxgears does not sound too bad but you should check that you are indeed accelerated by running "glxinfo | grep renderer" and see if it says something different to "Mesa GLX Indirect".

 I don't thin k you can install the XFree86 drivers but you shouldn't need to either with a sufficiently new X as I think intel is one of the few that actually release the source to their accelerated drivers as well.

I don't have much experience with the card you are using so I can't say much about how it is supposed to perform on Linux.

---

### Post by Wermut on 2006-01-06
glxinfo tells me:
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
Maybe something is wrong with these sections in xorg.conf?
Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
Section "Device"
        Identifier      "Intel Corporation Intel Default Card"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection
Section "DRI"
        Mode    0666
EndSection

---

### Post by knubbe on 2006-01-07
[QUOTE=Wermut]glxinfo tells me:
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20050225
Maybe something is wrong with these sections in xorg.conf?
..
..
[/QUOTE]

I have exactly the same settings. My problem is that it seems like if the built-in intel driver doesnt support scaling. 

Example 1: If i set a higher resolution in my games (well, wolfenstein: enemy territory, to be exact) the "game-size" gets smaller.

Example 2: If i run mplayer and choose "double size" the movies itself doesnt get bigger, only the mplayer window.

However.. There are actually new Intel drivers released on intel.com now (on the 5th of january 2006). But in the readme it says they are for suse? Anyone who knows something about this?

---

### Post by knubbe on 2006-01-07
Maybe i should add i only get 1000-1100 fps in glxgears (dell inspiron 6000, 1.4ghz, 2gb ram, i915 video chipset).

---

### Post by Lord Illidan on 2006-01-07
Dunno. You get 5000 fps.. My geforce 6800 (on a 4x agp mobo) gives me 4000 fps, yet i played AoE 3 in Windows quite well.

Have you tried anything else.. like UT 2004 demo?

---

### Post by Perfect Storm on 2006-01-07
Got a GF4 ti4600 and have a fps around 4500. Thougj I can run anything I through into my computer nicely.

---

### Post by miscz on 2006-01-07
[QUOTE=knubbe]Example 2: If i run mplayer and choose "double size" the movies itself doesnt get bigger, only the mplayer window.[/QUOTE]
This can be fixed by changing output to "xv".

---

### Post by slux on 2006-01-08
You have to remember that glxgears isn't a real benchmark at all - it's extremely simple so it's pretty much only useful for verifying that you have some sort of acceleration.

Nexuiz can be really taxing with some settings on and Deus Ex should not really require almost anything from the graphics card. Like others have said, I think you should try some other native stuff. Enemy Territory comes to mind as a reasonably undemanding game. How's sound been for you when you've tested these games?

I guess It's also possible that the Xorg drivers simply aren't very good at all but that would seem strange because they're coming straight from intel and a graphics card driver that can't handle Deus Ex seems like a complete waste of time.

---

### Post by knubbe on 2006-01-08
[QUOTE=miscz]This can be fixed by changing output to "xv".[/QUOTE]

ah, thanks! :-)

---

### Post by leech on 2006-01-09
[QUOTE=slux]You have to remember that glxgears isn't a real benchmark at all - it's extremely simple so it's pretty much only useful for verifying that you have some sort of acceleration.

Nexuiz can be really taxing with some settings on and Deus Ex should not really require almost anything from the graphics card. Like others have said, I think you should try some other native stuff. Enemy Territory comes to mind as a reasonably undemanding game. How's sound been for you when you've tested these games?

I guess It's also possible that the Xorg drivers simply aren't very good at all but that would seem strange because they're coming straight from intel and a graphics card driver that can't handle Deus Ex seems like a complete waste of time.[/QUOTE]

Deus Ex is pretty old, but still does require hardware acceleration.  Let's be blunt here, the Intel graphics cards aren't exactly power houses, not to mention Deus Ex runs through Wine, so it's not very likely to run as smoothly as under windows even.  

I think what it comes down to more than anything is what features of hardware acceleration does the Intel chips provide.  I'm sure they don't provide the full 2.0 OpenGL specks, and probably not even all of the 1.3 OpenGL stuff.  glxinfo will tell you exactly what is supported.  

Leech

---

### Post by nalmeth on 2006-01-09
I had a really hard time getting 3D going when I was using breezy amd64. The i810 driver was selected by default, but didn't seem to activate any sort of acceleration! I use i386 now, and the driver works. The native 3D-apps work pretty well, but nexuiz is terrible, and I don't quite expect anything really hardcore to run well at all. My built-in card is supposedly 128 megs, but its performance is mediocre. 
When I was trying to install drivers from intels site, I was directed by a fellow ubuntuer to use the i810, because it would be more up to date. 
Is this acurate?

---

### Post by slux on 2006-01-10
[QUOTE=leech]Deus Ex is pretty old, but still does require hardware acceleration.  Let's be blunt here, the Intel graphics cards aren't exactly power houses, not to mention Deus Ex runs through Wine, so it's not very likely to run as smoothly as under windows even.  

I think what it comes down to more than anything is what features of hardware acceleration does the Intel chips provide.  I'm sure they don't provide the full 2.0 OpenGL specks, and probably not even all of the 1.3 OpenGL stuff.  glxinfo will tell you exactly what is supported.  

Leech[/QUOTE]

The original Unreal engine (with slight enhancements from UT) which Deus Ex uses worked on a Voodoo Banshee (I'd say the original Voodoo but that fiddling with a lot of settings and wasn't perfect). It is heavily CPU bound and doesn't require much at all from the CPU. I've personally played with a Geforce 2 MX under WINE but have no doubt that it would work with less. So I think it's safe to say that Deus Ex should work even though Wine does incur a performance penalty  (and it isn't mainly directed to the graphics card). The problem is most definitely not that the card isn't capable - after all AOE3 works well and that is a 3D accelerated game released in 2005.

---

### Post by poofyhairguy on 2006-01-11
[QUOTE=slux]The problem is most definitely not that the card isn't capable - after all AOE3 works well and that is a 3D accelerated game released in 2005.[/QUOTE]

Its not all the card's fault. Its partially the driver's fault.

The only cards in Linux that have drivers that come anywhere NEAR the performance of their Windows counterparts are the closed Nvidia ones.

Thats why that Geforce worked well.

---

### Post by leech on 2006-01-11
[QUOTE=slux]The original Unreal engine (with slight enhancements from UT) which Deus Ex uses worked on a Voodoo Banshee (I'd say the original Voodoo but that fiddling with a lot of settings and wasn't perfect). It is heavily CPU bound and doesn't require much at all from the CPU. I've personally played with a Geforce 2 MX under WINE but have no doubt that it would work with less. So I think it's safe to say that Deus Ex should work even though Wine does incur a performance penalty  (and it isn't mainly directed to the graphics card). The problem is most definitely not that the card isn't capable - after all AOE3 works well and that is a 3D accelerated game released in 2005.[/QUOTE]

I just had a thought (amazing, I know...), but Deux Ex: Invisible War pretty much ran like a dog's ass on carpet when it first came out.  It was all about the settings in the engine.  It's quite possible that Wine has issues with Deus Ex on the Intel cards because of settings in Deus Ex itself.  Of course this is just a theory, but is a viable one.  I know to get WoW and other games working right, you have to tweak some of the config files.  

If you haven't already, I'd check [www.winehq.com](www.winehq.com) for information on getting it to run better.

Leech

P.S. On the voodoo chipsets it does utilize the GPU a lot more than the CPU, I know that at least with the original Unreal because it while it ran OK in software mode without a Voodoo, it looked like crap and only ran in lower resolutions.  Of course the Voodoo 1 was limited to 800x600, but it looked fantastic for the day (I still think Unreal looks fantastic by today's standards, but maybe that's just me, I load it up occasionally in Linux still :D

Leech

---

### Post by leech on 2006-01-11
"One of the worst problems I ran into with Deus Ex was the high system requirements. Deus Ex ran choppy even on some of the higher end computers we played it on. I had to turn the detail down on my PII450MHz with a Voodoo3 to get a fluid framerate, but after I installed one of the new Voodoo5s, it was smooth sailing with full detail. Of course, I hope we're not getting to the point where you have to own a PIII600 with a $300 video card to play a good PC game quite yet."

That's from an old review of Deus Ex.  I don't know how far Intel's video chipsets have come, but I don't think they're quite Voodoo5 (which is kind of sad for how old the Voodoo5 is, but then I could be way off base here.  But at least if you had a Voodoo5, you could use Glide, which was quite fast.)

Leech

---

### Post by slux on 2006-01-11
[QUOTE=poofyhairguy]Its not all the card's fault. Its partially the driver's fault.

The only cards in Linux that have drivers that come anywhere NEAR the performance of their Windows counterparts are the closed Nvidia ones.

Thats why that Geforce worked well.[/QUOTE]

I'm well aware of the fact that Nvidia provides quality drivers and ATI does not but had no real info about intel performance. Still, my point stands. Deus Ex requires nearly nothing from the graphics card.

The reviewer that Leech quoted was most likely rather clueless. The UT engine makes very little use of the GPU and no significant performance gains can be achieved even on a modern Nvidia GeForce 7800GT compared to that old 2 MX.

---

### Post by leech on 2006-01-11
Are you saying that I could put a Matrox G200 (which has full open sourced drivers in it, and are quite robust) and play Unreal Tournament on it in 1600x1200 with everything set at max as long as I have a 2ghz computer?  

That may work if I'm using software mode, but software mode is quite ugly, and if I recall correctly, Deus Ex requires hardware acceleration.

The fact of the matter is, all integrated video chipsets suck for playing games.  They simply don't support all the features that the ATI and nVidia add on cards support.

I probably could run UT on my G200, but it wouldn't be in max resolution or anything.  I had Soldier of Fortune running on it (the native version).

Leech

---

### Post by slux on 2006-01-11
[QUOTE=leech]Are you saying that I could put a Matrox G200 (which has full open sourced drivers in it, and are quite robust) and play Unreal Tournament on it in 1600x1200 with everything set at max as long as I have a 2ghz computer?  

That may work if I'm using software mode, but software mode is quite ugly, and if I recall correctly, Deus Ex requires hardware acceleration.

The fact of the matter is, all integrated video chipsets suck for playing games.  They simply don't support all the features that the ATI and nVidia add on cards support.

I probably could run UT on my G200, but it wouldn't be in max resolution or anything.  I had Soldier of Fortune running on it (the native version).

Leech[/QUOTE]

A G200 is far slower than this card.  Last time I played UT'99 a few years back, nothing could really run it smoothly at 1600x1200 because there weren't sufficient advances in CPU power but while G200 is very old and might actually be a problem, I think the GMA would not be a bottleneck for it at all.

Check out these benchmarks for reference:
[http://www.extremetech.com/article2/0,1558,1617356,00.asp](http://www.extremetech.com/article2/0,1558,1617356,00.asp)
[http://www.xbitlabs.com/articles/chipsets/display/i915g_4.html](http://www.xbitlabs.com/articles/chipsets/display/i915g_4.html)

It's not exactly a speed demon by todays standards but it can run even UT2004.

---

