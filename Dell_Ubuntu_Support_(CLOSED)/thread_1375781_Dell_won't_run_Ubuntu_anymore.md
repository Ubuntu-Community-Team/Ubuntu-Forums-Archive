---
title: "Dell won't run Ubuntu anymore?"
date: 2010-01-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PartsMan on 2010-01-08
I had been running ubuntu 8.04 for a while and then Xubuntu 9.10 for a little while fine.
Then the other day i loaded a game and it locked up my system.

Here is the general thread I started thinking it was the game.
[http://ubuntuforums.org/showthread.php?t=1370092](http://ubuntuforums.org/showthread.php?t=1370092)

I have since formatted and tried many times and versions of Ubuntu and it won't work.
Seems to have a problem with X. (8.04, UNR9.10, X9.10 even Debris)
Sometimes they will run live in the lower grafics mode.

I am running XP on this machine just fine, but I have run linux long enough hate windows.

Some lighter distos will run fine but nothing from Ubuntu.(Tinycore, DSL, Slitaz, NimbleX, Kate all boot run live fine.

Any ideas or explanations.

---

### Post by ubumania on 2010-01-08
wrong thread

---

### Post by robbielink on 2010-01-09
I have a 2400 and had many problems from 8.10 on - intermittent. Sometimes it would run from the live CD, sometimes not. I had given up on 9.10, got 9.04 to run for while but then it started freezing up at random times and then more and more. Much searching through forum threads, launchpad bug reports (there are many similar reports but the details all vary). Some folks get results with one fix, others not. The one thing I did that made the most difference - go in BIOS - I'm not on the Dell right now so cant' remember the exact name but theres a "legacy" section - open that and raise the video memory to 8 meg - it's default is 1 and the only other option is 8. 
That cut way down on the freeze-ups and then I got curious to see if I could upgrade back to 9.10 so I tried that and apparently some recent bug fixes in the core made a difference, too, because for a week now I've been running 9.10 with no freezeups except for a few software related ones (MuseScore default settings which I changed, Google Earth freezes everything no matter what, and a couple of others but I'm sure I'll find tweaks eventually). The onboard Intel Video chip seems to be the biggest culprit but I suspect there are other things, too.

PS - make sure you disable Compiz!

---

### Post by ugm6hr on 2010-01-09
Hardware details?

---

### Post by robbielink on 2010-01-10
> **ugm6hr said:**
> Hardware details?

Don't know if you were asking the original poster or me but here's what I have:
Dell Dimension 2400

Ubuntu 9.10 (karmic) release.
GNOME: 2.28.1 (Ubuntu 2009-11-03)
Kernel version: 2.6.31-17-generic 

GenuineIntel, Intel(R) Pentium(R) 4 CPU 2.66GHz
Total memory: 993 MB
Total swap: 2933 MB

MOTHERBOARD
Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
		
GRAPHIC CARD
VGA controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

SOUND CARD
Creative Labs SB Live! EMU10k1 (rev 08)

NETWORK
Ethernet controller
Broadcom Corporation BCM4401 100Base-T (rev 01)

Modem
Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)

-----------------
As I stated earlier increasing the video memory in BIOS solved many of my problems - plus I think a kernel update also solved problems and I now have Karmic running just fine on this machine where it was impossible just a few weeks ago.

Yesterday I installed a different kernel because I needed a low-latency kernel for some audio work. I installed the linux-rt kernel 2.6.31.9.10 and before I could even completely log in with it the computer froze up again. This also makes me think that the 2.6.31-17 kernel has some fixes that make installing on older Dell machines possible. Just an uneducated guess....

---

### Post by PartsMan on 2010-01-11
Yes Dell 2400 but mine's the 2.2ghz P4 With 640mb ram.
Everything integrated.

I ran the thing on 8.04 for a year and now any decent sized Linux I try won't work.
Just knew that my board was fried until XP ran fine.

I have borrowed a different video card from the bone pile at work to try that tonight.

---

### Post by hero1900 on 2010-01-11
also i got so many problems regarding games (linux games) stuck inside cant get out and so on so i have to restart my laptop but not with all games but it is so annoying so for me ubuntu is not a good choice for games also sounds not working even with the new manager also got many problem with it i hope they can fix these things

---

### Post by PartsMan on 2010-01-12
I didn't get a chance to try the video card last night.:(

How much memory should I be sharing with the video now?
I have 32-256mb to choose from.

---

### Post by PartsMan on 2010-01-12
Tried other video card. Still would not work with Any Ubuntu.


Giving up for the semester.:(
I need this thing stable for school.

---

### Post by PartsMan on 2010-01-15
The card i tried was not supported.
I ordered a new one today.

---

### Post by PartsMan on 2010-01-22
That Dell can't hurt anybody anymore.8-)

---

