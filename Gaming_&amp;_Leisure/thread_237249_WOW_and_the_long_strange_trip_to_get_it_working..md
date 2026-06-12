---
title: "WOW and the long strange trip to get it working."
date: 2006-08-15
forum: Gaming &amp; Leisure
---

### Post by DNSBubba on 2006-08-15
First, allow me to say that I am loving Ubuntu. I used to use Linux and Unix in my professional life years ago (Mostly just command line stuff), and due to a recent spy ware/virus infection (That no one here will own up to), I decided to move to Linux for most things.

Like many here, if I can get a few choice programs (or the Linux equivalent) working, I'll make the move for good.

Which brings us to World Of Warcraft. I like the game, but I really don't play it that much. The wife however, is going to have kittens if I can't get it working.

I have Wine installed, and the program runs and I get sound and everything. For the whole 10 seconds before the sucker locks up tighter than a duck's exhaust port, if you get my meaning.

It looks good, no graphical issue's or anything, but it simply won't seem to stay running. It doesn't exit, or shut down, just locks up.

I've been searching around the net for the better part of the day, trying various fixes, but nothing seems to solve it.

In addition to that issue, I can't seem to find a way to exit out of it back to the desktop, once it does lock up, other than restarting the whole system. Any help with that as well will be most appreciated.

Machine Specs:
NVIDIA nForce 410 Chipset Motherboard
AMD Athlon 3400+ processor 
Radeon x1600 512mb video card (PCI-E)
1gb DDR Ram

Again, let me say that I really like Ubuntu. No issues with the system itself, just this one program.

---

### Post by parsons151185 on 2006-08-15
Your not allown, I have the same problem but on my laptop which I cant restart as it doesnt have a restart button, its the off button for me, defantly not the best way but what can you do? Ubuntu, like you say is fine behind the locked up World of Warcraft (press the power button sound stops for a moment and then starts again)

DNSBubba:
What command do you use to launch it?

I use
```
wine "C:\games Files\World of Warcraft\Wow.exe" -opengl
```

I have been running on here a little, not very much maily because why Play an unstable version of WoW when you can play Warcraft 3:FT on a network game using the map "BoTa6.23 AI 1.90" and then play WoW when I return home from my friends using Windows *Grumble*

Fujitsu-Siemens Amilo A 7620
AthlonXP-M 2600+
1024GB DDR333
ATI Mobility Radeon 9000
fglrxinfo returns
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY/RADEON 9000 DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)
```
I dnt know if thats the correct version of the drivers as I have patched them as the newer drivers broke the Radeon 8500-9200, I found [the fix here](http://ubuntuforums.org/showpost.php?p=1071197&postcount=6)

---

### Post by AngryKidJoe on 2006-08-15
Did you install the Nvidia patch before compiling Wine?

---

### Post by DNSBubba on 2006-08-15
I didn't compile it, just downloaded and installed the most current binary that I could find.

Was that the wrong way to go about it? I have no problem removing it and doing the whole thing over if it will solve the problem.

Thanks for responding.

---

### Post by DNSBubba on 2006-08-15
I use the same command you do. It looks good, and the sound seems to be okay, the sucker just will not stay running.

Thanks for your response.

---

### Post by parsons151185 on 2006-08-16
I treid compiling 0.9.18 from source seeing there was no deb for it, but now there is 0.9.19 in deb format I installed that but when I open winecfg it still says 0.9.18
I haven't used and patches on 0.9.18, I used a patch on 0.9.17 seeing my ATI was coursing problems

Why would you install a patch for an Nvidia card when you to are using a ATI card?

I'd like to solve it aswell, then I can join my friends on WoW when Im at there houses and not just when I am at home

---

### Post by Waste on 2006-08-16
In response to your not being able to shut WoW down when it locks up, I set my virtual desktops to my F9-F12 keys so I can switch while WoW is running.
It also allows me to switch when WoW locks up.
Mind you though, I use Cedega, but I don't see why you couldn't do the same under Wine.

---

### Post by DNSBubba on 2006-08-16
Great idea! Thanks!

---

### Post by DNSBubba on 2006-08-16
Okay, tried that, but same deal. It seems to hard lock the whole system. But thanks for the advice, I do appreciate it.

---

### Post by DJRockoBobo on 2006-08-18
I couldn't get it working with doctor seven's mkdir......instead i've used 

wine WoW.exe -d3d

here i've changed some video settings and then i've used opengl

---

### Post by parsons151185 on 2006-08-18
so fare so good with the newest version of the drivers from ATI

follow the [instructions here](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.28.8_drivers_in_Ubuntu_Dapper_Manually)

---

