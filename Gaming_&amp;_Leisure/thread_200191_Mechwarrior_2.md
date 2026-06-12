---
title: "Mechwarrior 2"
date: 2006-06-19
forum: Gaming &amp; Leisure
---

### Post by keithjr on 2006-06-19
I ran a search and I can't seem to find anybody on this forum who's gotten Mechwarrior 2 (the greatest computer game ever made) to work in Wine.  What's even more troubling is that google doesn't turn anything up either.  I'd love to have been the first to get it to work but alas, my linux luck has never been that good.

When I pop in the cd, I try the following just to get the installation to run
```

mount /media/cdrom0
wine /media/cdrom0/install.exe
```

And I get the following error:
```

err:int31:DOSVM_Int31Handler int31: unknown/not implemented parameters:
int31: AX 8001, BX 1d70, CX 0000, DX 1fb8, SI 0fa8, DI 0001, DS 0001, ES 1fb8
```

I say "error" in the singular sense, but this error flies across my screen over and over again so I can't really say if there's any printout before it. 

What in the world am I doing wrong?  I set up everything according to the linux-gamers How-To on Wine, but that how-to has several explanation in the form of "Download this, Then a Miracle Happens, And You're Done!"  So perhaps I messed something up in there...?

---

### Post by minisori on 2006-06-20
There is nothing in wine database about this game, but Mechwarriors 3 and 4 seem to not work in wine.

[http://appdb.winehq.org/search.php?q=Mechwarrior](http://appdb.winehq.org/search.php?q=Mechwarrior)

You can become a maintainer of the game there if you want and add it to the database, posting the bugs and maybe someday they will get fixed.

> err:int31:DOSVM_Int31Handler int31: unknown/not implemented parameters:
int31: AX 8001, BX 1d70, CX 0000, DX 1fb8, SI 0fa8, DI 0001, DS 0001, ES 1fb8

I think there are multiple versions of mechwarrior 2, the one you using seem dos version?? If so you could try dosbox, maybe there works.

EDIT: 
I just looked it up and yes, it works in dosbox.
[http://dosbox.sourceforge.net/](http://dosbox.sourceforge.net/)

But there may be parches for winxp around, try to grab one of those and use it with wine, but you would have to copy the game manually, without installer.

[http://en.wikipedia.org/wiki/MechWarrior_2](http://en.wikipedia.org/wiki/MechWarrior_2)

---

### Post by keithjr on 2006-06-20
D'oh, you're right, I remember (from deeply fond childhood memories) running this  game via dos.  I tried to get it working with dosbox last year in windows XP, and it would never detect my CD drive and had serious problems with sluggishness.  I suppose I could give it another go.

I was thinking about indeed becoming a maintainer but didn't think I could justify it until I got the game working at least.

---

### Post by HAARP on 2006-06-20
Is cr***ing legal for games as old as that ones? If yes, I can help you getting them to work with Dosbox.
But it's still very slow

---

### Post by minisori on 2006-06-20
[QUOTE=keithjr]D'oh, you're right, I remember (from deeply fond childhood memories) running this  game via dos.  I tried to get it working with dosbox last year in windows XP, and it would never detect my CD drive and had serious problems with sluggishness.  I suppose I could give it another go.

I was thinking about indeed becoming a maintainer but didn't think I could justify it until I got the game working at least.[/QUOTE]

YOu dont need to get the game working to be a maintainer, most of them just dont do. Mostly its about try every new release if it works and post the bugs...

But well has to be windows version :P

---

### Post by keithjr on 2006-06-20
[QUOTE=HAARP]Is cr***ing legal for games as old as that ones? If yes, I can help you getting them to work with Dosbox.
But it's still very slow[/QUOTE]

You know, I do in fact legally own this game...:rolleyes: 

So I say anything I do to it is legal.

I found a nice guide for it here:
[http://vogons.zetafleet.com/viewtopic.php?t=7728&highlight=mechwarrior](http://vogons.zetafleet.com/viewtopic.php?t=7728&highlight=mechwarrior)

But it is rather dependent on windows being the OS of choice.  I have no idea how I'd even apply an executable patch without some way to run non-windows executables.  

You're saying it's still very slow, maybe you're where I was last year, running but not really...  Man, will I ever play this game again...
:-(

---

### Post by HAARP on 2006-06-21
Well, I don't want me, nor this board to get into trouble for helping someone cr*ck a game that old ;) Although i doubt that anyone would care.
Using DosBox, it is slow indeed. Can't use anything but 320x240, and it won't run fast enough to be well playable. (3200+ CPU)
Only solution would be Win/DOS (VMware? fast enough?) When I still had 2k (native), it ran quite fast (after some tweaking)

What's the matter with the guide? You can do that stuff on linux, too. Tell me what your problem is, I will try to help. You apply the patch in DosBox, and hexedit the file under linux with a Hex Editor program of your choice :)

---

### Post by keithjr on 2006-06-21
Upon further review, you are quite right.  I've just been used to installing games manually (and patching as such) in windows and using dosbox with D-Fend (very nice frontend) to run the setup (if appplicable) and game executables.  Didn't know it had the versitility to run any kind of executable.  I got the patch but wine once again refuses to work with it, of course.  

Although, if it indeed is that slow I might just have to give up on it and wait till I put together a windows 95 machine from scrap parts.  

What's your favorite 'nix hex editor, by the way?  Just asking 8)

---

### Post by HAARP on 2006-06-21
Oh well, I don't know any Hex-Editor under linux :mrgreen: 
But I'm fairly sure there are plenty out there. Try searching Synaptic with "hex"

DosBox can ran almost any kind of dos-executable. You're using a patch for the dos-version, frapos?
You could try VMware. It could be fast enough

---

### Post by keithjr on 2006-06-21
[QUOTE=HAARP]Oh well, I don't know any Hex-Editor under linux :mrgreen: 
But I'm fairly sure there are plenty out there. Try searching Synaptic with "hex"

DosBox can ran almost any kind of dos-executable. You're using a patch for the dos-version, frapos?
You could try VMware. It could be fast enough[/QUOTE]


VMware might be a decent idea.  I also have a packaged (still shrink-wrapped) version of DOS 7.0 I could dig up... I think that might be a better alternative than doxbox.  Dosbox doesn't do well with games that fringe on the late dos - early windows era.  On windows XP these can be run quite well with VDMSound.  If I were dual-booting at all I'd investigate it further, but my windows is gone and I was kinda hoping not to have to bring it back to life.

---

### Post by HAARP on 2006-07-06
I just discovered there's something else besides Dosbox: Dosemu. It doesn't emulate the CPU, and therefore is much, much faster.
I'm going to set it up and test it with MW2 tonight. Stay tuned :)

---

### Post by keithjr on 2006-07-06
[QUOTE=HAARP]I just discovered there's something else besides Dosbox: Dosemu. It doesn't emulate the CPU, and therefore is much, much faster.
I'm going to set it up and test it with MW2 tonight. Stay tuned :)[/QUOTE]


Whoa, this does sound promising... although it would spell doom for a lot of the older dos games that simply use the CPU clock to determine the game speed, it would be the breath of life that more recent games need!  Keep us posted, friend, and I'll also look into this later tonight as well.

---

### Post by HAARP on 2006-07-06
You could always try it the brute way: Load your computer with something demanding so it slows down :mrgreen:

The Dosemu from the Ubuntu repos seems to be broken..let's see if the debian ones work.

---

### Post by HAARP on 2006-07-06
Got it working. Speed is incredibly good, even with full details @ 1024x768

But I'm still having issues:
-Choppy sound in movies.
-No music
-Missile launchers tend to hit your own mech, especially when moving. I encountered this bug before, but it never was this bad.
-Mouse works in the menu, but not ingame.
-Crashes upon leaving a mission

GBL should work, too. I don't think Mercs will, since there are no cr*cks for it
I'm still working on it (Mech2), but I doubt it will ever reach a "playable" status.

---

### Post by keithjr on 2006-07-06
very interesting news.  I wager the missle problem is due to perhaps cpu overkill, or floating point rounding errors (no joke) miscalculating your mech's position...  *shrug*

 No music is simply due to a lack of CD (the music tracks were simple CD-Audio, you can always rip them if you have a copy)

the other problems are likely just inadequacies in dosemu.

---

### Post by HAARP on 2006-07-06
```
   You do not have the DOSEMU vga font installed and are running
   remote X. You need to install the vga font on your _local_ Xserver.
   Look at the readme for details. For now we start with an fixed font,
   which does not display all national characters correctly.
   ... be warned

ERROR: Unable to open console to evaluate the keyboard map.
Please specify your keyboard map explicitly via the $_layout option
full 0
ERROR: Fault handler re-entered! signal=11 _trapno=0xE
ERROR: cpu exception in dosemu code outside of DPMI client!
trapno: 0x0e  errorcode: 0x00000004  cr2: 0x0851100c
eip: 0x0809b261  esp: 0x0840d4b0  eflags: 0x00010212
cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
Page fault: read instruction to linear address: 0x0851100c
CPU was in user mode
Exception was caused by non-available page

```

I don't really care about the Fonts. They won't work, although i installed the package.
The fact the keyboard isn't working is bad tho. Since I'm using a crappy German layout, it's more of a try-and-error game to find out which key makes what special character. I don't know how to set it up properly. $_layout option? wtf?

Beginning with "full 0" is the actual error. It appears whenever I exit a mission, regardless of what the cause is (completed, died, aborted) and crashes the whole emulator. Huge bug, which renders the game unplayable.

The choppy sound could be related to which sound card I set before starting. Haven't tried it out since there are more important things to do
No music: Yea, of course that's the reason. Even if I had the CD inserted and Dosemu would recognize it, it wouldn't play because of the cr*ck

Those missile launchers are a major issue. I've blown myself up about 20 times now just because they explode immediately.

Did the mosue ever work ingame? I honestly can't remember :s But i think it did.


At this state, the game is unplayable. I doubt i will ever be, since I don't know any way to fix it

Dosbox actually does a better job at running this game.

---

### Post by jISh on 2006-07-10
Join my mission to get DOS running in VMWare. To hell with emulation, I've been trying to do the real thing..:P

---

