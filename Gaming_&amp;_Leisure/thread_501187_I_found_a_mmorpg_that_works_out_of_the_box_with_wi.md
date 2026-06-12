---
title: "I found a mmorpg that works out of the box with wine!!"
date: 2007-07-14
forum: Gaming &amp; Leisure
---

### Post by Ripfox on 2007-07-14
[http://www.prairiegames.com/](http://www.prairiegames.com/)

It's called Minions Of Mirth, and all I had to do was lower some settings in game!

And it's free. This is what I was looking for...

EDIT:

I have been testing some others and found some that work good!

[http://ubuntuforums.org/showthread.php?t=506565](http://ubuntuforums.org/showthread.php?t=506565)

---

### Post by Toxicity999 on 2007-07-15
Could you write up a personal run through or review or something? You never get the whole truth from a games site. Is it good/bad, etc.

---

### Post by Ripfox on 2007-07-15
Well, just the fact rhat it runs perfectly under Wine makes it worth a try for me...don't have too much time invested so far, but seems like a standard mmorpg to me. Are they really all that different? :o

---

### Post by Swarms on 2007-07-15
I am downloading it right now, look promising.

---

### Post by Wiebelhaus on 2007-07-15
GFX are gayer than a beer salted man tit tho'.


I'm just fooling , looks cool.

---

### Post by cogadh on 2007-07-15
The graphics do look a little dated, but hey, how often do you find an MMORPG that actually works in Wine? Nice catch ripfox! :)

EDIT - Hmmm, I can't run it, I keep getting an "ntlm_auth" error. I'm going to try creating a new Wine config to see if it corrects the issue.
EDIT2 - Looks like the ntlm_auth error was just a red herring, it was a different Direct3D error that caused the problem. I got rid of my custom Direct3D config and it launched fine. Now the OpenAL sound system doesn't launch, so the game works great with no sound.

---

### Post by dorath on 2007-07-15
Downloaded and installed it last night.  The install was a breeze, and aside from the sound issues already mentioned it rus great.

First order of business was running up to the top of that tower you start next to and jumping off.  Falling damage: check!

There were quite a few people in the starter area.   Well, for 1:30am Pacific anyway.  Always a good sign. :)

---

### Post by hikaricore on 2007-07-15
Looks like it's almost on par with Rugnum as far as graphic go (based on the screenshots),
characters look slightly lower quality than those you'd find in games like WoW.  Not too bad
from what I can see, though I refuse to let my life get wrapped up in another MMO.

---

### Post by Ripfox on 2007-07-15
Well, I can tell you how I configured my audio in wine and it works fine...

winegfg
audio tab
alsa ONLY
hardware acceleration = emulation
default sample rate = 44100
default bits per = 16
driver emulation box checked

I don't know if I just got lucky or what, but this makes the sound work for me.

Cheers

---

### Post by Extreme Coder on 2007-07-15
Sounds nice, but I'd rather play and support an MMORPG that bothers to give out a Linux version of its client. So its Regnum Online for me now :)

---

### Post by cogadh on 2007-07-16
> **ripfox said:**
> Well, I can tell you how I configured my audio in wine and it works fine...

winegfg
audio tab
alsa ONLY
hardware acceleration = emulation
default sample rate = 44100
default bits per = 16
driver emulation box checked

I don't know if I just got lucky or what, but this makes the sound work for me.

Cheers
That worked, thanks I have sound now! \\:D/

---

### Post by Ripfox on 2007-07-16
Um...I downgraded to Feisty from testing Gutsy for awhile. and it was when I was on Gutsy that I discovered this game. The point is, whatever intel graphics driver they are shipping with Gutsy apparently works better than the intel driver in the Feisty repos? The game worked much faster for me in Gutsy...what might I be doing wrong or forgot? I am thinking of trying the 1810 driver...hmmm. My video is the GM915 in an hp dv6000.

Btw...Hikari, should this be added to UGA? I didn't know if you advertised wine compatible games there or not.

Anyone know the difference in those drivers, or what's the latest info on this troublesome integrated video?

Peace

---

### Post by MaximB on 2007-07-16
doesn't work for me
the installation went fine
then I registered, login , created a character but when I click enter world nothing happens, nothing at all !
I set my graphics to very low and followed this little wine guide and it still doesn't work.

---

### Post by Ripfox on 2007-07-16
I have everything on wine set to defaults except the sound fix mentioned earlier...do you have accelerated graphics enabled? What is the result of glxgears in the terminal?

Edit...I assume that isn't the problem judging from your forum status, but it was worth a mention? :)

---

### Post by jusmurph on 2007-07-16
I downloaded it, it installed fine. Went to launch it and **nothing happens**, I did not really fiddle with it * too tired * but I'm emulating Win 98 i think (for GW) and probably have probably got the video acceleration going.

How good is the gameplay?

---

### Post by Ripfox on 2007-07-16
I suggest creating a profile and emulating either win2k or xp, thats how I am running it. Seems like a fun game, you can also play it as a single player mode if you are anti-social. :)

---

### Post by Barbossa on 2007-07-17
> **ripfox said:**
> I suggest creating a profile and emulating either win2k or xp, thats how I am running it. Seems like a fun game, you can also play it as a single player mode if you are anti-social. :)


I just tried this game, It was extremely laggy even on a 12 meg cable connection using 256 DDR Nvidia vid card
2.4 Ghz Pent 4.
1 gig ram
Ubuntu 704

I'm in california so i donno if its just that the servers are like in Korea or something or what, took a hour to download all the in game patches @ 25-150 KB/s  :(

And no sound either.

---

### Post by Ripfox on 2007-07-17
Weird..I live in Nebraska and the patching completed in 2-3 minutes here on a 6meg cable connection.
Did you try the winecfg options I mentioned earlier in this thread for sound?

---

### Post by jusmurph on 2007-07-17
> **ripfox said:**
> I suggest creating a profile and emulating either win2k or xp, thats how I am running it. Seems like a fun game, you can also play it as a single player mode if you are anti-social. :)

How do you make different profiles?

---

### Post by Ripfox on 2007-07-17
Click on the "add application" tab in winecfg

---

### Post by jusmurph on 2007-07-17
Got it working, though the controls are a bit buggy and it does not go full screen (avant window manager & gnome panel still show)

---

### Post by cogadh on 2007-07-17
In winecfg on the Graphics tab, uncheck "Allow the window manager to control the windows". That should take care of the fullscreen problem.

---

### Post by Barbossa on 2007-07-17
> **Barbossa said:**
> I just tried this game, It was extremely laggy even on a 12 meg cable connection using 256 DDR Nvidia vid card
2.4 Ghz Pent 4.
1 gig ram
Ubuntu 704

I'm in california so i donno if its just that the servers are like in Korea or something or what, took a hour to download all the in game patches @ 25-150 KB/s  :(

And no sound either.

Nope i didnt try that, my bad! I'll try it right now and report back , thanks!

---

### Post by jusmurph on 2007-07-18
> **cogadh said:**
> In winecfg on the Graphics tab, uncheck "Allow the window manager to control the windows". That should take care of the fullscreen problem.

Cheers... though the game did not hook me so far... (black bear cubs owned me)

---

### Post by derred on 2007-07-20
there seams to be a free version but I get the feeling it's striped down. Planeshift has a linux version and it's free, even second life works as a linux binary so I don't see why this mmo is so great. Please correct me if I'm wrong.

---

### Post by cogadh on 2007-07-20
Generally speaking, free MMOs do not work in Wine. Its not that the game is great, its just that it is rare to find one that will actually run in Wine. 

Besides, Second Life is not really a MMO (its more like social networking) and you can only play so much Planeshift or Regnum, so even if the game isn't the greatest, it is an alternative to the currently limited choices on Linux.

---

### Post by Ripfox on 2007-07-20
> **cogadh said:**
> Generally speaking, free MMOs do not work in Wine. Its not that the game is great, its just that it is rare to find one that will actually run in Wine. 

Besides, Second Life is not really a MMO (its more like social networking) and you can only play so much Planeshift or Regnum, so even if the game isn't the greatest, it is an alternative to the currently limited choices on Linux.

Yea...I thought I would never find a free mmorpg that would run on wine....especially without much "hassle" :)

(cant seem to get into PlaneShift for some reason)

---

### Post by diodoros on 2007-07-22
ripfox,

I'm trying to run MoM in Feisty on an Intel GMA 950. It seems as though all of the program's functionality is there; only the graphics are unbearably slow (e.g., the mouse pointer won't even move smoothly). I'm wondering if we encountered the same problem. You mentioned that MoM works well with the intel driver in gutsy but not with the one in feisty. Did you figure out how to get it to run well in feisty?

Thanks!

---

### Post by Ripfox on 2007-07-22
The only thing I could find that worked reasonably well is to install the intel driver vs the 1810 driver in synaptic, then I lowered the settings in the game to "lowest" graphics...then it was playable again. Curse these intel drivers! I cannot wait until someone who knows what they are doing with this sort of thing releases some decent drivers for us poor saps with intel chips...:(

---

### Post by diodoros on 2007-07-22
Thank you for your help.

Unfortunately, the MoM had the same troubles with either driver on my system. I'll fool with it again when it comes time to install gutsy.

Indeed. I purchased a system with the Intel graphics hardware because it was the only one whose driver code was open source. But of course it doesn't follow that the drivers would therefore work better... Nonetheless, these things will get sorted out, I'm sure.

---

### Post by cogadh on 2007-07-22
For graphics cards, you are always better off going with Nvidia. They produce their own closed source Linux drivers that are just as good as their Windows drivers and are just as easy to install/configure. 

It's a sad truth, but open source doesn't *always* mean better software, it just usually does.:)

---

### Post by Ripfox on 2007-07-22
I still have faith that my intel 915gm will get ironed out.

---

### Post by Extreme Coder on 2007-07-22
> **cogadh said:**
> For graphics cards, you are always better off going with Nvidia. They produce their own closed source Linux drivers that are just as good as their Windows drivers and are just as easy to install/configure. 

It's a sad truth, but open source doesn't *always* mean better software, it just usually does.:)
That's because uses a shared codebase between all platforms, which allows it to release drivers for Windows,Linux, FreeBSD and Solaris with (almost) the same level of features and peformance.
Not like that other company *cough*ATI*cough*

---

### Post by nickless on 2007-07-23
looks promising, I think I will try it when my exams are over :)

---

