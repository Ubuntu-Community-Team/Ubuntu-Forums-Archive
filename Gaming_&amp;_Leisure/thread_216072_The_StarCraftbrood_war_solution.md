---
title: "The StarCraft/brood war solution"
date: 2006-07-14
forum: Gaming &amp; Leisure
---

### Post by Cyraxzz on 2006-07-14
Since this game is common among Linux Gamers, and problems are commonly encountered on it under Wine(usually a slow speed performance), I decided to post the solution for this problem.

type ```
Wine --version
```

Check if you have Wine version 0.9.15, because it runs perfectly under 0.9.15.

It's awfully slow on 0.9.16, and less slow on 0.9.17 but not at it's normal speed.

I have not found a deb. package for it yet, sourceforge has wine debs that are of the 0.9.12 version or older, and the official wine page has only the newest version(0.9.17) for wine.

So I generated a .deb package from a .rpm compiled package with the 0.9.15 version of wine, Which you can [download here.]("http://www.filefactory.com/?cba187")

```
 cd /home/username/yourfilelocation
sudo dpkg -i wine_0.9.15-2.1_i386.deb 
```

[COLOR="Red"]*Note:* Remember to remove your current verison of Wine, which is probably more new than the 0.9.15 version.[/COLOR]

----------------------------------------------------------------------------------

If your desktop Tabs are not in their original state after you have exit StarCraft in full-screen,

then run it windowed

type 
```
winecfg
```
Go to the Applications tab.
Press Add application...
Navigate to "Program Files\Starcraft\starcraft.exe"
Go to the Graphics tab.
Tick "Emulate a virtual desktop".

---

### Post by Cyraxzz on 2006-07-14
For increasing the StarCraft/broodwar Speed in the newest version of Wine(0.9.17)

Durring game play

press **F10 > Options > Video > Diable Unit Portraits**

This alteration should bring it back to it's normal speed.

---

### Post by vem0m on 2006-07-14
heh i use an old version 0.9.9 i think and its running fine :P

---

### Post by YokoZar on 2006-07-18
> **Cyraxzz said:**
> I have not found a deb. package for it yet, sourceforge has wine debs that are of the 0.9.12 version or older, and the official wine page has only the newest version(0.9.17) for wine.

So I generated a .deb package from a .rpm compiled package with the 0.9.15 version of wine, Which you can [download here.]("http://www.filefactory.com/?cba187")you don't need to do this anymore :)


You can now easily get old Wine packages by downloading them from the [WineHQ packages archive](http://wine.budgetdedicated.com/archive/index.html).  Just download the version you're looking for.

Now, if it truly is the case that your program works in an old version of Wine but not in the current version, then you have discovered what we call a *regression*.  Regressions are quite serious bugs, as if they go unreported apps can sometimes remain broken for *very* long amounts of time - Fallout 2, for instance, worked fine in 2002 and then became broken for over a year due to an unreported regression in Wine's Direct Input handling.

So, please, do us all a favor and [file a bug](http://bugs.winehq.org/) or send an email to the [wine-devel mailing list](http://winehq.org/site/forums) noting that you have found a "regression".

Anyway, I hope you can get it working again, and if you need help installing the old packages, just ask here.

---

### Post by patrick295767 on 2006-07-18
I run starcraft / broodwar with cedega / cvscedega. 
I like it better & it's faster than with wine.
   
Did you try  cedega / cvscedega for broodwar ?

 Greetz

---

### Post by vem0m on 2006-07-18
wine is much faster running SC/BW here it varies per person/per computer cedega lagged and stalled alot Retail version 5.2.1 while wine version 0.9.9 was runnign it flawlessly i have since upgraded to 0.9.17 and will retest it soon :)

---

