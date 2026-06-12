---
title: "Linux compatible games"
date: 2007-11-12
forum: Gaming &amp; Leisure
---

### Post by Dapman01 on 2007-11-12
I was wondering what are some of the linux compatible games that do not require wine.  
I know Quake 4, Doom 3, UT2004/3 will work, but what else
Does FEAR work very well
I'll also accept games that work exceptionally well in wine

---

### Post by FG123 on 2007-11-12
FEAR doesn't work because there's no native Linux version of it.

Neverwinter Nights has a native build, that works well. Enemy Territory (the original as well as Quake Wars), they work natively in Linux. There's also other free games like Urban Terror, which I'd say comes close to commerical grade anyway.

---

### Post by Vitamin-Carrot on 2007-11-12
We are waitinf for EVE and X3 aswell
ANd have wrod that Valve/Seirra have hired linux guru's for poossible ports of the HL series.

---

### Post by Dapman01 on 2007-11-12
> **FG123 said:**
> FEAR doesn't work because there's no native Linux version of it.

Neverwinter Nights has a native build, that works well. Enemy Territory (the original as well as Quake Wars), they work natively in Linux. There's also other free games like Urban Terror, which I'd say comes close to commerical grade anyway.

Does fear work very well under wine?
Where do i find Urban Terror

---

### Post by FG123 on 2007-11-12
> **Dapman01 said:**
> Does fear work very well under wine?
Where do i find Urban Terror
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2878](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2878)
Summary: FEAR is too much for WINE, mainly due to .NET.

[http://www.urbanterror.net/](http://www.urbanterror.net/)

---

### Post by Scaly on 2009-03-22
> **Dapman01 said:**
> I was wondering what are some of the linux compatible games that do not require wine.  
I know Quake 4, Doom 3, UT2004/3 will work, but what else
Does FEAR work very well
I'll also accept games that work exceptionally well in wine
Try using PlayOnLinux. It will give you a whole list of games that are compatible. It even has patches for some, enabling you to play the game without the CD. You can also find patches for these games by going directly to the manufacture website of that game. For example [http://www.2kgames.com](http://www.2kgames.com)   Here's the terminal command directly from [www.playonlinux.com](www.playonlinux.com) for installing PlayOnLinux in the Terminal. You won't find it in Add/Remove, Synaptic, or Adept, so it has to be done in Terminal.


For Ubuntu(or Ubuntu based servers such as Kubuntu) copy and paste this command:
sudo wget [http://deb.mulx.net/playonlinux_hardy.list](http://deb.mulx.net/playonlinux_hardy.list) -O /etc/apt/sources.list.d/playonlinux.list
wget -q [http://deb.mulx.net/pol.gpg](http://deb.mulx.net/pol.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install playonlinux


If your using a different server, just goto the website for the other commands. I hope this was helpful, and sorry for it being so LONG. ;)

---

