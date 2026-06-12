---
title: "The Witcher 2: Assassins Of Kings Enhanced Edition Released For SteamOS Linux"
date: 2014-05-22
forum: Gaming &amp; Leisure
---

### Post by ELD on 2014-05-22
That's not an error, The Witcher 2: Assassins of Kings Enhanced Edition is now out for SteamOS/Linux and I am downloading it as I type this.
What a year!

Link: [http://www.gamingonlinux.com/articles/the-witcher-2-assassins-of-kings-enhanced-edition-released-for-steamos-linux.3746](http://www.gamingonlinux.com/articles/the-witcher-2-assassins-of-kings-enhanced-edition-released-for-steamos-linux.3746)

---

### Post by Zeven on 2014-05-22
[Source.]("www.gamingonlinux.com/articles/the-witcher-2-assassins-of-kings-enhanced-edition-released-for-steamos-linux.3746") I do hope The Witcher gets released too in the near future.

---

### Post by bapoumba on 2014-05-22
Threads merged.

---

### Post by Zeven on 2014-05-22
[Just for those who haven't done it yet.]("http://www.gog.com/witcher/backup") Makes sense to do it since [GOG is introducing Linux support later this year.]("http://www.gamingonlinux.com/articles/gogcom-are-going-to-support-linux-confirmed.3288")

---

### Post by oldrocker99 on 2014-05-22
And, in fact, GOG is owned and run by CDProjekt Red, programmers of the Witcher.

---

### Post by CharlesA on 2014-05-23
> **oldrocker99 said:**
> And, in fact, GOG is owned and run by CDProjekt Red, programmers of the Witcher.

Pretty awesome isn't it?

That's frigging sweet that they got it ported to *nix. Wonder how the performance is.

---

### Post by LostInBKK on 2014-05-23
Using play on Linux you can play that game now.

---

### Post by CharlesA on 2014-05-23
> **LostInBKK said:**
> Using play on Linux you can play that game now.

Yeah, but that's not exactly playing it natively. ;)

---

### Post by oldrocker99 on 2014-05-23
I eagerly tried to run the game last night, having downloaded what I thought was the complete game 3/20. I ended up deleting the cache and downloading again :-(, but The. Game. RUNS! Now, if Skyrim and Oblivion can get ported, and maybe Bioshock Infinite, I'll deepsix Windows forever!

It is somewhat obvious that this is as major a release as we've yet seen for our platform. What a year, indeed!

---

### Post by oldrocker99 on 2014-05-23
Ahem. This is **not** a native port, after all. The Linux port uses a VP eON wrapper, somewhat similar in concept to Wine, but supposedly tuned for each program it is built for.

The Steam and Gaming on Linux forums have been in high dudgeon mode about this. It also appears that installing the game using PlayOnLinux has better framerates. I don't personally care; I'd rather have an iffy port than no game. Nonetheless, it does play fine for me on my <$1000 box.

---

### Post by LostInBKK on 2014-05-26
Till the Steam Boxes come out we are going to have to accept that ports will be for most games.

I just hope that something big that Half Life 3 or Left 4 Dead 3 is given 3 or 6 months exclusive on the Steam Box

---

### Post by oldrocker99 on 2014-05-26
> **LostInBKK said:**
> Till the Steam Boxes come out we are going to have to accept that ports will be for most games.

I just hope that something big that Half Life 3 or Left 4 Dead 3 is given 3 or 6 months exclusive on the Steam Box

The best I'm hoping for is that Linux/SteamOS versions come out at the same time as the Windows versions. Yeah, it'd be great to see exclusive releases for Linux/SteamOS, but I'll just be satisfied to see simultaneous releases.

---

### Post by LostInBKK on 2014-05-26
If there is not exclusive software I can't see anyone buying one.

Software releasing at the same time is great for us Linux users :D

---

### Post by DanglingPointer on 2014-09-29
I downloaded it from Steam on the weekend for $20!  And it is awesome!  Runs smoothly!
I'm running on High settings with Anti-Aliasing turned off, Large Textures on, and no depth of field (I like being able to see clearly everything on the scene and not be focused on just some part!).

Running 1080p on
Ubuntu 12.04 
Catalyst 14.6
R9-290X
i7-2600
16GB RAM
RAID5 game library

---

### Post by oldrocker99 on 2014-09-30
The much-derided eON wrapper has been diligently worked on by Virtual Products, and what was crashing and running poorly is now running beautifully and crash-free (for myself at least). 

It's really nice to see someone responsible for a game running on Linux to fix what wasn't working, in order to make customers happy. Painkiller:Hell and Damnation, a native port which worked fine on nVidia and wouldn't run at all on ATI was worked on by the developer, even contacting ATI on their fglrx driver until ATI owners could run the game.

There have been a lot of native ports which run flawlessly, and Linux gaming is progressing by leaps and bounds.

---

### Post by DanglingPointer on 2014-10-01
I just tried out a new tweak to decrease stuttering on high settings...
If you have a card with greater than a GB of VRAM, you can tweak the texture size buffer to load more textures into the card instead of streaming them in game.  The game was developed at a time when a GB was the norm for high end cards.
Go to ~/.local/share/cdprojektred/witcher2/GameDocuments/Witcher 2/config and open the user.ini after you have selected "high" settings from the graphics options.  This will have the user.ini primed with the high configuration.
Change TextureMemoryBudget to a larger value.  I have mine at 2048 MB.

For more details read here from post 5 down... [http://forums.steampowered.com/forums/showthread.php?t=1918044](http://forums.steampowered.com/forums/showthread.php?t=1918044)

With my config I disabled V-sync and increased LOD distance to FAR using the Options GUI.  Then I exited the game, opened the user.ini file then set the TextureMemoryBudget to 2048; saved then made the file read-only.
It really works with my R9-290X.

Enjoy!

---

