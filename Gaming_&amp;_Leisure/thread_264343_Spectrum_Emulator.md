---
title: "Spectrum Emulator"
date: 2006-09-24
forum: Gaming &amp; Leisure
---

### Post by Mark76 on 2006-09-24
I just installed Spectemu from the repository.

Typing spectemu into the terminal doesn't do anything.  Does anyone know the command to get it to work?

---

### Post by kabads on 2006-09-24
Do you have any files which represents games? If I remember correctly, you normally need to load a program into these emulators  for them to run. I'm not sure if you'll get the old spectrum prompt with basic built-in.

---

### Post by Mark76 on 2006-09-24
I was planning to download Tir-na-nog :)

---

### Post by rolando2424 on 2006-09-24
Try going to the console, enter the place where you have the roms and type "Spectemu rom_name"

That should do it...

---

### Post by Biggus on 2006-11-17
Dude, I think the command you are looking for is xspect.

I'm trying to 'load up' an ancient old game called 'Chaos', and I've used

> xspect -tzx Chaos.tzx

tzx is an option whereby you specify the type of tape image (or disk if you were posh enough to have a +3)

> xspect -help gives you more options.

:D

Oh, and incidentaly, don't use .tzx files, they take an eternity to load, I'm currently getting the bleeeee-sccrshhhhhhhhh bleeee-schreeeeeeeeeee thing happening for a good couple of minutes.

---

### Post by MikeSz on 2007-11-21
> **Biggus said:**
> Dude, I think the command you are looking for is xspect.

I'm trying to 'load up' an ancient old game called 'Chaos', and I've used



tzx is an option whereby you specify the type of tape image (or disk if you were posh enough to have a +3)

 gives you more options.

:D

Oh, and incidentaly, don't use .tzx files, they take an eternity to load, I'm currently getting the bleeeee-sccrshhhhhhhhh bleeee-schreeeeeeeeeee thing happening for a good couple of minutes.

that game has to be one of the best ever created - there are a number of re-makes out there and a few places where you can play the original online.  Check out:

[http://chaos.ffnet.org/](http://chaos.ffnet.org/)
or
[http://chaosgroove.wordpress.com/](http://chaosgroove.wordpress.com/) (a fairly faithfull but improved remake)

Hope that helps!!!

---

### Post by inversekinetix on 2007-11-21
Try running spectaculator in wine,  failing that just go to the world of spectrum website and play the games in their java emulator.

btw  I have about 50,000 speccy games,  its mind boggling how many they made

---

### Post by BigSilly on 2007-11-22
There's a shortcut in Spectemu to load games quickly. No game has to take an age to load. Type in xspect to bring up the emulator, then when the window appears with the Sinclair start screen, you can press ctrl and h for the instructions you can use. It's actually a very easy emu to use, even though it has no GUI. 

I'll pop back later when I've got the time to help you use it if I can. I've got to take the kiddie to school at the mo! But Spectemu is actually pretty good imho, and I've played more than a few games on it.

---

### Post by inversekinetix on 2007-11-22
Im from sheffield originally, did ya used to swap games on c90s?

---

### Post by BigSilly on 2007-11-22
> **inversekinetix said:**
> Im from sheffield originally, did ya used to swap games on c90s?

Hiya. Cool! What's it like living in Japan? A world away from scruffy old Sheffield I bet, you lucky thing!

I was lucky enough to be born right into the Spectrum glory days, so of course I swapped those old C90's. :D  I still had a few up until recently, and then I gave the whole thing away to a charity. It was a Spectrum Plus anyway, and wasn't my original rubber keyed one that had long since broken and been thrown away. :(  Ah well, luckily I have this excellent emu for Linux!

For the chap that was struggling to use it, [this might come in useful.]("http://www.inf.bme.hu/~mszeredi/spectemu/README") Download your zipped up games, and extract them somewhere. You'll notice that the folders you extract contain little files with .tgz, .z80, .sna extensions and a couple more. These are what you need and Spectemu can deal with all of them. 

Open a terminal and type xspect, then space, then drop in the .sna or whatever into the terminal. This'll put the full path to the game into the terminal. Press enter, and you'll go straight to the game if it's a snapshot. If it's a .tap tape file or similar, you'll get the Sinclair start screen. Press J for LOAD, and then ALT and 2 twice. This'll give you the classic Speccy LOAD "". Press enter. The Spectrum screen goes grey. Then press CTRL and O (the letter not the number) to 'play the tape' and the game will load up "old school" (ie. will take ages!). You can speed up things by pressing CTRL and Y. 

This should sort you out I reckon. It's a bit tricky for beginners, and had me stumped for a while so I hope this helps. :)

---

### Post by spec-chum on 2007-11-22
spectemu is quite a nice 48K Speccy emulator.  It doesn't emulate the 128K machines though.  I use Fuse (the Free Unix Spectrum Emulator)
which emulates just about everything, including a black and white TV
(yes, really).

This is the main Fuse site where you can download the source code:
**[http://fuse-emulator.sourceforge.net/](http://fuse-emulator.sourceforge.net/)**

I installed the Debian binaries available at
[B]
[http://www.youmustbejoking.demon.co.uk/progs.etch.html](http://www.youmustbejoking.demon.co.uk/progs.etch.html)[/B]

though rather than compiling from source.  Works fine here on Gutsy.

Here it is running one of the best Spectrum games ever. :)

---

### Post by spec-chum on 2007-11-22
Oh, talking of Head Over Heels (which is what the screenshot is of) you may want to download Retrospec's remake of the game for your nice snazzy Linux box.  Check that out here:
[http://retrospec.sgn.net/game-overview.php?link=hoh](http://retrospec.sgn.net/game-overview.php?link=hoh)

Here's a screenshot of that in action.

---

### Post by spec-chum on 2007-11-22
Ah. :)  If I add the -bgr option to my Head Over Heels launcher in the menu I get the correct colours.  That'll teach me to read the docs. :lolflag:

---

### Post by BigSilly on 2007-11-22
Hehe! Cheers for that spec-chum, I'll definitely be giving those a shot. 

Head Over Heels is a classic. One of my favourite Speccy titles is Underwurlde from Ultimate. It always surprises me when I talk to old Spectrum fans who have never even heard of it. It's a classic dammit!

EDIT: Just installed your updated Head Over Heels. How cool is that? Fantastic. Cheers for the nod on that one. ;)

---

### Post by spec-chum on 2007-11-24
I never could get on with Underwurlde.  I always ended up bouncing uncontrollably around the place.  I did complete Sabre Wulf and Knight Lore though.

---

### Post by BigSilly on 2007-11-24
It definitely required a delicate hand. I've always enjoyed platform games more than any other genre though. It's the one style of game I generally have no problems with, though I have to admit I never completed Underwurlde. I got very close though...

BTW, I installed that Fuse you mentioned. I got the xfuse-sdl packages. How do I get it to go full screen? When I open it, it comes up in a tiny window. I really like the look of it, so if you have any handy hints about using it, they'd be much appreciated.

Many thanks. :)

---

### Post by spec-chum on 2007-11-24
> **BigSilly said:**
> 
BTW, I installed that Fuse you mentioned. I got the xfuse-sdl packages. How do I get it to go full screen? When I open it, it comes up in a tiny window. I really like the look of it, so if you have any handy hints about using it, they'd be much appreciated.

Many thanks. :)

I've installed the xfuse-gtk package rather than the sdl as it's a nicer interface.  With that you can't go full screen, but you can expand the window to three times normal size which is plenty big enough.

---

### Post by BigSilly on 2007-11-24
Oh right. Can I not make this screen bigger on the sdl version then? Should I just install the gtk version?

---

### Post by spec-chum on 2007-11-24
You can call the SDL version with
```
xfuse-sdl --full-screen
```
to get it to go full screen (as I've just found).  Seems to not play nice with avant window navigator when coming out of it though so I'm gonna stick to the GTK version.

---

### Post by BigSilly on 2007-11-24
The sdl version crashed my computer earlier, so I thought I'd install the gtk version and give it a bash. However, I'm getting this error when I try to launch it with xfuse-gtk in the terminal -

```
xfuse-gtk: error: Unknown display size/image size 0/1
```

What does that mean?

---

### Post by spec-chum on 2007-11-25
> **BigSilly said:**
> The sdl version crashed my computer earlier, so I thought I'd install the gtk version and give it a bash. However, I'm getting this error when I try to launch it with xfuse-gtk in the terminal -

```
xfuse-gtk: error: Unknown display size/image size 0/1
```

What does that mean?

It's not worked. :)

I'm guessing you probably need to install GTK+ first.  I think I did.  Unfortunately that does require compiling from source as far as I know.  You can find it here:
[http://www.gtk.org/](http://www.gtk.org/)

---

### Post by BigSilly on 2007-11-25
> **spec-chum said:**
> It's not worked. :)

I'm guessing you probably need to install GTK+ first.  I think I did.  Unfortunately that does require compiling from source as far as I know.  You can find it here:
[http://www.gtk.org/](http://www.gtk.org/)

Guess I'll be sticking with me Spectemu then! Cheers for your replies.

---

### Post by BigSilly on 2008-02-03
Bumping this thread back up in the hope someone can help. I've downloaded FUSE from GetDeb today, and so far it seems to be working excellently. I've read somewhere that you can use your PC gamepad as a joystick device in order to play your games on it, but I can't figure out how to configure it. I've searched the internet, but nothing I find can help. I'm just not sure which boxes I should be ticking, and how to set up the pad. My pad works excellently on Ubuntu, and is great with SDLMame, ZSNES, Mupen64, FakeNES and loads more. It's a PS2 style dualshock-alike, [this one in fact.]("http://www.play.com/PC/PCs/-/673/880/-/3274924/Speed-Link-Strike2-Gamepad-With-Force-Vibration-In-Transparent-Blue/Product.html?searchtype=genre")

If there's a way to set it up I'd appreciate your help. Thanks in advance.

---

### Post by mooncats on 2008-05-04
Sorry for bumping a quite outdated topic, but it's the only spot google leads to, so i thought it might be useful for people who run into same trouble:

```
xfuse-gtk: error: Unknown display size/image size 0/1
```

This can be fixed by using a commandline parameter:

```
xfuse-gtk --no-aspect-hint
```

Hope it helps anyone.

---

