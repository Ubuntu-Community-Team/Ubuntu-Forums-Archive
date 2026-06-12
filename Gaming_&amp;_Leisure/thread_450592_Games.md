---
title: "Games"
date: 2007-05-21
forum: Gaming &amp; Leisure
---

### Post by burt_57 on 2007-05-21
Here goes:
I use to play 3 games I played often in Windows.
Max Payne
GodFather
Mafia
Now it would be nice if I could make these game work in Ubuntu , then I would 
not have to go to Windows Xp ever.
There must be some very smart people out their who know how or are trying
to make it possible.
All else work, I can print, scan, play and rip music, email work, and Internet connection is just dandy.

Burt

---

### Post by earobinson on 2007-05-21
We have a gaming section for this kind of think. I have messaged the mods and asked them to move it.

---

### Post by lazyart on 2007-05-21
You can try wine but you might find that you'll need to dual boot to continue to play them.

---

### Post by Nekiruhs on 2007-05-21
Have you tried using Wine?
1) Install wine
 ```
sudo apt-get install wine
```2) Run executable
```
wine /media/cdrom/PATH/TO/EXE
```That might do it. To see if your app is compatible go to [winehq.org]("http://appdb.winehq.org/").
It seems Max Payne works VERY WELL under wine. It got a platinum rating
Unfortunately GodFather probably wont work, it got a garbage rating under wine.
Mafia should work if you install it in Windows and then copy it over to your wine directory (~/.wine/drive_c) and run it from there. It got a gold rating.
[edit]Darn, too slow, i had to do research though...[/edit]

---

### Post by burt_57 on 2007-05-21
I have ubuntu 64bit AMD
Now will wine work ?
I am not afraid to try anything ;)

---

### Post by houstonbofh on 2007-05-21
[http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)

It should give you a 32bit emulated enviorment, and work the same as a 32bit instal.  But will the games work, is the question...

---

### Post by hikaricore on 2007-05-21
64bit builds for Feisty here:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

^_^

Good luck.

Check the wine application database for info on how your titles run:  [http://appdb.winehq.org](http://appdb.winehq.org)

---

### Post by burt_57 on 2007-05-21
> **hikaricore said:**
> 64bit builds for Feisty here:

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

^_^

Good luck.

Check the wine application database for info on how your titles run:  [http://appdb.winehq.org](http://appdb.winehq.org)

Thank it is install fine no problem.
Now how do I run this emuator?
I know Max Payne should work so is Mafia according to the site you suggested.  :)

---

### Post by hikaricore on 2007-05-21
This might be some helpful reading:

[http://help.ubuntu.com/community/Wine#head-3acca7686806077923c05fa38c442e856ffacc54](http://help.ubuntu.com/community/Wine#head-3acca7686806077923c05fa38c442e856ffacc54)
[http://wiki.winehq.org/FAQ#head-7cc34974c2205854cd92c0afbe0a84e102f58abd](http://wiki.winehq.org/FAQ#head-7cc34974c2205854cd92c0afbe0a84e102f58abd)

---

### Post by burt_57 on 2007-05-21
> **hikaricore said:**
> This might be some helpful reading:

[http://help.ubuntu.com/community/Wine#head-3acca7686806077923c05fa38c442e856ffacc54](http://help.ubuntu.com/community/Wine#head-3acca7686806077923c05fa38c442e856ffacc54)
[http://wiki.winehq.org/FAQ#head-7cc34974c2205854cd92c0afbe0a84e102f58abd](http://wiki.winehq.org/FAQ#head-7cc34974c2205854cd92c0afbe0a84e102f58abd)

Oh man oh man I will never sleep tonight so much info.
But I must say it is good to have people like you help newbies like me .
I will get it with a little help from my friends ;)

---

### Post by hikaricore on 2007-05-22
> **burt_57 said:**
> I will get it with a little help from my friends ;)

*cue Wonder Years intro*


:p

---

### Post by burt_57 on 2007-05-22
Error I get when I try to Ron Max PAyne 

2\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135

---

### Post by kanapee on 2007-05-22
It seems like the games copy-protection won't work with wine, so you will probably have to get a No-Cd crack... PM me if you need more info, as I am not sure wether such cracks are legal or not.

*Edit: From Wikipedia, on No-Cd cracks:> This act is a form of software cracking. No-CD cracks can be found on the Internet from various reverse engineering websites or file sharing networks. No-CD cracks have legal uses, such as creating backups of legally owned software (a user right by law in many countries) or avoiding the inconvenience of placing a CD-ROM in the drive every time the software is being used, although this might be used likewise to circumvent software laws by downloading and executing full versions of non legally owned applications.*

---

### Post by burt_57 on 2007-05-23
> **hikaricore said:**
> This might be some helpful reading:

[http://help.ubuntu.com/community/Wine#head-3acca7686806077923c05fa38c442e856ffacc54](http://help.ubuntu.com/community/Wine#head-3acca7686806077923c05fa38c442e856ffacc54)
[http://wiki.winehq.org/FAQ#head-7cc34974c2205854cd92c0afbe0a84e102f58abd](http://wiki.winehq.org/FAQ#head-7cc34974c2205854cd92c0afbe0a84e102f58abd)

Ok maybe it is because I am so new at this , but nothing work.
Read the info.... ect.
Max payne does install but when I press play a window come up for
about 1/2 second saying starting install shield wizard and it poof it is gone.
No game nothing.
I have check winefile and see the directory that it has created.
I even double clicked on the exe. But same problem.
Without game I have to keep Windows grrrrrrrrrrr.

---

### Post by adam0509 on 2007-05-23
check [http://liflg.org/?catid=7](http://liflg.org/?catid=7) , they have good installer. You'll need to change the script of maxpayne in the first line from "!bin/sh to !bin/bash

Needless to say that you will need a wine correctly installed to use Loki installer...


Thus, 64 bit is really f*ck*d up for hundreds of things, and games are in the thing, I don't know if the Loki installers works for 64 bit version...

---

### Post by burt_57 on 2007-05-24
> **adam0509 said:**
> check [http://liflg.org/?catid=7](http://liflg.org/?catid=7) , they have good installer. You'll need to change the script of maxpayne in the first line from "!bin/sh to !bin/bash

Needless to say that you will need a wine correctly installed to use Loki installer...


Thus, 64 bit is really f*ck*d up for hundreds of things, and games are in the thing, I don't know if the Loki installers works for 64 bit version...

You know I am new user for all this.... I just can not run or install what you have 
suggested ...and darn it I will win some how with help :D.
Editor ? how to run that?
Wine is working fine now
Do you think I should install the the other version of Ubuntu... I have it.

---

### Post by adam0509 on 2007-05-24
For beginners, 32bit version is a lot better.

Even for pro...

In fact, I think 64bit version will be good in a year (when flash,wine and w64codecs and other programs will fully support 64bits...)

---

### Post by burt_57 on 2007-05-24
> **adam0509 said:**
> For beginners, 32bit version is a lot better.

Even for pro...

In fact, I think 64bit version will be good in a year (when flash,wine and w64codecs and other programs will fully support 64bits...)

I have removed the amd64.
Now with /i386
let see if I can get that Max Payne going now.
must mention that my screen look much better ,it is like 
I had it in windows. :)

---

