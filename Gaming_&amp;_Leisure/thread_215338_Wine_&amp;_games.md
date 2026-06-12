---
title: "Wine &amp; games"
date: 2006-07-13
forum: Gaming &amp; Leisure
---

### Post by Ob1 on 2006-07-13
are they fast enough on wine? i've heard some complaints from Linux users with quite powerful macines complaining that old games like StarCraft don't even function normally under Wine.

---

### Post by vem0m on 2006-07-13
Starcraft works fine i run it myself now some games do some don't if they don't then try cedega if that don't work well then ur out of luck but that is how it is some games work some don't bottom line its an emu

---

### Post by shinkaide on 2006-07-13
It may vary from installation to installation. You should try it yourself, to see how it goes on your box. If it runs a little slow, you might need to tweak a few settings here and there (check the winehq app pages and [getting page help]("http://www.winehq.com/site/getting_help") for additional information). ;)

---

### Post by Orunitia on 2006-07-14
> **vem0m said:**
> Starcraft works fine i run it myself now some games do some don't if they don't then try cedega if that don't work well then ur out of luck but that is how it is some games work some don't bottom line its an emu

Comma and period, please use them, I had a hell of a hard time reading that.

---

### Post by vem0m on 2006-07-14
sorry bout that, i get carried away trying to type fast to get back to work lol

---

### Post by Polygon on 2006-07-14
i actually just got starcraft to work in wine, its just that most games you have to run in windowed mode or else it screws up your applets/bars and the game kinda gets screwed up.

i can also get steam running.... just not any games though... lol

---

### Post by handy on 2006-07-14
**W**ine **I**s **N**ot an **E**mulator.  Games can run on Wine as fast & sometimes faster than on windoze.

Wine has reverse engineered & is in the perpetual process of doing same, of the API's required to duplicate the windoze system environement called for by app's & games programmed to run on windoze.

When anyone gives Wine or Cedega or Crossover shit!  Just remember what they are doing.  They are making softwares written for a VERY different operating system, run on Linux!!!

More power to them! :KS

---

### Post by billT on 2006-07-14
> **handy said:**
> **W**ine **I**s **N**ot an **E**mulator.  Games can run on Wine as fast & sometimes **faster** than on windoze.

Wine has reverse engineered & is in the perpetual process of doing same, of the API's required to duplicate the windoze system environement called for by app's & games programmed to run on windoze.

When anyone gives Wine or Cedega or Crossover shit!  Just remember what they are doing.  They are making softwares written for a VERY different operating system, run on Linux!!!

More power to them! :KS

Indeed. OOTP 2006 (Out of the Park Baseball) runs much faster under Wine than it did in Windows. However, Wine couldn't run the other two games I play regularly (Football Manager 2006 and Civ IV), so I installed those two with Cedega. I tried to install OOTP in Cedega as well so as to only have one program installed to game, but it wouldn't even launch the installer, so Wine it is for the time being.

---

### Post by vem0m on 2006-07-14
Cedega runs off of wine all it is is an Enhanced version of wine so some will work better on it then thu wine some will not but in the end its only a matter of testing

---

### Post by Ob1 on 2006-07-14
So what sort of modifications do i have perform with Wine so it runs games properly?

I got Broodwar to run under it, it's rather slow though

---

### Post by vem0m on 2006-07-14
type winecfg from the terminal and look around the settings also look over at [http://www.winehq.com/](http://www.winehq.com/) for more info and possiable fixes for some games good luck :)

---

### Post by YokoZar on 2006-07-15
> **vem0m said:**
> Cedega runs off of wine all it is is an Enhanced version of wine so some will work better on it then thu wine some will not but in the end its only a matter of testing
This is a misconception.  Cedega is not based off of Wine - it is based off of a *very* old version of Wine from before Wine had its license changed to the LGPL.  The two programs have been developed seperately - Wine openly, Cedega closed.  There are many apps that do not run in Cedega but run perfectly fine in Wine.

---

### Post by vem0m on 2006-07-15
see there u contradict urself old wine is still wine no matter how u look at it its still BASED off wine and truth be told they are very similar

---

### Post by nthdegree on 2006-07-15
WINE can run near enough any game cedega can.

Infact I have found a lot of games run nicer in WINE than in cedega,  cedega is not closed source development by the way.

The CVS version is called WineX as it includes everything except the proprietary parts and is 100% open and free, however TransGaming goes schizo if distros try to package the CVS version even though according to the licenses in theory it is free to distribute a CVS compiled version.  Cedega used to be called WineX before it got the more closed source features and WineX remains as the core of cedega, but essentially whatever you can do with WineX you should be able to do with WINE.

I haven't fully researched this but apparently WINE changed to LGPL because Cedega (and others) were not contributing back to WINE to help enhance the project so they made their software LGPL to put an end to having their work skanked off them and sold for profit with no benefit to WINE itself.

As far as optimising WINE for games goes:

If you use an NVidia graphics card I recommend grabbing the NVidia drivers off the NVidia site rather than using the packaged version if you intend to use WINE or Cedega, and when installing make sure the 32-bit compatibility libraries get installed.

I also recommend that under some games you use the system monitor and nice the WINE processes to 20 (Very Low Priority) and use OpenGL modes over Direct3D ones.

If a game refuses to work under WINE (or WineX) then best idea might be to create a VMWare Virtual Machine under VMWare Server and then install VMWare Player and make use of VMWare Player's experimental Direct3D support.  Server does not have support for it but Player and Workstation do,  Player is free just like Server now is!

---

### Post by handy on 2006-07-15
CVSCedega, is not the same as the commercial version of Cedega.  There is NO copy protection support in the CVS version.  Nor is there the sweet GUI: Point2Play, which by the way is becoming a lot more powerful & friendly as Cedega develops.

Don't get me wrong, I only use Cedega because I can not play Guild Wars on linux any other way.  As soon as I can play GW on Wine I will dump Cedega as quick as a flash!

I do agree with those that consider Cedega extortionware, due to the Transgaming marketing strategy, which = you keep on paying, every month, forever...

---

### Post by thunderduck3141 on 2006-07-15
cedega is terrible
transgaimg is a boil on the face of open source
all they want is your money, nothing more, they dont care if it runs or not, just if they have your money

---

### Post by rmjb on 2006-07-15
Can't you stop paying TransGaming and still use Cedega in the last state you had it??

- rmjb

---

### Post by vem0m on 2006-07-16
> **rmjb said:**
> Can't you stop paying TransGaming and still use Cedega in the last state you had it??

- rmjb

that is what i keep telling ppl to do i do it myself

---

### Post by handy on 2006-07-16
> **rmjb said:**
> Can't you stop paying TransGaming and still use Cedega in the last state you had it??

- rmjb

Yes, you can.  But I had to do a reinstall of Ubuntu, & was forced to resubscribe to Cedega, if I wanted to use it!!

Not happy about that, understandably.

Cedega is not an easy thing to backup, it has files all over the place, & there are a lot of them.

---

### Post by vem0m on 2006-07-16
no its not easy to back up those files but if u have the cedega small .deb package and an engine update package tha is really all u need u can get deps on ur own install the small package then upgrade its engine with the engine package :P

---

### Post by rmjb on 2006-07-16
> **vem0m said:**
> no its not easy to back up those files but if u have the cedega small .deb package and an engine update package tha is really all u need u can get deps on ur own install the small package then upgrade its engine with the engine package :P

Maybe you could do a mini HOWTO on this procedure?

- rmjb

---

### Post by vem0m on 2006-07-16
hmmmmmm well i might a lil later when i get time :)

---

### Post by handy on 2006-07-16
> **vem0m said:**
> no its not easy to back up those files but if u have the cedega small .deb package and an engine update package tha is really all u need u can get deps on ur own install the small package then upgrade its engine with the engine package :P

OK, so I need to download an "engine package" from Transgaming, & then I am covered for future installations of the OS?

---

### Post by vem0m on 2006-07-16
yes grab that and the install deb file weather small(that is what i have i d/l the deps myself) or u can get the big install package and the engine package and u will be set yes :)

---

### Post by handy on 2006-07-17
> **vem0m said:**
> yes grab that and the install deb file weather small(that is what i have i d/l the deps myself) or u can get the big install package and the engine package and u will be set yes :)

Great news, thanks very much... :KS

---

### Post by YokoZar on 2006-07-18
> **vem0m said:**
> see there u contradict urself old wine is still wine no matter how u look at it its still BASED off wine and truth be told they are very similar
Despite sharing similar roots, the two programs are so different now that it doesn't add much for understanding purposes to describe Cedega as "Wine-based" or "Wine with enhancements", since that same description fits new versions of Wine even better than it does Cedega.

---

