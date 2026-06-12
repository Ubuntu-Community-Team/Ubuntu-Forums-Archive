---
title: "All 3D games crash with purple stripes"
date: 2009-01-26
forum: General Help
---

### Post by Flying Mandarine on 2009-01-26
Hi everyone!

Each time I start a 3D game on Ubuntu 8.10, whether full screen or in windowed mode, whether native or on WINE, the game crashes after some time. I can still hear the music, but the screen is all pink/purple and I cannot do anything but hard reboot the computer. Also, after something like a minute, the screen just shuts down and I have to reboot the computer.

The strange thing is that it does not happen with Flash games or 2D games (as far as I'm aware), although I haven't tested a lot of 2D games. It seems to crash faster with some games than with others, but it's still rather random: with a game such as Gravity Bone (free indie game), the game can crash after 1 or 5 minutes whereas with Smokin' Guns (another free indie game), I can sometimes play for up to 10 or 15 minutes.

Maybe it's because Smokin' Guns is less CPU-intensive than Gravity Bone? I remember trying Assassin's Creed on WINE and it always crashed after one or two minutes.

[Here]("http://img102.imageshack.us/my.php?image=imgp2286ti9.jpg")'s a link to a picture I took of my screen when it crashed. Does that kind of display/computer crash ring a bell to anyone?

And here's my configuration:

GeForce 9600 GT 512 mb (Twintech)
Power supply Novasia Axxyon 930 W
Dual Channel DDR2, XMS2, 2 x 1 Go, PC2-6400, Corsair
Hard drive DiamondMax 22, 500 Go, 7200 tpm, buffer 32 Mo, SATA II, Maxtor
Main board GA-P35C-DS3R ver. 2.1, socket 775, Gigabyte
Core 2 Quad Q9300 (2.50 GHz)
Screen Proview Electronics CA-772

The screen is quite old but I never had any problems with it. I tried reverting to the NVIDIA drivers 173 (right now I'm on 177) but I had problems with configuring my screen so I dropped the idea.

I had some problems with that computer before but with the guarantee I was able to get a new graphics card, a new Core 2 Quad and a new power supply, so they're just a few months old.

Also, I'll try to install Windows XP on another hard drive, just to see if it has to do with my hardware or with Ubuntu.


Thanks in advance!

Flying Mandarine

---

### Post by GWBouge on 2009-06-18
have any luck with this?

mine started doing this last night, and it's actually quite scary ... on a reboot, the loading screen (before and during grub) has green or red stripes going across it, and, like you said, the screens will shut off and it will require another reboot.  once I had to reboot it a few times, tried my Win partition (still with the green stripes) and it would load into safe mode, but not a normal boot.  I had to shut it off and let it sit for a while before it would act normally.  This doesn't occur only during games for me, though

is this possibly a video card issue?

Dell XPS420 Series
Intel Core2 Duo 3.0GHz(E6850)
4x1GB DDR2 800MHz
nVidia 8600GTS 256MB
Sound Blaster X-Fi Fat1l1ty
Hauppauge WinTV-HVR-1600

---

### Post by GWBouge on 2009-06-18
*UPDATE*

shortly after I posted that last reply, it happened again.  several reboots later it started to act right, so I ran nTune on my Vista partition, and the same thing happened after a minute or so of stability testing.  I borrowed an 8800GT from a friend, and that one worked ok (once I finally got it set right in the PCIe2 slot ... something seems quirky there).  I'm using my video card again at the moment, and it seems to be fine for now (after it cooled off for an hour or so).  guess I need to refrain from gaming for a little while   =o(

time for an upgrade!

---

### Post by nandemonai on 2009-06-18
Sounds like it's overheating to me.

---

### Post by t4thfavor on 2009-06-18
My old cards do that when the fan is dirty, or about t go. It really looks like overheating to me as well.  I would clean it, and make sure the fan is working.

---

### Post by GWBouge on 2009-06-20
in my case it was actually pretty clean.  I think my main problem was my power supply.  Dell shipped w/375 watt, and the sound card and TV tuner were added by me (I already had them when I ordered the computer).  so, I'm guessing I was pretty borderline on the psu, and in times of heavy load the video was starving a little and overheating.  I had that concern at first, but everything worked fine for a year and a half, but I guess the video card finally had enough.  it died completely on me thursday night ... let it sit until after work friday, still no luck.

but that's ok, I was just forced to hurry up and get a PCI card while I'm waiting for another PCIe to come in (been wanting to try multiple workstations  =oD ).

as for the OP ... maybe he got sent a bunk card?

---

### Post by Flying Mandarine on 2009-07-11
GWBouge: I'm sorry, but what's a bunk card?


I am surprised somebody answered after all this time!

Unfortunately, I still haven't solved my problem. I tried a different screen but the problem still came, so I thought let's try another OS. I installed Windows on a new hard drive, but the problem is still here.

However, the really strange thing is, I played Assassin's Creed for three or four days, at about seven or eight hours a day. The game never crashed. All the other games I've tried (all free games: Trackmania Nations Forever, Sauerbraten, Gravity Bone, Smokin' Guns, Audition Online, and Quake Live) crash (same purple screen, there is a link to a picture I took in my first post). However, some games seem to crash faster than others, and as a whole, they take more time to crash than on Ubuntu (I think it might be because I'm using BOINC at the same time on Ubuntu but not on Windows).

Why would one game (Assassin's Creed) work without problems but all the others not?

I'm going to try some more games to see if they crash, so if you'd like me to test a specific game (a free game I can download somewhere), just tell me.

Does anyone have any idea?

---

### Post by ibuclaw on 2009-07-11
You could try upgrading to the latest NViDIA Driver.

Failing that, it may be a over-heating issue as stated above.

Regards
Iain

---

### Post by Flying Mandarine on 2009-07-11
Hey Iain, thanks for the quick answer!

I installed the latest drivers for the nVidia GeForce 9600 (186.18, I'm under Windows at the moment), and... still crashing.

The strange thing is, the crashing time varies from game to game it seems... I can play Quake Live for maybe 30 minutes, but a game such as Audition Online crashes after less than 5 minutes, although I'm only in the menus (which are in 3D), not actually playing the game.

I checked several times the temperature of the motherboard and of the graphics card (in the bios and with the nVidia software), and there doesn't seem to be an overheating issue... I don't get it.

And if it was an overheating issue (or any other issue for that matter), why would only one game (Assassin's Creed) out of ten work?

---

### Post by ibuclaw on 2009-07-11
> **Flying Mandarine said:**
> Hey Iain, thanks for the quick answer!

I installed the latest drivers for the nVidia GeForce 9600 (186.18, I'm under Windows at the moment), and... still crashing.

The strange thing is, the crashing time varies from game to game it seems... I can play Quake Live for maybe 30 minutes, but a game such as Audition Online crashes after less than 5 minutes, although I'm only in the menus (which are in 3D), not actually playing the game.

I checked several times the temperature of the motherboard and of the graphics card (in the bios and with the nVidia software), and there doesn't seem to be an overheating issue... I don't get it.

And if it was an overheating issue (or any other issue for that matter), why would only one game (Assassin's Creed) out of ten work?

Check what Graphics settings you have set in Assasins Creed compared to other games, if possible.

It could be anything small that may be crashing the card.

ie: type of Buffer, Anti-aliasing, Anisotropic Filtering enabled, Sync to VBlank enabled, etc,etc.

Regards
Iain

---

### Post by Flying Mandarine on 2009-07-11
I'm not sure how to know what I've tried or not tried, but what I do know is that I tested most games with the maximum details (anti-aliasing and anisotropic filtering for instance).

How could I compare those graphics settings with other games? Do you have any game in mind you can advise me and which would be highly customizable in its graphics?

I made a search once again and I'm surprised that I cannot find anybody having the same problem as I do, especially since it happens with a clean install (of whatever OS) and with more or less all games.

I'm going to try a few more games just to see if I can find another one that doesn't crash.

---

### Post by Flying Mandarine on 2009-07-13
Alright, so I went into the BIOS of my motherboard (Gigabyte P35C-DS3R) and I remembered I messed around with the "MIB Intelligent Tweaker" options when I had another (power supply-related, changed my power supply since then) problem. I didn't overclock much, but still, just to try, I put everything down to the lowest (or so I think... there is stuff I'd rather not mess about since I have no idea what they're supposed to do).

I thought my problem was solved because I could play Audition Online (which normally crashes after less than 5 minutes), Quake Live and Trackmania Nations Forever for 45 minutes each without it crashing... The day after, I tried to play Trackmania Nations Forever but after about an hour of play (in windowed mode), the game crashed the same way as before (see first post for a picture), except the music/sounds didn't seem to repeat every one or two seconds; it seemed to slow down.

I'm at a loss here, I was really thinking the tweaking I did earlier was the problem here... Maybe it has to do with overheating as some other people said, since the less busy my computer is (and the less overclocked), the longer I can play before it crashes... But when I check the temperature in the BIOS or with the nVidia panel, both temperatures are completely OK.

Does anybody have any idea?

Thanks!

---

