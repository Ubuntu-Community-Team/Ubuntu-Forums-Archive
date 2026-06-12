---
title: "Bad stuttering on L4D2 (Native) with Radeon 7850 on Ubuntu 12.04.4 x64"
date: 2014-03-06
forum: Gaming &amp; Leisure
---

### Post by xinghua31 on 2014-03-06
As title, I'm having really bad stuttering issues, as well as input latency too with L4D2 on Ubuntu for some reason. I'm using the post-release updates driver from System Settings -> Additinal Drivers. The game is completely unplabable in its current state. I've recorded a video to try and show the issue in more detail, but YouTube's processing has made it look slighty smoother than it actually runs. Anyway, here's the video lol.

[https://www.youtube.com/watch?v=kpx8wRXvaoM](https://www.youtube.com/watch?v=kpx8wRXvaoM)

On Windows 7 Home x64, I get a perfect 60 FPS with the settings maxed. On Ubuntu, I doubt I'm getting 30 even when it's not stuttering, or having input latency issues and sliding all over the place.. :/

My PC specs are:
AMD A8 5500 APU @ 3.3Ghz (3.7Ghz boost)
MSI FM2-A55M-E33 Motherboard
Kingston HyperX 4Gb 1600Mhz DDR3 RAM
XFX Radeon 7850 DD 2Gb GDDR5
Evo Labs Cronus 550W 80+ Modular PSU
Zalman ZM-T4 Mini Tower Case
Ubuntu 12.04.4 LTS x64

---

### Post by mastablasta on 2014-03-07
could the desktop special effects be affecting the game? i don't know who this is done in ubuntu but in Kubuntu there is a setting that automaticly disables special desktop effects when running full screen applications (such as games).

in 12.04 this could be tested by selecting Unity 2D or fallback mode on login.

edit: what kernel do you currently have? ```
uname-a
```

---

### Post by xinghua31 on 2014-03-07
Hi,
As far as I remember, Ubuntu with Unity has had the disable Compiz effects when fullscreen thing since at least the 12.04 launch days. I should have also mentioned the stuttering issue happens with fullscreen and windowed. I had to record windowed as Simple Screen Recorder didn't record anything fullscreen, although that's probably my fault, as I haven't used that program before.

I will test 2D mode in a moment, I'm busy trying to figure out a WINE issue ATM! :P

The current kernel is the default one Ubuntu updated with. Uname -a returns this;

> xinghua31@xinghua31-MS-7721:~$ uname -aLinux xinghua31-MS-7721 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
xinghua31@xinghua31-MS-7721:~$ 




---

### Post by Jake_Paine on 2014-03-07
Watching your video I have the exact same issue, I have 2x 6870's in crossfire (finally working correctly), randomly though it stutters constantly.

I'm on 13.10 x64 using Gnome 3 though. It seems to be the only source game that's doing it though. Half Life 2, Portal 2 are fine.

Out of interest, on a few games DOTA2 being one OpenGL crashes as soon as the game is started... Do you have any issues like that too?

---

### Post by xinghua31 on 2014-03-07
Hi,
I can run DOTA 2, but it as well is pretty stuttery, although nowhere near as bad as L4D2. Again, it isn't on Windows 7.

---

### Post by Jake_Paine on 2014-03-07
I installed some updates this morning and now I'm stuck at a black screen on start up... As soon as I get that sorted after work I'm going to have a little play around and see if I can even get a bit closer on the L4D issue :/

Lowering the settings doesn't work either it still stutters when I go from max to low.

---

### Post by xinghua31 on 2014-03-07
> **Jake_Paine said:**
> I installed some updates this morning and now I'm stuck at a black screen on start up... As soon as I get that sorted after work I'm going to have a little play around and see if I can even get a bit closer on the L4D issue :/

Lowering the settings doesn't work either it still stutters when I go from max to low.

Well that sucks! :(

I just tried Portal 1, and even that's stuttering, on a quadcore CPU and a Radeon 7850.... -_-

---

### Post by Jake_Paine on 2014-03-07
That's strange! L4D2 is the only Source game I've had issue with. Though Half Life 2 does drop from 350fps to 90fps in sections randomly which seems like a large drop...

Are you using the latest beta driver from the AMD site?

---

### Post by xinghua31 on 2014-03-07
I just tried the latest 14.2 Beta driver, and the stuttering is even worse lol. Also now the WASD keys no longer work for some reason...

---

### Post by Jake_Paine on 2014-03-07
Oh god, haha. Perhaps this is a AMD driver issue then? I have no idea how much of a performance difference using the free drivers from the repos will be but might be worth a shot.

The only driver thats currently working on 13.10 from AMD is the latest 14.2 beta. Did you try in the fallback desktop?

---

### Post by xinghua31 on 2014-03-07
If previous experience with the open AMD drivers on Ubuntu 12.04.x is anything to go by, then they're FAR too slow for actual use in gaming. 

And yes, the fallback Unity 2D desktop makes zero difference.

---

### Post by R33D3M33R on 2014-03-07
Same stutter here, HD7750, Catalyst 13.12 or fglrx-updates for 14.04, however, here is something interesting I discovered: this stuttering happens when level starts or in the middle of the level when something unusual happens (a big explosion for example). The more I play the game, less stuttering occurs and after everything loads in RAM, the stuttering completely disappears. Because I suspected this has something to do with loading things from the HDD, I fired up KSysguard and closely inspected HDD usage. **Every time the game locks up, there is a spike in disk read activity**! I have tried some tweaks to preload more data into RAM, however the stuttering never disappeared completely. This makes me think that preloading doesn't work correctly if fglrx is installed ...

---

### Post by Jake_Paine on 2014-03-08
Thats a good fine R33D3M33R. Not really sure what else we can do about this other than post it to the AMD forums :/

---

### Post by slooksterpsv on 2014-03-08
After you install the drivers are you having the AMD apps create your xorg.conf file? That's a possibility. It's like: 
sudo aticonfig --initial

NOTE: IF YOU'RE UNABLE TO GET BACK INTO THE WINDOWING ENVIRONMENT DO THE FOLLOWING (Write this down in case):

Xorg -configure
sudo mv ./xorg.conf.new /etc/X11/xorg.conf

(notice capital X and 1 hyphen)

---

### Post by Jake_Paine on 2014-03-09
> **slooksterpsv said:**
> After you install the drivers are you having the AMD apps create your xorg.conf file? That's a possibility. It's like: 
sudo aticonfig --initial

NOTE: IF YOU'RE UNABLE TO GET BACK INTO THE WINDOWING ENVIRONMENT DO THE FOLLOWING (Write this down in case):

Xorg -configure
sudo mv ./xorg.conf.new /etc/X11/xorg.conf

(notice capital X and 1 hyphen)

Thanks! Given that a go, I had a feeling I've already tried this but gave it a go, and no luck. However reading on the AMD driver page it says for optimal performance you need to enable POSIX shared memory. Not sure if that will or should make a difference with desktop graphics but just giving that a go now too. Fingers crossed!

Update: Nope. Still no better

---

### Post by slooksterpsv on 2014-03-09
In L4D2 do you have VSYNC enabled or is that an option? I believe it is and it may be under advanced.

---

### Post by Jake_Paine on 2014-03-10
Many thanks! I have tried it enabled and disabled - I really suspect theres not much that we can do I think this just down to AMD driver issues.

TF2 is also having the same issues for me so I suspect its not just a L4D2 issue as others have said.

---

### Post by xinghua31 on 2014-03-11
> **Jake_Paine said:**
> Thanks! Given that a go, I had a feeling I've already tried this but gave it a go, and no luck. However reading on the AMD driver page it says for optimal performance you need to enable POSIX shared memory. Not sure if that will or should make a difference with desktop graphics but just giving that a go now too. Fingers crossed!

Update: Nope. Still no better

Yes, I've tried disabling V=Sync. It had no effect.

---

### Post by mastablasta on 2014-03-11
what about with opensource drivers using latest kernel? also bad?

curse you AMD. i had such high hopes for you! :-)

---

### Post by dannyboy79 on 2014-03-12
yeah, try out 3.13+ kernel plus Oibaf's PPA for the updated source radeonsi driver

---

### Post by Chuck_Finley on 2014-03-25
Any luck guys? I have a 7950 video card with all these same issues. L4d2 is especially unplayable. I am also sure it has something to do with "pre loading" as just loading a game takes several minutes.

---

### Post by Chuck_Finley on 2014-03-25
I reduced sound quality to low and a lot (not enough) of the stuttering went away. I wonder why that is..

---

### Post by mastablasta on 2014-03-26
because instead of GPU doing all the graphics computing it seems a portion of it is passed to CPU which also handles the sound. reducing the sound quality freed up more CPU for the grpahics computing. just a guess.

---

### Post by R33D3M33R on 2014-03-26
It would be great if someone who has a Github account could open a bug report in the Valve Github issue tracker: [https://github.com/ValveSoftware/steam-for-linux/issues?labels=&page=1&state=open](https://github.com/ValveSoftware/steam-for-linux/issues?labels=&page=1&state=open)

---

### Post by Chuck_Finley on 2014-03-27
Well I just purchased a 750 ti video card. I will let you guys know if this solves all the issues. My cpu shouldnt be a problem as I have a amd 8350. This cpu should be able to handle these games

---

### Post by mastablasta on 2014-03-27
oh wow, that card costs almost one salary of mine.  edit: <<--- disregard i mistook it for 780 ti, but i  still feel that...

now your card is "green" but so is my face... :mrgreen:

---

### Post by Chuck_Finley on 2014-03-31
Alright I installed my 750ti using the latest drivers from nvida. Loading times have decreased by minutes. l4d2 single player used to load for 3 minutes and now only takes 1. That being said,

the stuttering still continues. So the stuttering is not due to amd! Unfortunatley I think the next step is a new hard drive... or do you guys think this is totally valves problem?

---

### Post by Chuck_Finley on 2014-03-31
SOLUTION FOUND!!

In steam console type 

snd_updateaudiocache

Give it a few minutes to load 

more information here:

[http://forums.steampowered.com/forums/showthread.php?t=2147462](http://forums.steampowered.com/forums/showthread.php?t=2147462)

---

### Post by R33D3M33R on 2014-10-07
I have installed the opensource drivers on the same system as stated above. The game/level loading times have decreased, but the stutter at start of the level or unusual events is still there. Sure, it's not as severe as with FGLRX, since it's much shorter, but still ... snd_updateaudiocache doesn't seem to help.

---

