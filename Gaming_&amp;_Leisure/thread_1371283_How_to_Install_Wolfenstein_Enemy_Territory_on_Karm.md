---
title: "How to Install Wolfenstein Enemy Territory on Karmic Koala"
date: 2010-01-03
forum: Gaming &amp; Leisure
---

### Post by Unholii on 2010-01-03
How do i install Wolfenstein Enemy Territory on Karmic?

I've tried to search on google for help, but i can't find any. I have problems with installing libgtk1.2. Every tutorial says that i have to install libgtk1.2 by doing this in console
```

sudo apt-get install libgtk1.2

```

But all i get is this:

```

mika@mika-desktop:~$ sudo apt-get install libgtk1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgtk1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgtk1.2 has no installation candidate
mika@mika-desktop:~$ 

```

---

### Post by Perfect Storm on 2010-01-03
libgtk1.2 is obsolite and not maintained anymore and therefore not part in further releases of Ubuntu. However you can grab it here; 

[http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=jaunty&section=all)

---

### Post by Unholii on 2010-01-03
> **Artificial Intelligence said:**
> libgtk1.2 is obsolite and not maintained anymore and therefore not part in further releases of Ubuntu. However you can grab it here; 

[http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=libgtk1.2&searchon=names&suite=jaunty&section=all)

I tried to install, but this happens:

```

status: Error: Dependency is not satisfiable: libglib1.2ldbl (>= 1.2.10-18)

```

---

### Post by Perfect Storm on 2010-01-03
If you check the dependency list of libgtk1.2 on the site, you'll see where to get'em ;)

---

### Post by Unholii on 2010-01-03
> **Artificial Intelligence said:**
> If you check the dependency list of libgtk1.2 on the site, you'll see where to get'em ;)
Thanks :D I'm  not so good at english as u can see.

There should be tutorial for ET on Karmic ;)

Well gonna watch Forrest Gump now :popcorn:

Thanks REALLY really much. :)

---

### Post by Perfect Storm on 2010-01-03
There's one for 64-bit: [http://gwos.org/doku.php/guides:64bit:et_wolfenstein](http://gwos.org/doku.php/guides:64bit:et_wolfenstein)

---

### Post by MindFusion on 2010-01-03
Also, i have a small question, i keep getting kicked on wolfenstein ET (at random points, sometimes i can play an hour sometimes only half a minute) for violating the game's integrity:

```
Violation game integrity 20004
```

I've tried disabling punkbuster, but then i can't join nearly any server.. Also i found an older topic about this but i was completely confused by ti since i'm a coding noob.

---

### Post by Syndri on 2010-01-03
easy as this :)
scroll down to it and click install
it does it all for you with one click


[http://www.playdeb.net/updates/Ubuntu/9.04/?category=FPS](http://www.playdeb.net/updates/Ubuntu/9.04/?category=FPS)

---

### Post by Unholii on 2010-01-03
> **MindFusion said:**
> Also, i have a small question, i keep getting kicked on wolfenstein ET (at random points, sometimes i can play an hour sometimes only half a minute) for violating the game's integrity:

```
Violation game integrity 20004
```I've tried disabling punkbuster, but then i can't join nearly any server.. Also i found an older topic about this but i was completely confused by ti since i'm a coding noob.

MindFusion. PB does NOT support linux systems. 

[quote=http://www.pbbans.com/forums/index.php?showtopic=15762]
Hi there.I would like to know,if there is an detailed PB violation code list.I mean this #800000 numbers.
I already found this:
[I]Evenbalance supplied these codes concerning Punkbuster. So their is no gray area, anything above 50000 is consider a cheat and the player is attempting to gain an unfair advantage, period...

Technical Violations : (Resolution: Reinstall PunkBuster from the latest game update patch)
#101 - Communication Failure
#102 - Communication Failure
#131 - Initialization Failure
#132 - Protocol Error
#141 - Distress (This indicates a problem trying to update to the latest version of PunkBuster - it may indicate a problem reaching one of our Internet-based Master PB Servers which can be caused by firewalls, router problems, etc.)

Miscellaneous Violations :#111 - Bad Name (Resolution: Change player name or play on a different server)
#112 - Too Many Bad Names
#113 - Too Many Name Changes (Designed to eliminate name change spamming)
#114 - Protected Name (Resolution: Change player name or play on a different server)
#121 - Negative Score Too Low (usually from Killing Teammates)
#151 - Extended ASCII Characters in Player Name (Resolution: use regular letters, numbers and symbols in the player name or play on a different server)
#9001 - CVAR value failed range check (see the FAQ for more info)

[COLOR=Red]**Integrity Violations :When PunkBuster is unable to verify that a player's gaming environment is functioning properly and/or has not been alterred, an Integrity violation is raised. This also involves the detection of modified game or PunkBuster files. These violation numbers are between 10000 and 29999.**[/COLOR]

Cheat/Hack Violations :When PunkBuster detects a cheat or hack by repeated positive identification on a player's computer, a violation is raised. These violation numbers are 50000 and higher. Families of cheats are listed below. Resolution: Remove cheats and hacks from the computer.
#50000s - Aimbot
#60000s - Wallhack
#70000s - Multihack
#80000s - Gamehack - This includes editing memory locations and crosshairs
#90000s - 'Cheat' Video Drivers
#100000s - Speedhack
#110000s - Autofire
#120000s - Game Hook
#130000s - Attempted PunkBuster Hack[/I]

But i wanna know if there is something more detailed,like when i find in logs somethink like #60010,what does it exactly mean?

Thanks for any usefull answer  :rolleyes:                                                  
[/quote]

---

### Post by MindFusion on 2010-01-03
Then ... how come wolfenstein ET is listed on all Ubuntu gaming sites ? Wth...

---

### Post by Unholii on 2010-01-03
> **MindFusion said:**
> Then ... how come wolfenstein ET is listed on all Ubuntu gaming sites ? Wth...
Basically, PB supports ET, but never updates it. That's why it can kick for stupid reasons etc. U may check that list on my previous list for ur violation..

Usefull links:
[http://evenbalance.com/index.php?page=support-et.php](http://evenbalance.com/index.php?page=support-et.php)
[http://evenbalance.com/index.php?page=pbsetup.php](http://evenbalance.com/index.php?page=pbsetup.php)

---

### Post by MindFusion on 2010-01-03
Err, when i choose download i just get a page full of code... hm

---

### Post by Unholii on 2010-01-03
> **MindFusion said:**
> Err, when i choose download i just get a page full of code... hm
What exactly u were trying to download? I tried pbsetup, and it normally  downloaded .zip file.

_*Btw i have problems with editing et and etded files. It says that i dont have permission to do that : <*_ [SOLVED]

---

### Post by MindFusion on 2010-01-03
Okay can someone tell us what do :p ?

---

### Post by Perfect Storm on 2010-01-03
right click "save as" usually do the trick on a link.

---

### Post by MindFusion on 2010-01-03
Tell us what to do as in: please make a (chrono)logical text in which you tell us what to do step by step.

---

### Post by Tayl on 2010-01-05
> **Unholii said:**
> I tried to install, but this happens:

```

status: Error: Dependency is not satisfiable: libglib1.2ldbl (>= 1.2.10-18)

```

Sorry, how do you get around this? 

> **Artificial Intelligence said:**
> If you check the dependency list of libgtk1.2 on the site, you'll see where to get'em ;)

I didn't quite understand where to go with that? I'm a MEGA beginner so if it isn't spelled out for me in huge letters, I get completely dumb founded lol.

I downloaded the file from the bottom of the page: [http://packages.ubuntu.com/jaunty/libgtk1.2](http://packages.ubuntu.com/jaunty/libgtk1.2) but get that error in the message I quoted #1. What or how do you check the dependency list of libgtk1.2? Sorry for my incompetence. Does that mean I need to install everything under 'Other Packages Related to libgtk1.2'?

Tayl.

**:: Edit ::**

Played about a bit with files and what not, done a bit of searching online and found that if you install 'libgtk1.2-common_1.2.10-18.1build2_all.deb' first, then 'libglib1.2ldbl_1.2.10-19build1_i386.deb' you can then run and install 'libgtk1.2_1.2.10-18.1build2_i386.deb' fine. After that, you can then run the game install file.

**:: 2nd Edit ::**

Right, I got the game installed but now it won't play with any sound. I've attempted to use the [http://nullkey.ath.cx/~stuff/et-sdl-sound/](http://nullkey.ath.cx/~stuff/et-sdl-sound/) but I still can't seem to get the sound working. Any suggestions?

Tayl.

---

### Post by Perfect Storm on 2010-01-06
[http://ubuntuforums.org/showthread.php?t=1309656](http://ubuntuforums.org/showthread.php?t=1309656)

---

