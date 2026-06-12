---
title: "Need help with ePSXe.."
date: 2007-10-06
forum: Gaming &amp; Leisure
---

### Post by tcoffeep on 2007-10-06
Hey all, this is a question regarding ePSXe in Ubuntu Gutsy...

I'm trying to run it, and it'll work, methinks, but there's one problem...the dependencies...


+ libncurses.so.5   [GOT THIS ONE]
+ libdl.so.2   [GOT THIS ONE]
+ libXt.so.6
+ libz.so.1
+ libgtk-1.2.so.0
+ libgdk-1.2.so.0
+ libgmodule-1.2.so.0
+ libglib-1.2.so.0
+ libXi.so.6
+ libXext.so.6
+ libX11.so.6
+ libm.so.6   [GOT THIS ONE]
+ libc.so.6   [GOT THIS ONE]
+ libSM.so.6
+ libICE.so.6
+ /lib/ld-linux.so.2     [GOT THIS ONE]

I know I have a couple of these, including libncurses, but there're some that I just can't seem to find. Anyone know of any ideas?


[edit] : I've all the plugins, plus the BIOS. Just in case anyone posts anything pertaining to those...

---

### Post by DoktorSeven on 2007-10-06
I'm pretty sure it has all the dependencies by default -- did you try running it?

Run **ldd** (from the terminal) on the main binary plus the plugin .so files and see if there are any that aren't found.  You can then search for them by installing **apt-file** and searching for the libraries with it.

---

### Post by tcoffeep on 2007-10-06
Yeah, I tried running it, but nothing comes of it. I've tried running it by double-clicking on the launcher, and by typing it in terminal. Nothing comes of it.

---

### Post by acoustibop on 2007-10-06
IMHO I'd use [pSX Emulator]("http://psxemulator.gazaxian.com/") instead.  In Feisty, the only library you need to install is libgtkglext1 for it to run, there are no plugins needed and configuration is easy.  It's such a nice emulator, too.

---

### Post by tcoffeep on 2007-10-06
I am running Gutsy though...

---

### Post by tcoffeep on 2007-10-06
pSX Emulator worked rather choppy on my system, but then again, it could've been because I'm running Gutsy and the libraries (might) be different.

---

### Post by DoktorSeven on 2007-10-06
So typing ./epsxe in the terminal does absolutely nothing?  Doesn't even output any text?  That's unusual.  Make sure you're actually running it from the directory you extracted it to.

pSX does run more slowly in my experience on some systems (particularly older ones) than ePSXe, which generally runs fast on all but the most ancient systems, so I always suggest ePSXe over pSX for most people.

---

### Post by disturbedite on 2007-10-06
pSX runs pretty well on my quite outdated system.

Intel P4 1.8ghz (no HT)
640MB PC2100 DDR
Intel Integrated i845G Video w/ Intel driver

---

### Post by zmb0386 on 2007-10-06
I have the same problem, when I try and run epsxe absolutely nothing happens.  No text or anything from the terminal.

It was working on Gutsy until very recently, and then (like compiz, around the same time) it broke for me.  The perils of using the development version, I suppose.

---

### Post by FranMichaels on 2007-10-06
How about pcsx, it's in the Ubuntu repositories. 
Although to be honest I usually use my psone or PS2...

But it seems to run pretty well I think. :KS

---

### Post by Sockerdrickan on 2007-10-07
ePSXe how2:

Step 1: Get pSX

---

### Post by acoustibop on 2007-10-07
LOL!  All three emulators, pSX, ePSXe and PCSX will run well on reasonable machines if properly installed and configured.  It's just that pSX is _much_ easier to install and configure.

@tcoffeep: if pSX is running choppily, disable Frame skipping and increase the values for the sound Latency sliders.

Contrary to what DoktorSeven says, most people seem to find that pSX runs better than ePSXe on slow machines.  It's possible, I suppose, that on a slow machine with a fast videocard, you could be using the videocard in ePSXe (or PCSX) to offset the load on the CPU.  The videocard doesn't make much different in pSX, since it emulates in software, so the CPU is doing pretty much everything.

And most slow machines, of course, will have similarly levelled videocards...

---

### Post by tcoffeep on 2007-10-07
Well, I back-tracked, and re-installed Feisty, and I've gotten the GUI back up-and-running, now there's only a little fsck-up. I'll quote verbatim :

> plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetCliplarocque@larocque-laptop:~/Desktop/epsxe$ 

So, I noticed it was the crdmooby that was doing something...so, I took it out...and it works, well, it works as far as the GUI, and the ability to test out the BIOS, but something goes really slow or something, and it is unresponsive to any buttons pressed.

I've tried all 3 emulators, yet ePSXe is the one that comes closest to ACTUALLY fixing the problem. pSX glitches in the first five seconds, and pcsx will actually go to both BIOS and FFIX, but it takes about 5 minutes to get through BIOS, and the sounds and video are cut and chop...

I've ran these programs before. Anybody got any idea what's wrong??

---

### Post by tcoffeep on 2007-10-07
@acoustibop :

I'll try that, thanks.

---

### Post by DoktorSeven on 2007-10-07
Generally, if ePSXe gives you these errors or has these problems, try another plugin.  I use the following with best results:

Video: Pete's MesaGL 

Audio: P.E.Op.S. OSS

Input (Ext. Game Pad): ammoQ's padJoy

I don't use any CD/image drivers since the builtin seems to work just file with both physical CDs and CD images.

And I'm really not sure how people are doing well with pSX unless it runs well with a better system than mine (a now ancient P4 with not a huge amount of memory).  I get audio stuttering and lag, some games are terribly slow, and other huge lags (in Castlevania: SotN it takes forever for the item screen to come up).  ePSXe has none of these issues with most games.

---

### Post by acoustibop on 2007-10-07
A P4 and it won't run pSX perfectly?  You've got to be kidding, DoktorSeven!

It runs smoothly, but with slowdowns on some games, on an Athlon 1600+ I have, and every machine I've tried with an Athlon 2000+ or better, or Pentium equivalent, has run everything I've tried perfectly.  Even games that exhibit slowdowns in some places in ePSXe on the same machines (Chrono Cross battle commencement, for instance) run perfectly in pSX.

There will, of course be compatibility problems with individual games on every emulator, and there will be games that one emulator will run better than the other, but across the board, I have to say, pSX performs much better than ePSXe.

And, in case you think I'm prejudiced against ePSXe, I was using it very happily for 5 or 6 years before pSX came along.  But it didn't take long to realise just how much better pSX is - or was, even in the early releases.

---

### Post by tcoffeep on 2007-10-08
None of them seem to work in Gutsy...

I've a Dual-Core AMD Turion64, 1.6 Ghz, with a ATI Radeon Xpress 200m card...

PCSX is the only one in the repos, and none seem to respond to my button mashing ^.^

Is there certain settings that you would suggest for my laptop? (pSX I mean, seeing as ePSXe is very angry at Gutsy :P)

---

### Post by acoustibop on 2007-10-08
Certainly, the only things you need in a Feisty (or Edgy) install to run pSX successfully, tcoffeep, are libgtkglext1 and 3D acceleration for your videocard, a working soundcard and a working Playstation BIOS.  I would expect the same to be true for Gutsy.  Certainly your specs look to be more than enough.  What's the output of fglrxinfo if you're running one of the fglrx drivers, or glxinfo if you're running the default free driver?

Yes, PCSX seems always to have been the only one in the repositories.  However, that shouldn't really matter, since all you have to do to install any of them is decompress them into a folder.  ePSXe and PCSX will need plugins as well, but pSX should be good to go if you've satisfied the requirements above.

---

### Post by DoktorSeven on 2007-10-08
> **acoustibop said:**
> A P4 and it won't run pSX perfectly?  You've got to be kidding, DoktorSeven!.

Nope, no kidding here.  pSX has been nothing but slow and problematic every single time I've used it, both in Linux and Windows.  I am all for alternatives for everything, and was happy pSX produced a Linux version, and really wanted to like it, therefore I'm not trolling here.  I really wanted pSX to be good because it's easy to configure.

But ePSXe has blown it out of the water in every single instance, with every single game I've tried.  Compatibility is about the same between both in my experience, so I've really found no reason to even use pSX because of the terrible speed issues I've had with it.

I have no idea why no one else has the same issues.

---

### Post by dfreer on 2007-10-08
pSX works fine in AMD64 Gutsy BTW, which pretty much means that it will work in regular 32-bit as well. Just to let you know it's not a problem with Gutsy.

> Nope, no kidding here. pSX has been nothing but slow and problematic every single time I've used it, both in Linux and Windows. I am all for alternatives for everything, and was happy pSX produced a Linux version, and really wanted to like it, therefore I'm not trolling here. I really wanted pSX to be good because it's easy to configure.

Not to start a pSX vs. ePSXe flamewar, but I am surprised that pSX runs slow for you as well. My parents have P4 2.0 Ghz with some onboard Intel video chip, and it had problems running ePSXe in windows (low fps), whereas pSX runs just fine for me. As for OP, there isn't much to configure graphics-wise on pSX. I'm assuming your ATI video card is setup correctly?

---

### Post by FranMichaels on 2007-10-08
I'm on a laptop, with Gutsy, using pcsx from the repositories, and it works with my psx controller (through a usb adapter from radio shack). 

Here are my settings, and a little screen cap of the beginning of SOTN (which is the end of Chi no Rondo ;) )

:KS

P.S. Sorry I can comment on the other emulators, besides pcsx, the last playstation emulator I used was Bleem! (anyone remember it? :lolflag:)

---

### Post by acoustibop on 2007-10-09
Yes, Bleem! was the first Playstation controller I ever used, and I actually purchased a legal copy.  They never produced a Linux version, though - makes you wonder what Bleem! and Connectix VGS would have been doing now if Sony hadn't put them out of business...?

---

### Post by DoktorSeven on 2007-10-09
> **dfreer said:**
>  I'm assuming your ATI video card is setup correctly?

I use nvidia, and it's set up correctly.  I don't know.  As I said, I have no idea why pSX performs so poorly for me.

Edit: Oh, and fullscreen cuts off the bottom and right sides of the screen regardless of aspect correction setting.  Only on pSX, if you think I'm misconfigured somehow (and I play lots of games in Linux).

---

### Post by dfreer on 2007-10-09
I was actually referring to the OP's card, just to make sure that it wasn't a case of 3D acceleration not working. At least ePSXe works for you, perhaps you could file a bug report for your problems with pSX DokterSeven.

@tcoffeep - So your card is setup correctly, yeah? Other 3D games work fine?

---

### Post by tcoffeep on 2007-10-09
I can use OpenArena, if that's worth mentioning...

---

### Post by tcoffeep on 2007-10-09
The entire reason I'm in need of an emulator is that my controllers are all busted up, and back in my Windows days, I was able to use my keyboard...pSX doesn't seem to respond to my keyboard, nor does PCXS, and I swear, ePSXe hates me. ^.^

---

### Post by vlo on 2007-10-09
> **zmb0386 said:**
> I have the same problem, when I try and run epsxe absolutely nothing happens.  No text or anything from the terminal.

It was working on Gutsy until very recently, and then (like compiz, around the same time) it broke for me.  The perils of using the development version, I suppose.

I too have the same problem. No terminal output whatsoever. I've been able to run ePSXe (1.6.0)  in Dapper, Edgy and Feisty without problems.

I am running on a 64-bit Gutsy system, with all the 32-bit libraries that ePSXe requires installed.

Does anyone have clue what might cause this?

---

### Post by tcoffeep on 2007-10-09
I wish I knew. Have the people who were making ePSXe stopped working on it? We haven't seen an update since '03. Anyone know which language it was written in? We could always find a group of people to work on an update of sorts...

---

### Post by acoustibop on 2007-10-09
@tcoffeep: this is, I think, the first time you've said anything about having to use your keyboard rather than a controller.

I don't know about ePSXe, but in pSX, you need to set 'Device' to 'None' and 'Type' to 'SCPH-1010: Normal pad' on the controller tab to use your keyboard as a controller.  Since a keyboard is a digital device (on/off switches), you won't be able to use it as an analog controller, obviously.  I've just tried setting up my keyboard as a controller and it works fine in Feisty - no reason it shouldn't work in Gutsy.

@vlo: if you want to try pSX instead (IMHO a much better Playstation emulator than ePSXe or PCSX), check the 'pSX for AMD64/i386' link in dfreer's sig for help and links to his own repository for installing it on a 64 bit system.

@DoktorSeven: I can't figure out here why your system won't run pSX more happily but, as dfreer says, why not post your problem in the [pSX forums]("http://psxemulator.proboards54.com/index.cgi")?  That's where all the pSX people are... ;)

---

### Post by tcoffeep on 2007-10-09
In all honesty, I didn't know it was possible to use a psx controller until today. Haha.

---

### Post by tcoffeep on 2007-10-10
Great news!

It seems that in Gutsy, v1.13 of pSX doesn't respond very well (at least on my machine), but v1.12 responds perfectly. I just finished playing some FFIX and it ran smooth as ePSXe did for me on a Windows comp. My thanks to acoustibop and dfreer!

---

### Post by dfreer on 2007-10-10
Interesting to know, and glad it works for you!

---

### Post by acoustibop on 2007-10-10
Indeed, interesting, tcoffeep, and I wonder why v1.13 doesn't work so well in Gutsy?

Here's the changes from v1.12 to v1.13:

> Changes in this release:


    * Added Korean, Bosnian, Serbian and Icelandic translations
    * Added some missing translations to Linux build
    * Debugger DMA capture buffer now autoresizes
    * Fixed streaming music in Jikkyou Oshaberi Parodius
    * Fixed bug when setting sound frequency in Windows
    * Implemented volume and mute in Linux
    * Fixed "missing body parts" bug in Deception 3
    * Fixed bug that caused XA audio in Deception 3 to not stop correctly
    * Fixed random crash in Road Rash: Jailbreak
    * Fixed debugger crash when emulator is reading from CD
    * Fixed hang opening CD images in Linux
    * Per-user settings for Linux (.ini file is now stored in ~/.pSX)
    * Removed SSE instructions used during init (should fix crash on AMD CPUs)
    * Fixed GTK warnings when clicking window close button in Linux


Please note that the Linux version now stores its settings in ~/.pSX although it will read psx.ini from the same directory as the .exe if it exists.

Perhaps you should post this in the [pSX forums]("http://psxemulator.proboards54.com/index.cgi"): if new versions of pSX are going to have a problem with the next version of what's probably the most widely used Linux distribution, this needs looking at.

---

### Post by NightCrawler03X on 2007-10-21
The reason pSXfin is slower than ePSXe is because:

pSX uses the CPU to render graphics, then sends the images to the GPU and the GPU just draws them to the screen.
So the advantage is that you don't have to have a particularly good graphics card, or even 3D support for that matter, but the disadvantage is that you then need a faster CPU than is required for ePSXe. For pSXfin I would recomend about a 1 ghz CPU or faster, a graphics card that would have been decent 6 years ago, and a decent SPU (SPU isn't rendered by CPU with pSXfin, it is done with the sound card).

ePSXe on the other hand, renders graphic with the GPU, and sound with the SPU, so less weight is put on the CPU, Everything is evenly spread out. For ePSXe, I would recomend a 500mhz CPU or higher, and GeForce 2 Nvidia card or higher/equivalent, and a decent soundcard that is about 5 years old or younger.


But then most people now days will have a CPU 1 ghz or faster, so what they hey, use pSXfin.

---

### Post by acoustibop on 2007-10-21
psxfin.exe is the Windows executable, NightCrawler03X.  The Linux executable is just called pSX and the emulator is pSX Emulator. ;)

Actually, most people with a CPU running at 1GHz or less aren't likely to have a videocard that will take much load off the CPU.  I've pointed out before now that ePSXe might run better than pSX on a slow CPU with a videocard that _will_ take an appreciable load off the CPU - but this isn't usually likely to be the case.

pSX often won't run faster than ePSXe because it's meant to run games at the correct speed and no faster, while ePSXe can be speeded up; however, on slower machines where neither will run at full speed, pSX is usually the faster.  Also, pSX usually runs games without slowdowns, while ePSXe, even when it runs games at full speed, is much more likely to slow down at points.

And pSX _does_ require a 3D capable videocard.

---

### Post by @vijay@ on 2007-10-21
i was able to run epsxe 
after compiling and installing vanilla 2.6.23 kernel , i have done this to fix some network problems
and install dependencies
sudo apt-get install libglib1.2 libgtk1.2 libgtk1.2-common

but the problem is i was unable to see the text on epsxe 
here is a screenshot

---

### Post by @vijay@ on 2007-10-21
plz help me out; epsxe is better than psx and pcsx:guitar:
psx works but i cant play two player in tekken3:mad:
pcsx freezes and doesnot work:(

---

### Post by dfreer on 2007-10-21
@vijay@ - Try running this command on epsxe, like so:
```
ldd ./epsxe
```
and post it here.
I'm guessing you are missing a shared library, although I'm not for sure.

---

### Post by Mike'sHardLinux on 2007-10-21
```

ldd ./epsxe
not a dynamic executable

```

> **dfreer said:**
> @vijay@ - Try running this command on epsxe, like so:
```
ldd ./epsxe
```
and post it here.
I'm guessing you are missing a shared library, although I'm not for sure.

---

### Post by @vijay@ on 2007-10-21
> **dfreer said:**
> @vijay@ - Try running this command on epsxe, like so:
```
ldd ./epsxe
```
and post it here.
I'm guessing you are missing a shared library, although I'm not for sure.

i got the same thing

vijay@vijay-desktop:~/Desktop/ePSXe$ ldd ./epsxe
        not a dynamic executable

---

### Post by dfreer on 2007-10-21
Hmmm, I guess that means it doesn't use shared libraries... eh, just trying to troubleshoot.

---

### Post by mekura on 2007-10-26
There's a discussion [_here_]("http://ubuntuforums.org/showthread.php?t=95835&page=18") about a resolution to the library problem that might be of interest to some of you.

---

