---
title: "sdlmame stutters &amp; skips"
date: 2010-06-03
forum: Gaming &amp; Leisure
---

### Post by Objekt on 2010-06-03
I recently installed the GMAMEUI frontend (version 0.2.11, from the Ubuntu 9.10 repository) and started playing some old games.  All games exhibit a weird performance problem, in which the video will get jerky and stuttery for no obvious reason & stay that way for several seconds at a time.  The degree of the stuttering varies, but it happens in all games, including at least: Burger Time, Ms. Pacman, Vs. Excitebike, and Bad Dudes.  Often, the jerkiness is enough to cost me a life in whatever game I'm playing.

I've watched the sdlmame process (the actual binary that's running the games, called by GMAMEUI) in System Monitor while playing games.  When games are running smoothly, sdlmame cpu use hovers around 30%.  The stuttering usually starts when sdlmame's CPU usage passes 40%.   Occasionally, it spikes to 80-100%.

The audio doesn't get distorted along with the sound, for some reason.  But the jerkiness makes playing games this way pretty worthless.

I know it's an emulator, but there's no way my hardware (listed in sig) should have any difficulty running an arcade game from 30 years ago.

FWIW, I do have the proprietary Nvidia drivers installed.  None of the games are 3D though, so it shouldn't matter, right?

I run the realtime Linux kernel (2.6.31-9-rt), instead of the standard one, which might matter.

The same games work just fine in MAMEUI under Windows XP.  No hitches or stuttering there.  That is why I think it's an Ubuntu problem, or possibly an sdlmame problem.

What gives?

---

### Post by hikaricore on 2010-06-04
You don't by any chance have desktop effects of any sort enabled do you?
Also what version of sdlmame are you using?

---

### Post by Objekt on 2010-06-04
No, I turned off all desktop effects a while back. 

According to Synaptic, sdlmame is version "0.132-0ubuntu1."

I dug up one old thread on sdlmame that suggested skipping can be a PulseAudio-related problem.  However, I'm not getting the audio artifacting & distortion others have had.  It's just video.

In some games, it manifests as the player character teleporting from one screen location to another.

I could try running with PulseAudio disabled (e.g. killing it in System Monitor), but then I would have no sound at all, which is even less fun that occasionally-stuttering video.

---

### Post by BigSilly on 2010-06-04
Would ```
sdlmame -ad sdl
``` work with this emulator? Could be worth a try. This would set sdl as the audio driver rather than PulseAudio. You only have to do it once, not every time you want to play. I know this method works with ZSNES...

---

### Post by Objekt on 2010-06-04
That didn't work.  Here's how it went at the command line:
```
objekt910@objekt910-desktop:~$ sdlmame -ad sdl
Loading BDF font... (256 characters loaded)
Loading BDF font... (512 characters loaded)
Loading BDF font... (768 characters loaded)
Loading BDF font... (1024 characters loaded)
Loading BDF font... (1280 characters loaded)
Loading BDF font... (1536 characters loaded)
Generating cached BDF font...
sdlvideo_init: Initialization failed!

```

Still have the stuttering when running games.

I also tried playing after killing pulseaudio.  No sound, but no video choppiness either.

WTF is the deal with Pulseaudio?  It seems to cause as many problems as it solves.

---

### Post by hikaricore on 2010-06-04
Pulseaudio works fine, it's all the shitty integrated audio hardware these days that's the problem.
If you think pulse is bad you should have seen the mess 5 years ago when every damn piece of software wanted to use a different audio protocol and had to fight over the hardware.

---

### Post by Objekt on 2010-06-04
A Soundblaster Audigy 2 ZS is hardly "shitty integrated audio hardware."  Are you saying I need to turn off the motherboard sound device in BIOS?  I have one of those too, but I never use it.  Still could be causing problems, I guess.

Update:

Sheesh, I wish someone had suggested that MONTHS ago!

I rebooted & turned off my onboard sound device in BIOS.  [a]Looks like the problem with sdlmame is licked - no mysterious slowdowns so far.  [/s]

It also seems to have solved an unrelated problem with the Linux client for Teamspeak 3.  Previously, it would use 100% of both cores after running for a few minutes, so I couldn't actually use it while playing games.  Now it purrs along with maybe 2% CPU use, which is how it's *supposed* to work.

---

### Post by hikaricore on 2010-06-04
I keep trying to people I'm always right but they never listen.  :p

---

### Post by Objekt on 2010-06-06
Nevermind, sdlmame is still broken.  It still consumes 100% (or more) CPU at random, for several seconds at a time.  I was playing Ms. Pacman just now & it was particularly bad.

Teamspeak 3 continues to behave itself, so at least that issue is licked.

update:
FWIW, as you and I expected, pulseaudio has nothing to do with the slideshow effect.  Killing the pulseaudio process in System Monitor neither reduces nor increases the random hiccups.

I signed up for the SDLMAME forums & am discussing it there.  Will post here if I get a fix there, as I suspect other Ubuntu users are having the same problem.

---

### Post by mocha on 2010-06-10
This is an old pulseaudio sdl issue and still not fixed in Lucid.  Try installing the libsdl esd (search for that) package.  Then at the bottom of mame.ini change the sdl audio option to "esd" instead of "auto".

---

### Post by Objekt on 2010-06-10
OK, I swapped "libsdl1.2debian-pulseaudio" for "libsdl1.2debian-esd."  Also changed my mame.ini file to include the following:
```
#experimental
audiodriver               esd
```

That *should* mean I'm using esd for sound now instead of pulseaudio, when running MAME.  I haven't yet played enough to see whether the problem has gone away, since it was intermittent anyway.

No, that didn't fix it.  Still getting slow video at random times.

---

### Post by jaymzw on 2010-08-09
I've had this problem forever, have experimented with tons of different options but still have no idea how to fix it.  Like clockwork, every few seconds the display jerks.

---

### Post by Objekt on 2010-08-12
It's less predictable for me, but yeah, I've pretty much given up on fixing the problem.

The funny thing is, the Windows version of MAME doesn't necessarily work any better.  Some games - Ridge Racer in particular - are completely unplayable under Windows, where they're at least somewhat serviceable under Linux.  Go figure.

But I've moved on from retro arcade gaming in general.  Got my fill of it, I guess.

---

### Post by jaymzw on 2010-08-14
I see it in sidescrollers a lot.  rthunder exhibits the problem well - if you run to the right you can see the stutter, particularly with a lot of characters onscreen.  It's very regular for me, every few seconds - jerk jerk jerk, then normal, then jerk-jerk-jerk.

I wonder if it is somehow related to the dirtyrect scheme?

---

### Post by jaymzw on 2010-08-14
Actually -refreshspeed together with -waitvsync even it out so that it is more consistent.  So the issue probably lies in trying to match up refresh rates with the sync rate of the monitor.  Triple buffering might help but it doesn't seem to be present in sdlmame.

Maybe the new video scheme in sdl1.3 will help.  Too bad it isn't compatible with the current mame binary.

---

### Post by BigSilly on 2010-08-14
> **Objekt said:**
> It's less predictable for me, but yeah, I've pretty much given up on fixing the problem.

The funny thing is, the Windows version of MAME doesn't necessarily work any better.  Some games - Ridge Racer in particular - are completely unplayable under Windows, where they're at least somewhat serviceable under Linux.  Go figure.

But I've moved on from retro arcade gaming in general.  Got my fill of it, I guess.

I honestly don't get these problems with sdlmame, and I can't tell you what I'm doing right to be able to help. I will say though, that the nature of MAME emulation would probably mean that at it's current state, something like Ridge Racer will be far off playable yet on any OS.

---

### Post by Objekt on 2010-08-14
I think someone got tired of waiting for MAME to handle the Ridge Racer series, because there's a standalone emulator for Namco System 21 hardware called "Vivanonno."

System 21 is, of course, the arcade machine that runs the first three Ridge Racer games (RR, RR2, Rave Racer).

Vivanonno works flawlessly, but unfortunately is only available in a Windows version.  I don't see why it couldn't be recompiled for Linux, but as far as I can tell no one has done so yet.  It was last updated in 2002 or 2003 and appears to be an abandoned project.

---

### Post by mocha on 2010-08-16
Try turning on opengl vsync in your video card driver, make sure you use opengl rendering and waitvsync in mame.ini, and turn off everything else such as autoframeskip.  I know on my system turning off autoframeskip makes all games smooth.  The modern ubiquitiousness of LCD screens sure causes a lot of problems with apps like mame.

---

### Post by Objekt on 2010-08-19
I have both CRT and LCD monitors, but I play MAME on the CRT.  So what are you saying?

---

### Post by BigSilly on 2010-08-20
I notice in your sig Objekt that you are using Ubuntu 9.10. I can't say I had problems with MAME especially when I used that myself, but I will say that now I'm Ubuntu 10.04 (64 bit also) a lot of game related audio problems have since vanished. I had audio issues with various apps on 9.10, such as Kega Fusion and Penumbra etc. It could be worth upgrading.

FWIW, I'm using MAME on an LCD monitor and it's been great. Just as good as my old CRT, if not better.

---

### Post by Objekt on 2010-08-23
I know sound problems with MAME are pretty common for Ubuntu users, but it's one part where I've yet to have a problem.  It's the video lag that is annoying & distracting.  In fact, I have had zero sound-related problems in general, once I switched off my motherboard's built-in sound hardware (it didn't play nicely with PulseAudio for some reason).

I've set automatic frameskip to "off" in GMAMEUI, and checked "Sync to VBlank" in the Nvidia X server settings application.  We'll see whether that fixes the video lag.

update:

Yep, looks like the video stuttering is gone!  I guess this one is solved.

---

### Post by Objekt on 2010-08-24
Hmm, thought I posted an update here but I guess I never got around to clicking "Submit."

Anyway, I am happy to report that the video stuttering seems to be fixed.  I made the changes suggested above (turn off frame autoskip in GMAMEUI, turn on "wait for sync blanking" in the Nvidia Xserver settings applet) and I guess those two things did the trick.  I no longer get the "freeze for a few seconds, then rapidly 'catch up'" video that I was getting, at least in the few games I've tested.  I'll have to play a bit more to be sure, of course.

---

