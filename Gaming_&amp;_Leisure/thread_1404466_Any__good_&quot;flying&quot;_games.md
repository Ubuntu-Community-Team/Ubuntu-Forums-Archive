---
title: "Any  good &quot;flying&quot; games"
date: 2010-02-11
forum: Gaming &amp; Leisure
---

### Post by Dragonbite on 2010-02-11
My son just re-found my old Microsoft joystick which I used to play an old "X-Wing vs Tie Fighter" flight simulator game. It was on a Windows 98 box before.

I was wondering, what are some good simulator-type games (space, aeronautical, etc.) available for Ubuntu Linux?

I don't have a great graphics card, or a lot of Ram (yet) so something low-powered would be fine.

I'm not sure how well "X-Wing vs Tie Fighter" would work in Linux, under Wine or as part of a VM, but since it is pretty low-end and ran on a system even weaker than my current one (which is weaker than the one I'm about to move to) I am kinda hopeful but would rather a "native" game.

---

### Post by Perfect Storm on 2010-02-11
You could try with [oolite](http://gwos.org/doku.php/games:alphabetical:o:oolite). It's more like Elite.

---

### Post by Chesnut on 2010-02-11
This is the best one there is for Ubuntu: [http://www.flightgear.org/](http://www.flightgear.org/)
You should be able to run it, it doesn't need a good PC.

---

### Post by Dragonbite on 2010-02-11
Both sound interesting.

Are either in the repositories or do I have to download myself?  If so, I hope they have .deb files.

---

### Post by ratcheer on 2010-02-11
My son has an awesome flying game, but it is on PS3.

Tim

---

### Post by Hwæt on 2010-02-11
gl-117 is pretty fun. You can find it in the repos.

---

### Post by Sockerdrickan on 2010-02-11
I am tempted at writing a little "flying game". I just need some motivation. I basically have an airplane ready. I was thinking about writing a really small game with only the executable and no external media. Sound would be generated on the fly with ALSA. A lot of shading effects. Like a small game demo.

---

### Post by PuddingKnife on 2010-02-11
theres a space flight game called vendetta online

---

### Post by ironclaw on 2010-02-11
The FreeSpace 2 Source Code Project is a very good open source space combat simulator with lots of single-player mods. I don't think it's in the repositories, but they have an install script that automatically downloads and installs everything.

---

### Post by Naegling23 on 2010-02-12
Hmmm, if I remember correctly, the old star wars space combat games are dos based... that would mean that they "should" run under dosbox.  If thats the case, you "might" have more luck playing them on linux than you do windows.

Wine tends to run older games rather well, I would imagine that xwing vs tie figher would be playable in linux either dosbox or wine....if thats the case, check out wine, and Good old Games, I would imagine they have some of the old star wars games, and wing commander series games which may work.

---

### Post by Naegling23 on 2010-02-12
Oh, and I know its not combat, but is the flight sim hack still present in google earth? that was a pretty neat feature. (sorry, I cant remember how to enable it).

---

### Post by Dougie187 on 2010-02-12
> **Dragonbite said:**
> Both sound interesting.

Are either in the repositories or do I have to download myself?  If so, I hope they have .deb files.

Just so you know. If you aren't sure if something is in a repo, you could open a terminal and type
```
apt-cache search *packagename*
```
Like here, you could use flightgear for the package and it would return this information.
```
apt-cache search flightgear
fgfs-base - Flight Gear Flight Simulator -- base files
flightgear - Flight Gear Flight Simulator
simgear-dev - Simulator Construction Gear -- development files
simgear1.9.1 - Simulator Construction Gear -- shared libraries
```

then you can see that flightgear is in fact the package name. You can also use more general terms like flight to see if it gives you any other packages that have something to do with flight.

You will get a lot of useless packages in that search, but it gives you an idea.

Then you can tell if something is in a repo. Hope that helps!

---

### Post by CharmyBee on 2010-02-12
> **Naegling23 said:**
> Hmmm, if I remember correctly, the old star wars space combat games are dos based... that would mean that they "should" run under dosbox.  If thats the case, you "might" have more luck playing them on linux than you do windows.
Xwing vs. Tie is for Windows, as is Xwing Alliance, and the "special" versions of X-Wing and Tie Fighter that add voice, SVGA and a digital soundtrack.

Only X-Wing and Tie Fighter are for DOS and they don't run good in DOSBox since it will have input issues.

---

### Post by Dragonbite on 2010-02-12
One thing I found funny is that the X-Wing vs Tie Fighter game stopped being supported by Windows 98.  Somebody did a hack to get it to run on Windows 2000 but after that.. kaput!

I tried it once before in Wine, specifying Windows 98 as the target system and it ran.. sort of.  It was so dogged slow it was practically unusable.  That is part of why I'm preferring Linux-native games over Windows ones.

I think that was on Ubuntu 8.04, so I don't know if Wine has made any significant improvements.  How is VirtualBox supposed to be with these types of games?

Oh, and for looking to see what is available, I did get to their sites (they timed out when I tried before which is why I asked, must have been something on my network).  I can also look them up at [http://packages.ubuntu.com]("http://packages.ubuntu.com") too.

Thanks for the advice!  Keep them coming!

It would be cool if Ubuntu did an "Ubuntu Gaming Edition", where it includes and makes as easy as possible the hardware (graphic card drivers, joystick, headset, controllers, etc.) and a ton of games in place of OpenOffice, Gimp, etc.  It can even come on a DVD or LiveDVD.

I think Fedora has a Gamers mix, or is working on one.

If something like this was easily transferable/installable/playable then wouldn't that help counter the stigma that "Linux is not for games"?

---

### Post by Perfect Storm on 2010-02-12
oolite package: [http://www.playdeb.net/updates/ubuntu/9.10/?q=oolite](http://www.playdeb.net/updates/ubuntu/9.10/?q=oolite)

---

