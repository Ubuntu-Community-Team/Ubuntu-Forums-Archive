---
title: "What's so great about sdlmame?"
date: 2009-10-16
forum: Gaming &amp; Leisure
---

### Post by codefenix on 2009-10-16
I have been playing around with both xmame and sdlmame, and I can't help but wonder why xmame development ever ceased.  It seems vastly superior, in terms of performance, to sdlmame.

I've found many posts urging users to use sdlmame instead of xmame.  But for every one of those, there are about five posts from sdlmame users complaining about poor speed, ugly graphics rendering, and choppy sound.

I installed sdlmame from the repositories.  Sorry, but I don't remember which version (I'm not at home right now).  My best guess is 0.134, but I forget the alpha suffix.

The first game I tested was pacman, which worked fine with an average speed of 100%.  Next I tried dkong, which could only manage about 78%, and had horrible sound.  I'd like to report the speeds for kof or sfa, but I start crying every time I think about them.

I have tried:
 - Disabling antialiasing
 - Changing from opengl to soft
 - Setting autoframeskip to 1
 - Setting filter to 0
 - Setting switchres to 1 and using lower resolutions, 640x480, 320x240, etc.
 - Using multithreading
 - I am using alsa, not pulseaudio
 - Using different graphics drivers (see below)

Nothing I do seems to help.  The overall experience in sdlmame for me has been abysmal at best.  I've got half a mind to uninstall sdlmame and go back to xmame.  I'm just bummed about it because I really wanted sdlmame's updated rom list and its ability to run every game in a full screen without changing the monitor's video mode-- it's a real hassle to keep changing the width/height & vert/horz position every time a different game is run, especially if the monitor is to be installed in a cabinet.

I am not using any desktop effects, like compiz.  I also removed most nonessential applications like bluetooth and print services from startup (those things won't be missed in a cab!).

As for my specs:
 - AMD Athlon XP1500
 - NVidia GeForce FX 5200, Using latest proprietary driver 173, and tried 96
 - 320 MB RAM
 
Admittedly, it's an old box, but the specs are ample enough to run everything else I throw at it (ZSNES, Gens/GS, FCEUX, Dosbox) with no issues whatsoever.

So does anyone have a definitive solution, or at least a suggestion I haven't tried yet?  I really don't want to resort to using a dead project.  But it would be better than an active one that struggles just to play dkong!

Thanks

---

### Post by DoktorSeven on 2009-10-16
dkong was updated in mame mainline to use actual sound emulation rather than samples, therefore it's MUCH slower than it used to be.  xmame, meanwhile, is frozen back in the old times where it still used samples.  For some reason you need a decent system to emulate dkong with its new implementation at full speed.  I used to have a system similar to yours and got the same results when MAME switched dkong to its current implementation.  

Basically sdlmame is updated along with mainline MAME which makes these changes and it DOES work better on many games.  Basically, you're just seeing the result of one game being changed.  Play several other games, you should see pretty much the same performance as the older xmame.

---

### Post by BigSilly on 2009-10-17
That's right. It's not Sdlmame's fault so much as it's regular Mame's fault. It updates all the time, and stuff gets broken sometimes. It's a real pain to be honest, so I usually just grab one particular version of the emulator and stick with it. I'm currently using version 0.130, and that's what I'll use for some time yet. I still think it's much better than the old Mame's though.

---

### Post by codefenix on 2009-10-17
Thanks for the responses, DoktorSeven and BigSilly.

Well, I downgraded to 0.132, and performance has increased dramatically.  Even mvsc is running at near full speed now.  I'll continue to tweak the settings until I hit that sweet spot.

Thanks!

---

### Post by codefenix on 2009-10-20
Well, another problem has presented itself.  Now, in the middle of a game (doesn't seem to matter which one), it freezes.  Video, sound, everything freezes and the computer doesn't respond to any keystrokes.  Only way out is to  hold the power switch on the front of the case to do a hard power-off-power-on cycle.  This has happened about a half a dozen or so times.  I'm guessing that my 320 megabytes of RAM just isn't enough to keep sdlmame happy.

So for now I've decided to revert back to xmame until I replace the hardware.  Shame.  I really liked all the options and features in sdlmame.

---

### Post by disturbedite on 2009-10-20
> **codefenix said:**
> Well, another problem has presented itself.  Now, in the middle of a game (doesn't seem to matter which one), it freezes.  Video, sound, everything freezes and the computer doesn't respond to any keystrokes.  Only way out is to  hold the power switch on the front of the case to do a hard power-off-power-on cycle.  This has happened about a half a dozen or so times.  I'm guessing that my 320 megabytes of RAM just isn't enough to keep sdlmame happy.

So for now I've decided to revert back to xmame until I replace the hardware.  Shame.  I really liked all the options and features in sdlmame.

yeah, in this day and age 320 MB of RAM doesn't cut it with much.

---

### Post by DoktorSeven on 2009-10-20
Sounds more like a hardware or driver issue to me.  At worst a memory issue would slow things down a bit or just crash the application (does CTRL+ALT+F2 bring up a terminal where you can log in and kill sdlmame, then switch back to X using CTRL+ALT+F7?).

sdlmame probably does use a bit more memory than the older xmame, but I don't think it would do anything as drastic as completely crash your system.

---

### Post by CharmyBee on 2009-10-20
Try vesa for video. Maybe the FX5200 is badly implemented for 2D (i've heard bad things about that card in emulation)

---

### Post by codefenix on 2009-10-20
DoktorSeven-- all functionality locked up, unfortunately.  No keystrokes or sequences of any kind work during this freeze up.

CharmyBee-- thanks for the suggestion, but I think that would be a little extreme, given the **one** program I'm having difficulty with.  I would hate to sacrifice the quality of all my other working programs, just to placate sdlmame.

I truly appreciate all the input, but I think for now I'll have to stick with xmame.  Even though sdlmame boasts a nicer feature set, there is really no benefit for me to switch to it.  I'll revisit the idea in the future should I decide to replace this hardware.

---

### Post by williamts99 on 2009-10-24
> **codefenix said:**
> 
 - I am using alsa, not pulseaudio


I know you said that you were not using pulseaudio, but there is a fix for those of you that are that worked for me, and that was installing libsdl1.2debian-pulseaudio

sudo apt-get install libsdl1.2debian-pulseaudio

Just FYI,

Williamts99

---

### Post by Bagleemo on 2009-10-24
> **codefenix said:**
> Well, another problem has presented itself.  Now, in the middle of a game (doesn't seem to matter which one), it freezes.  Video, sound, everything freezes and the computer doesn't respond to any keystrokes.  Only way out is to  hold the power switch on the front of the case to do a hard power-off-power-on cycle.  This has happened about a half a dozen or so times.  I'm guessing that my 320 megabytes of RAM just isn't enough to keep sdlmame happy.


I'm seeing the same problem, Karmic RC1, 2Ghz processor, 512 Ram. Also, when it does run, it doesn't reach 100% speed. So I don't think insufficient hardware is the reason for the problems you are seeing. I think sdlmame is probably a wee bit buggy.

---

### Post by williamts99 on 2009-10-25
> **Bagleemo said:**
> I'm seeing the same problem, Karmic RC1, 2Ghz processor, 512 Ram. Also, when it does run, it doesn't reach 100% speed. So I don't think insufficient hardware is the reason for the problems you are seeing. I think sdlmame is probably a wee bit buggy.

What is your processor usage like and which rom(s) are you using?  Are you using sdlmame from the repos, source or debs/repos from [http://sdlmame.wallyweek.org](http://sdlmame.wallyweek.org)

---

### Post by BigSilly on 2009-10-30
Yup. Interesting problems here now too with sdlmame. Using Karmic 64 bit, and it freezes at random moments during use. Sometimes I can be selecting a game and it'll freeze. Other times it crashes when exiting the program. I'm also getting no sound, but I'm sure that's easily solvable next to the crashes. Like Codefenix, it completely locks up the system, and only a hard reboot will do.

Gutted. It's the first time I've ever had any issues with sdlmame. :(

EDIT: Installing any of the older packages from wallyweek still shows exactly the same behaviour. Perhaps this is an Ubuntu thing rather than an sdlmame issue...?

---

### Post by BigSilly on 2009-10-30
Noticing if I leave the emu when its crashed, eventually it brings up an error message on the window bar - "No driver loaded [empty]".

Anyone know what this could mean? Thanks.

---

### Post by DoktorSeven on 2009-10-30
Running sdlmame from repos in 64bit Karmic here with no issues; just ran Donkey Kong and Street Fighter III: Third Strike with no slowdowns, no lockups, no crashing (AMD quad core, 4GB RAM, onboard ATi HD chip).  I am running under Kubuntu though; could something like pulseaudio be causing some of the issues you are all seeing?

---

### Post by BigSilly on 2009-10-31
> **DoktorSeven said:**
> Running sdlmame from repos in 64bit Karmic here with no issues; just ran Donkey Kong and Street Fighter III: Third Strike with no slowdowns, no lockups, no crashing (AMD quad core, 4GB RAM, onboard ATi HD chip).  I am running under Kubuntu though; could something like pulseaudio be causing some of the issues you are all seeing?

I suppose it could. How would I go about disabling it for this emulator? Is there an easy way? I'll try anything! :D

---

### Post by BigSilly on 2009-10-31
/holds breath

I think I may have fixed it!

Thanks to your post Doktor, I decided to look at what pulseaudio packages I have installed, and noticed I didn't have libsdl1.2debian-pulseaudio installed. I installed that, along with padevchooser and whatever that brought up with it, then ran-

```
sdlmame -ad sdl
```

-to set the audio driver. So far, everything seems absolutely fine. Phew eh?

Thanks for the heads up anyway. :)

---

### Post by codefenix on 2010-02-22
Well, I thought I'd check in and report that I'm no longer having any problems with SDLMAME (yet).  I decided to take a whole new approach and tried installing xubuntu-desktop.  As xubuntu uses fewer resources than its gnome-counterpart, I think it's safe to conclude that the system halts and performance issues were all due to a lack of memory.

Some of my results so far:
dkong reported a speed of 100%
pacman ... 100%
mspacman ... 100%
mvscu ... 99.64%
sfiii3 ... 90.04%

So my confidence in SDLMAME is more or less restored, but I'm not quite ready to put this issue to bed yet.  I plan on doing much more play testing before I commit this box to my cabinet, and I may just go ahead and max out the ram while I'm at it (tops out at 768 MB-- did I mention it's an old box?).

One last thing.  Do I see correctly on the [site's homepage]("http://sdlmame.wallyweek.org/") that "SDLMAME is no more"?  What does this mean for SDLMAME users?

---

### Post by williamts99 on 2010-02-22
> **codefenix said:**
> 
One last thing.  Do I see correctly on the [site's homepage]("http://sdlmame.wallyweek.org/") that "SDLMAME is no more"?  What does this mean for SDLMAME users?

Glad to hear that it is working well for you now.

SDLMAME is included with regular MAME as of 0.136u1, it's just all unified now. [http://rbelmont.mameworld.info/?p=519](http://rbelmont.mameworld.info/?p=519)

---

