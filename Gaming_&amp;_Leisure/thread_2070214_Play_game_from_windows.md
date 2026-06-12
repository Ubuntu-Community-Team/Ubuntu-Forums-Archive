---
title: "Play game from windows"
date: 2012-10-12
forum: Gaming &amp; Leisure
---

### Post by deathyr on 2012-10-12
Hi, i have some games installed on windows and i want to play them on ubuntu directly from the windows folder (i mean, without installing them on ubuntu)
Is that possible?
I tried running pes 2010 with wine and in the attachments there is the log.
Thanks for helping :)

---

### Post by pompel9 on 2012-10-12
That is not possible. The main reason for this is that ubuntu can't use the exe files. And most games for windows uses directx, ubuntu does not have this.

There are two ways to play games designed for windows on ubuntu. The first one is wine (does work on some games), and the second one is using a VM. Using a VM is not possible, unless you have a powerful PC.

I would advice to dual-boot.

---

### Post by Bölvaður on 2012-10-12
It can be done!
But that is if you are familar with how the Windows operating system works and what it is doing when you are running your games, and/or know a bit about how WINE works, then you can do it.

If you are not familiar with windows you better just go to [http://appdb.winehq.org/](http://appdb.winehq.org/) search for the games you want to install to get information from others that have installed those games. The WINE subforum here on ubuntuforums is useful if you need to ask someone if you run into troubles.

You cannot expect to run any game at all in wine, and surely you will run into problems with badly programmed games. They might not run at all.

---

### Post by pompel9 on 2012-10-12
If I am not mistaken, he asked if he could play the games directly from the windows partition. That is not possible.

> **deathyr said:**
> **Hi, i have some games installed on windows and i  want to play them on ubuntu directly from the windows folder (i mean,  without installing them on ubuntu)**
Is that possible?
I tried running pes 2010 with wine and in the attachments there is the log.
Thanks for helping :smile:

---

### Post by mentorious on 2012-10-12
it depends.. probably part of apps and games can be playable, but you must replace the windows registry (copy it from "C" partition to ~/.drive_c/). I can guarante  nothing, but sometime I was able to launch "Football Manager" from windows partition, without installation this game in wine etc.

PES2010 can be installed normally in wine. I still play in this "2010" version since two years, works fine on Ubuntu 9.10, 10.10, 11.04, 12.04 ;) Check [winehq ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=18148")and [this video]("http://www.youtube.com/watch?v=XevwLxXPYWg"):

---

### Post by deathyr on 2012-10-13
> **pompel9 said:**
> If I am not mistaken, he asked if he could play the games directly from the windows partition. That is not possible.
Yes, that's the point.
>  		it depends.. probably part of apps and games can be playable, but you  must replace the windows registry (copy it from "C" partition to  ~/.drive_c/). I can guarante  nothing, but sometime I was able to launch  "Football Manager" from windows partition, without installation this  game in wine etc.
I'll try this :)
Thanks everybody

---

