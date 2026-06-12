---
title: "Wine and video games"
date: 2006-09-04
forum: Desktop Environments
---

### Post by Rippy on 2006-09-04
Basically, the only thing I still use Windoze for is for games, the only thing linux lacks (other than quicktime >_>). And so, I have a couple Wine-related questions to ask:

1. Does Wine decrease performance in games? I'm running games like CS:S on my 20ghz CPU and Radeon 9250, I don't exactly have the FPS to spare.
2. What games will work on Wine? I have a bunch of Steam games, Call of Duty 2, Starcraft, Age of Mythology, and a bunch others, but it's the Steam game I'm worried about.

Sorry, I'm no expert on Wine, or emulation in general, so sorry if I'm missing something obvious :P Any help appreciated,

-Rippy

---

### Post by iONiK on 2006-09-04
> **Rippy said:**
> Basically, the only thing I still use Windoze for is for games, the only thing linux lacks (other than quicktime >_>). And so, I have a couple Wine-related questions to ask:

1. Does Wine decrease performance in games? I'm running games like CS:S on my 20ghz CPU and Radeon 9250, I don't exactly have the FPS to spare.
2. What games will work on Wine? I have a bunch of Steam games, Call of Duty 2, Starcraft, Age of Mythology, and a bunch others, but it's the Steam game I'm worried about.

Sorry, I'm no expert on Wine, or emulation in general, so sorry if I'm missing something obvious :P Any help appreciated,

-Rippy


Well, Wine has been recently configured to run full 3D games, so it should work for you.

And about what games would work in Wine, I don't know about that.
If you are running them full off a CD then all of them should as lond as you configure the CD right (you need some files on your computer), but all of them SHOULD work unless you can't get the files on your computer. (This option is bad unless you are a config freak.)

---

### Post by Rippy on 2006-09-04
Alright, and does performance drop much? Or is it comparable to running the game in Windows?

Edit: nevermind, that time I was able to find my answer in a search >_>

---

### Post by Aualin on 2006-09-04
and, do you really mean 20 ghz?!!
or do you mean 2,0 :p

---

### Post by JNowka on 2006-09-04
Wine works great with OpenGL games.  It still has something to be desired for DirectX.  Not all OpenGL games will work, and usually takes a little bit of configuring to get things to work.  As for DirectX games, most will not work.  As for the comparibility, depends on the game.  Some games work better other the same, and still others worse.

---

### Post by divgradcurl on 2006-09-04
Some useful sites...

[http://appdb.winehq.org/](http://appdb.winehq.org/)
[http://frankscorner.org/index.php](http://frankscorner.org/index.php)

---

### Post by SishGupta on 2006-09-04
1. You may or may not experience an FPS drop using wine on linux. It depends on the game and your gfx card. Some opengl games dont work 100% in wine and you will get a performance drop from that. Some GFX cards dont work that well in linux either, resulting in a performance drop. I hear that ati cards dont have the same fps in linux as they do in windows because of how ati does drivers. And i hear that nvidia cards will be the same performance-wise as in windows.

For opengl games like ones based on the HL engine and the source engine, wine should work fine. Use the appdb from the post below for tweaks, tips, and bugs.

For directx games the only option is cedega, which by law requires you to pay for it as there is proprietary code in it. I am not telling you to break the law, but i will say that with cedega, it is possible to break the law. There is also a CVS version of cedega, but then you lose a lot of the finer points of cedega, as in some stuff that will make games that do not work..work. When you pay for cedega you also get support. CVS/Lawbreakers...not so much.

I hope this info helps.

---

### Post by Rippy on 2006-09-04
W00t! I figured out how to work wine!
W00t! I installed Starcraft!
Crap! It lags terribly!

Dang. I'll have to try some other games and see how they fare >_> Also, how do you figure out if a game uses OpenGL or DirectX?

Ah nevermind, I figured it'd be in the system requirements and I was right :P Starcraft requires DirectX 5.0 (gasp), which would explain the horrible lag.

But anyway, thanks for the help so far.

Edit: Crap, all my games are DirectX >_> Only ones going for me are the Steam games, but I'm gonna make up my machine before I tackle them because it could be a messy uninstall if it fails.

Oh and yes, I did mean 2.0ghz. 20ghz, hahah I wish.

---

### Post by skymt on 2006-09-04
I'm pretty sure Wine includes some DirectX support. Recent news postings on the [website](http://winehq.com/) mention things like "Still more work on Direct3D" and "More work on Direct3D shaders."

---

### Post by zaipai on 2006-09-04
I would recemend  Cedega ([http://www.transgaming.com](http://www.transgaming.com)) you can just select the lowest cost option download it burn it to CD and you are set. After subscription runs out there will be no updates but then the games you sited don't need any further support. You pay for Cedega (I use it for Everquest and its great) not because the code is owned by another company as much as you are paying for support and further programing. There is a license fee but the company could charge each user a one time fee of $5 and cover that.
The other option if you can not do Cedega is VMPlayer you can install Windows in there, goto [http://www.easyvmx.com](http://www.easyvmx.com) to get the files to work with the free VMWare player. Then look at the forums for info on how to get directx to work with it. I did it and it works great (some times laggy but not too bad).
There is also other PC Virtual Machines that you can use that are free and don't require breaking the EULA to use for gaming. You can also just Dual Boot Windows / Linux and the last thing, install Windows and use DSL (Damn Small Linux) and run it from the NTFS/FAT partition.

---

### Post by CatKiller on 2006-09-05
> **Rippy said:**
> W00t! I figured out how to work wine!
W00t! I installed Starcraft!
Crap! It lags terribly!

Do you actually mean lag? I've been playing Starcraft through Wine with few problems on a much less powerful computer than yours. The only time I've had problems with lag is when playing online against people behind poorly-configured routers - and they were using Windows :rolleyes:

But I did have some problems with the sound that were fixed by running the game with ```
nice -n 20 wine starcraft.exe
``` which I believe makes the game run at a lower priority than the sound. So the game *does* slow down to stay in synch with the sound. At least I think that's what's happening, anyway ;)

---

### Post by Rippy on 2006-09-06
Yes, it was near-unplayable lag, I'm estimating around 15 fps. Right from the menu.

Now, I noticed later that I didn't have the "give support for pixel shaders (if available) option in the Graphics section of winecfg. But surely Starcraft doesn't use pixel shading. Other than that, I have no idea why it would run so slowly. Are you running wine as a virtual desktop maybe? I wouldn't think that would affect anything, but you never know.

---

### Post by La_Frenezo on 2006-09-06
> **CatKiller said:**
> Do you actually mean lag? I've been playing Starcraft through Wine with few problems on a much less powerful computer than yours. The only time I've had problems with lag is when playing online against people behind poorly-configured routers - and they were using Windows :rolleyes:

But I did have some problems with the sound that were fixed by running the game with ```
nice -n 20 wine starcraft.exe
``` which I believe makes the game run at a lower priority than the sound. So the game *does* slow down to stay in synch with the sound. At least I think that's what's happening, anyway ;)


I had a lot of b.net-issues and mouselag with Wine and Starcraft. So I bought Cedega ONLY cause of Starcraft. It's an officially SUPPORTED GAME. But in fact it is NOT playable smoothly. I am really upset cause of that. Cedega might work well with other Dirext-X games, but Starcraft is definately not one of them.

---

### Post by GTX on 2006-09-06
Cedega ([http://www.transgaming.com](http://www.transgaming.com)) - They have decent support for games etc

---

### Post by CatKiller on 2006-09-07
> **Rippy said:**
> Yes, it was near-unplayable lag, I'm estimating around 15 fps. Right from the menu.

Now, I noticed later that I didn't have the "give support for pixel shaders (if available) option in the Graphics section of winecfg. But surely Starcraft doesn't use pixel shading. Other than that, I have no idea why it would run so slowly. Are you running wine as a virtual desktop maybe? I wouldn't think that would affect anything, but you never know.
Sometimes I run it as a virtual desktop - if I'm going to be using battle.net, for example.

FWIW, I'm using Windows 2000 as the Windows Version, I've enabled desktop double-buffering and I'm letting the window manager manage windows. I've gone for hardware on the Vertex Shader Support, and I've allowed Pixel Shader. I don't think Starcraft uses either of those, tbh. I'm using ALSA for sound. I've got hardware acceleration set to standard, driver emulation on, and quality at 22050/8, but I think that all of these were when I was playing with Settlers 4.

In terms of the game, I've turned off the portrait animations. And I run it reniced, as I mentioned before.
> **La_Frenezo said:**
> I had a lot of b.net-issues and mouselag with Wine and Starcraft. So I bought Cedega ONLY cause of Starcraft. It's an officially SUPPORTED GAME. But in fact it is NOT playable smoothly. I am really upset cause of that. Cedega might work well with other Dirext-X games, but Starcraft is definately not one of them.
The battle.net issue is widely-reported. And Blizzard shut down the only alternative. I believe, based on not much, that the battle.net client uses some kind of pikey undocumented routine to write to the graphics card. Anyway, you can get round the legibility issues by pressing the Show Desktop button - when you go back to the application, the bits of the window that were obscured by layered text are replaced by a chunk of your desktop background (this is why I run it in a window if I'm doing battle.net) and if your background is dark, as mine is, you can read the next layer of text quite happily. Oh, and at some points you need to force a redraw of areas - buttons in the menus, and so on - by waving your mouse pointer over them. It's a bit of a pain, but it's hardly arduous. The actual network play is fine once you've got past all the battle.net nonsense.

The only issues I have running the game on the Wine that's packaged at the budgetdedicated repository are the battle.net problems above, which are hardly show-stoppers, and a slight delay when one of the buildings acknowledges. Perhaps you could get round this by turning them off. Haven't played for a little while, so I can't remember exactly which options are in there. The sound engine in Starcraft is hardly robust though - a scratch on the cd causing corruption of one of the .wav files will cause the game to crash hard rather than just skipping the audio.

This is running the game on a 1.2 GHz Athlon with a 32MB GeForce 2 GTS using onboard sound, btw. Running Wine 0.9.20.

---

### Post by andb on 2006-09-08
About starcraft being jerky, I had problems for ages in wine. Tried everything. In the end it turned out to be the graphics card. I had an integrated Intel graphics controller. Worked fine in Win. Put in an old ATI 9250 and now it is just as playable as windows. Im really demanding, sometimes play over 20 hours a week online with freinds. Now with wine as is, p4 2.8 512mb and the ATI 9250, all is well in the world of starcraft.

---

### Post by puppy on 2006-09-08
I have World of Warcraft working perfectly under Wine (it uses a slightly hacked version of the Wine package - have a search around on the forums, there's a good HOW-TO) and the Steam suite of games work well also - perhaps there's a slight hit to performance etc but it's nothing more than 2 or 3 fps. I'm using 32bit dapper and I have an Athlon64 running at about 2.5Ghz, 2GB memory and a Geforce 6800GT. 

I do have Cedega but to be honest it seems to be more trouble than it's worth - WoW installation using Wine was painless while I've never actually managed to get it to install under Cedega ](*,)  The support in their forums is also poorer than what you can get by googling I find... and you don't need it for either of the above games. In its defense it is very cheap though and although I have them, I haven't tried installing Battlefield or Call of Duty using it yet - I may have more success...

I think with Wine & Cedega, once you've worked out the bugs (which usually involves changing little bits in scripts you find on the web) it'll be your hardware that will dictate performance (as with Windoze). 

Big caveat though - don't expect games that have just been released to work on linux - Prey and F.E.A.R cannot be run, even by Cedega, at the moment I understand, and it takes time for all the bugs to be worked out on slightly less recent releases... but if you don't mind playing games that have been out for a while (and thus are much cheaper ;) ) then gaming on linux is definitely worth considering :mrgreen:

---

### Post by tombean on 2006-09-27
> **puppy said:**
> (it uses a slightly hacked version of the Wine package - have a search around on the forums, there's a good HOW-TO)

Hey puppy can you link the hacked wine package and the HOW-TO?

Thanks a lot.

-tom

---

