---
title: "Single player FPS games"
date: 2010-01-11
forum: Gaming &amp; Leisure
---

### Post by Bad Sector on 2010-01-11
I'm a huge fan of FPS games (and also a developer trying to make one... or 2-3...), of the single player kind. While i do occasionally play some multiplayer game, i'm 95% made of single player material :-).

I've used Linux since the late 90s and i had it as my main OS for years, until recently when i decided that i don't really like to reboot in order to play games and since all my devtools are cross platform, i might just stick with Windows. And besides, i'm one of those creepy people who actually like Vista.

However, honestly, what keeps me in Windows is the availability of single player FPS games. While Linux does have some good FPS games, most of them are multiplayer games. 

I would like to spend some more time in my Linux installation, but i also would like to play some games. So i decided to make this thread for listing the singleplayer FPS games people know about and have a Linux version (dedicated servers do not count, wine support also doesn't count).

So the games i know so far are:

[LIST]
[*]**Quake** and all the derived engines. My favourite is [DarkPlaces]("http://icculus.org/twilight/darkplaces/"), although it breaks some mods. For those mods i like [Fitzquake's SDL port]("http://www.kristianduske.com/fitzquake/").
[*]**[Cube and Cube 2/Sauerbraten]("http://cubeengine.com/")**. Personally i prefer Cube 1 to Cube 2 because it feels more action-y and the graphics are visually more consistent. Also the single plane action has a special feeling. Ok that might be my Doom addiction speaking. Which reminds me...
[*]**Doom**. Well, [prBoom]("http://prboom.sourceforge.net/") seems to be the good choice here. I also like [Chocolate Doom]("http://www.chocolate-doom.org/wiki/index.php/Chocolate_Doom"), which performs like vanilla doom down to supporting DHC scripts.
[*]**Unreal**. One of my favourite FPS games. It has been a while since i tried the [linux installer]("http://icculus.org/%7Eravage/unreal/unrealgold/") though.
[*]**Doom 3** seems to work, but its a bit glitchy for me.
[*]**Prey** supposedly also work, but i haven't tested it...
[*]**Marathon (via [A1]("http://source.bungie.org/"))**. For some reason i always fail to play past the first rooms of this game.
[*]**Duke Nukem 3D** supposedly runs under Linux port, but making [EDuke32]("http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux") to work is a pain. Too bad because the new "Polymer" renderer looks awesome.
[/LIST]
Reading the above list again... aren't there any indie or opensource or whatever else *single player* FPS games? Except for Cube/Cube2 and Doom3/Prey, its made up of ported classic (and old) DOS/Windows games. Do you know any? If so please list them :-).

Single player only though :-P.

---

### Post by Twitch6000 on 2010-01-11
Assault cube is another one.

---

### Post by munky99999 on 2010-01-11
I hear Duke Nukem Forever is going to be released on linux as an open source game. It's supposed to be released in 20

---

### Post by CharmyBee on 2010-01-11
> **Twitch6000 said:**
> Assault cube is another one.

Bot games of simulated multiplayer don't really count as single player.

---

### Post by william_nbg on 2010-01-11
Quake 2
Quake 4 both have Linux ports.

:popcorn:

---

### Post by ShadowTek on 2010-01-11
Doom 3 runs choppy by default, but setting the sound driver to OSS fixed it for me.

I couldn't get ALSA surround sounds to work though. That's the only real glitch I found.

---

### Post by TerminX on 2010-01-12
> **Bad Sector said:**
> 
**Duke Nukem 3D** supposedly runs under Linux port, but making [EDuke32]("http://wiki.eduke32.com/wiki/Building_EDuke32_on_Linux") to work is a pain. Too bad because the new "Polymer" renderer looks awesome.
How is it a pain?  [http://wiki.eduke32.com/wiki/APT_repository](http://wiki.eduke32.com/wiki/APT_repository)

---

### Post by Bad Sector on 2010-01-12
@Twitch6000:
Well, as CharmyBee said, i don't include multiplayer games which have bot-based singleplayer :-).

@william_nbg:
Ah yes, i forgot about Quake 2 and Quake 4 :-).

@ShadowTek:
Yeah with "glitch" i mean that it doesn't feel as smooth as the Windows version.

@TerminX:
I never noticed the APT repositories and when i searched for "EDuke32 Linux" at Google i only got the building page i link in my first post :-P. I'll check the packages when i'm at home :-).

Are those the only games? Anything from opensourceland?

---

### Post by Arrowsmith on 2010-01-12
> **munky99999 said:**
> I hear Duke Nukem Forever is going to be released on linux as an open source game. It's supposed to be released in 20
I like how you hedged your bet in this post, but honestly a DNF release within the next 90 years might be a tad optimistic.

---

### Post by SirBismuth on 2010-01-13
> **Arrowsmith said:**
> I like how you hedged your bet in this post, but honestly a DNF release within the next 90 years might be a tad optimistic.

Oh, I thought the "20" was some new number system like binary, where "10" does certainly not mean ***ten***.  So 20 would then mean something like 4 billion.  Although converting to hexadecimal makes it 3230 I see, so maybe it was in hex?.

B

---

### Post by Brebs on 2010-01-13
> **ShadowTek said:**
> Doom 3... I couldn't get ALSA surround sound to work.
See [the fix](http://forums.gentoo.org/viewtopic-p-4173170.html#4173170). ID messed up their ALSA code ](*,)

---

### Post by ShadowTek on 2010-01-14
> **Brebs said:**
> See [the fix]("http://forums.gentoo.org/viewtopic-p-4173170.html#4173170"). ID messed up their ALSA code ](*,)
lol  Your the same guy that told me to do that last time, but I had a lingering problem that went unsolved.
[http://ubuntuforums.org/showthread.php?t=1304228&page=2](http://ubuntuforums.org/showthread.php?t=1304228&page=2)

I'd still like to figure out what the deal is, as I described in that last post, if you have any idea what's causing it. :confused:

---

### Post by Brebs on 2010-03-01
> **ShadowTek said:**
> if you have any idea what's causing it. :confused:
Nope. Maybe the ALSA support for your particular soundcard model is incomplete, in which case you should go to the ALSA bugzilla, because I've never seen an ALSA dev on Linux distro forums.

---

### Post by ShadowTek on 2010-03-01
I'm using the onboard Realtek ALC888.
```
-desktop:~$ lspci | egrep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
```
/proc/asound/cards
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xea100000 irq 22
```I've never had an audio problem with this chipset before. I was under the impression that compatibility for these onboard chips was good, but a check of alsa's driver list doesn't even show the ICH10.
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

I have an old C-Media CMI8738 laying around, and it *is* on their driver list.
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media](http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media)

I guess I'll give that a try and see what happens.

---

### Post by ShadowTek on 2010-03-02
Well that was a big, fat waste of time. I'm seeing the *exact same* problem with the CMI8738. :evil:

If I map rear-left to rear-left and front-left, and rear-right to rear-right and front-right, everything works as expected, but trying to map each channel to its own proper speaker results in dysfunction of the rear channels.

Apparently, hardware compatibility isn't the problem.

---

