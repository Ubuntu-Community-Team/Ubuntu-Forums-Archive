---
title: "Need to speed things up"
date: 2009-04-20
forum: General Help
---

### Post by mark.giblin on 2009-04-20
I have just sacrificed a winXP system, to be frank, was faster and more responsive than this intrepid thing.

Currently sitting doing nothing the sysmonitor reports that 72% of resources are being eaten, all I have is a web browser running, same applies to using the firefox browser as well.

When no programs are running, it still consumes >25% of system resources.

The thing is very noticably slower than the LiveCD, even with the drive latency in the DVD Rom, it was faster than the installed version.

What do I need to do or how do I correct this?

I neglected to mention that it also has issues when trying to do more than one thing like play an MP3 and access a folder, the music stops. Same applies to the system opening or using a program.

---

### Post by kerry_s on 2009-04-20
let me consult my magic ball, hmm....hmm....
nope nothing, perhaps if you had actually told us something we could work with, you could get some help.

computer model?
specs?
anything?

just saying it's broke or slow means nothing.

---

### Post by lisati on 2009-04-20
Hmmm... The LiveCD is usually slower than with an installation on a hard disk. Insufficient swap space? Wonky RAM?

---

### Post by mark.giblin on 2009-04-20
The spec

Packard Bell (branded)
2.66 Ghz Pentium 4
256MB Ram PC2100
20 Gig HDD for its own use which it appears to have set aside 1.2Gigs for swap.
DVD-RW 16x
Nvidia Video card (ATI Radeon 7000)

No other operating system is installed.

Don't know what else to tell you, if knowing the colour scheme of my lounge helps, its a nice leaf green.

---

### Post by Elegia on 2009-04-20
The ram is definitely the bottleneck here. I assume you're using GNOME, which requires quite some memory to run smooth. Also, check if you have compiz enabled. That would slow down things too.

What you could also do is try installing a more light-weight desktop manager, like xfce and see if that works faster.

---

### Post by mark.giblin on 2009-04-20
I checked my specs and are within the quoted specs needed to run this Ubuntu.

As for other stuff, GNOME... wouldn't know where to begin looking. 

If this is command line stuff then I am stuck as I am new to Linux and wouldn't know where to start.

---

### Post by hesjnet on 2009-04-20
First of: Disable special effects
System --> Preferences --> Apperance
Choose the tab for Visual effects
Choose None.

Second: Disable memory consuming applications
System --> Preferences --> Sessions
Click on checkbox to de-activate
"Tracker"
"Tracker Applet"
This disables the indexing of files(for faster searching)

click Ctrl+Alt+Backspace to reload Gnome.

---

### Post by mikewhatever on 2009-04-20
You should post the output of **ps -aux** command to let us see what's consuming so much resources, also post the output of **free -m**.

---

### Post by kerry_s on 2009-04-20
> **mark.giblin said:**
> The spec

Packard Bell (branded)
2.66 Ghz Pentium 4
256MB Ram PC2100
20 Gig HDD for its own use which it appears to have set aside 1.2Gigs for swap.
DVD-RW 16x
Nvidia Video card (ATI Radeon 7000)

No other operating system is installed.

Don't know what else to tell you, if knowing the colour scheme of my lounge helps, its a nice leaf green.


thank you, like "Elegia" said it most likely the ram it's probably swapping like crazy.
you have a couple of options:
1) add more ram
2) trim gnome down
3) a lighter setup

for now, i'm going to go with gnome tips.
1) trim the running programs, System> Preferences> Sessions:
the first tab is start up options, uncheck those you don't need. log out and back in.
i built mine from a base install up, so i don't have much. see pic

2) turn off all the fancy stuff, System> Preferences> Appearance:
lose the background, pick the first 1 a choose your color. you can use a lighter theme, but it's pretty hard to tell the difference speed wise.

3) turn on reduced resource mode, Applications> System Tools> Configuration Editor:
click edit> find, type> reduced, check both boxes
after that search "animation" turn them all off

hmm, that's pretty much all i can think of right now.
make sure you google your vid card to get the best setting, example:
"linux Radeon 7000 setup"
open a terminal, Applications> Accessories> Terminal:
type> lspci
to get more info on your card, i been doing the same thing for my card, it's a crappy savage card ( S3 Inc. VT8375 [ProSavage8 KM266/KL266] ) runs like crap. ;) i got it at least usable for now.

anyways good luck to you, let us now if you want to go the other routes. :D

---

### Post by nawitus on 2009-04-20
Install Xfce, it should use less memory. Or seriously buy more ram, it's almost free nowadays..

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by mark.giblin on 2009-04-20
> **nawitus said:**
> Install Xfce, it should use less memory. Or seriously buy more ram, it's almost free nowadays..

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Hmmm, would be nice, certain parts of the world we still get stuffed with prices like £24.99 for 128mb of ram.



I have turned off allot of the stuff that TBH is not needed and the overall consumption has plumeted, now average of 18% when running a web browser.

[QUOTE=kerry_s]3) turn on reduced resource mode, Applications> System Tools> Configuration Editor:
click edit> find, type> reduced, check both boxes
after that search "animation" turn them all off[/QUOTE]

Sorry, nothing but KGRUB Editor under that menu.

This is the other anoying thing, the live CD contained a good array of tools that are not installed from the CD, you have to download them. My first Linux install ended up going from desktop to a commandline affair and I ended up installing again after I had downloaded half a gig of programs installed and then found myself looking at a commandline. So I had to go through the loop again to get here today.

So with that in mind, anyone know how I grab the installers or access them to back them up?

---

### Post by ushills on 2009-04-20
> **mark.giblin said:**
> Hmmm, would be nice, certain parts of the world we still get stuffed with prices like £24.99 for 128mb of ram.


Assuming you are in the UK, you can get memory far cheaper than that.

E.g, Kingston 1GB DDR 266MHz/PC2100 Memory CL2.5 Unbuffered Non-ECC for 37.07GBP from ebuyer

[http://www.ebuyer.com/product/38992](http://www.ebuyer.com/product/38992)

or 512MB for 16GBP

[http://www.ebuyer.com/product/26878](http://www.ebuyer.com/product/26878)

Gnome will not perform well with 256Mb although xubuntu will be okay.

---

### Post by LowSky on 2009-04-20
> **mark.giblin said:**
> The spec

Packard Bell (branded)
2.66 Ghz Pentium 4
256MB Ram PC2100
20 Gig HDD for its own use which it appears to have set aside 1.2Gigs for swap.
DVD-RW 16x
Nvidia Video card (ATI Radeon 7000)

No other operating system is installed.

Don't know what else to tell you, if knowing the colour scheme of my lounge helps, its a nice leaf green.

Nvidia does not make Radeon cards, they are tow competing companies
256 RAM is barely enough, 512 would be much better
The processor is fine



> **mark.giblin said:**
> I checked my specs and are within the quoted specs needed to run this Ubuntu.

As for other stuff, GNOME... wouldn't know where to begin looking. 

If this is command line stuff then I am stuck as I am new to Linux and wouldn't know where to start.


Here are the actual settings recommended, see link below
**Bare Minimum requirements**

It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation.

    * 300 MHz x86 processor
    * 64 MB of system memory (RAM)
    * At least 4 GB of disk space (for full installation and swap space)
    * VGA graphics card capable of 640x480 resolution
    * CD-ROM drive or network card 

[B]Recommended minimum requirements
[/B]
Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly.

    * 700 MHz x86 processor
    * 384 MB of system memory (RAM)
    * 8 GB of disk space
    * Graphics card capable of 1024x768 resolution
    * Sound card
    * A network or Internet connection 

Note: All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation


[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by kerry_s on 2009-04-20
> Sorry, nothing but KGRUB Editor under that menu.

so your not using gnome? kgrub is a kde program, kde is the heaviest of the 4 desktops.

1) lxde > the lightest desktop setup
2) xfce4 > medium
3) gnome > heavy
4) kde > heaviest

i suggest: open a terminal, type> sudo apt-get install lxde
log out> select lxde in the menu and log in.

---

### Post by mark.giblin on 2009-04-21
Well under system it says "About GNOME"

All software is installed through the package manager and if KGRUB is KDE, WTF is Ubuntu doing installing an App that is nothing to do with GNOME?

Theirs no indication to say that the app is tied to a particular GUI, if it is, why did GNOME list it in the package manager?

BTW, since turning off the effects, theirs been a vast improvement in performance. Not assessed the other issues I have been having with it so we shall see.

---

### Post by kerry_s on 2009-04-21
you can install any program and use it, you can even install different desktops or window managers.

a stock install is suppose to look something like this>

---

### Post by kerry_s on 2009-04-21
on my old laptop, 450mhz 256mb ram, i use a window manager called jwm, to keep things light.

---

### Post by mark.giblin on 2009-04-23
Thanks for all the help so far. Things are certainly faster without the "Enhancements" (Hmmm ok, if the devs say so)

---

### Post by go_beep_yourself on 2009-07-21
Blacklist modules you don't use like battery (if you aren't using a desktop) and bluetooth

Install sysv-rc-conf and edit the default run level two to disable services from running in the background that you really don't need or care for.

Or just get Puppy Linux. It looks amazing, and I know it's fast. I'm still waiting to try it.

gOS is a light weight ubuntu made by google.

---

### Post by cpressland on 2009-07-21
> **go_beep_yourself said:**
> gOS is a light weight ubuntu made by google.

No, it's not. It's based on Ubuntu, yes, but not made by Google.

It's called 'GoodOS' not 'GoogleOS' it's made by the Linux Community at Large just like everything else.

Any why're you resurrecting a topic that's not seen action since April?

---

