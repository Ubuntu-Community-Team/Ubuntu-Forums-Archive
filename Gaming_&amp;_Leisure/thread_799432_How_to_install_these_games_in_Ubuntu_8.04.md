---
title: "How to install these games in Ubuntu 8.04?"
date: 2008-05-19
forum: Gaming &amp; Leisure
---

### Post by vjsimon on 2008-05-19
Hi guys,

I have been trying to install the following games in Ubuntu 8.04 but have had no luck. I am hoping someone could help me out.

1) Slam Soccer 2006
2) Eat the Whistle
3) FreeCol
4) Globulation 2
5) Savage
6) Yoda Soccer
7) Bos Wars
8) Bygfoot
9) Dark Oberon
10) Secret of Ultimate Legendary Fantasy Unleashed
11) 0 A.D.
12) Glest
13) isoccer
14) Open-football

Please help.

---

### Post by rockerphil on 2008-05-19
here's what i'd do, if it's an Ubuntu game i'd simply search the repository for the game and get the actual name of the package then just run this code

sudo apt-get install <packagename>

if it's a Windows game you'll have to run it through Wine, which can be pretty hit or miss. if you don't already have Wine installed then run this code

sudo apt-get install wine

then you'll have to download the .exe file for the game and then run it through wine to install it. once that's done you'll need to navigate to the directory that holds the Windows program file of your game and wine the main .exe file


also, here's the URL for the repository lists

[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by Canis familiaris on 2008-05-19
Use Add/Remove and Synaptic.
You can also try [CNR]("http://www.cnr.com")

---

### Post by Bakon Jarser on 2008-05-19
Have you searched synaptic for these?  I searched for the first four and eat the whistle (etw) and freecol were there.  See how many you can find there.

---

### Post by Sef on 2008-05-19
1) For gaming site info, check out this [list]("http://ubuntuforums.org/showthread.php?t=359842").

2) Moved to Gaming and Leisure.

---

### Post by atomkarinca on 2008-05-19
> **vjsimon said:**
> Hi guys,

I have been trying to install the following games in Ubuntu 8.04 but have had no luck. I am hoping someone could help me out.

[...]

11) 0 A.D.

This game hasn't been out yet, I guess we will be able to play a beta on September. You can get the news from [here]("http://wildfiregames.com/0ad/").

> 12) Glest

```
sudo apt-get install glest
```

> 13) isoccer

This game is still not even alpha, but you can check out what's what with subversion

```
sudo apt-get install subversion
svn co https://isoccer.svn.sourceforge.net/svnroot/isoccer/ isoccer
cd isoccer
chmod +x iSoccer
./iSoccer
```

---

### Post by bartos on 2008-05-19
FreeCol needs java to run.The game does install but will not run without java.
Hopefully another one off you list:popcorn:

---

### Post by atomkarinca on 2008-05-19
> **vjsimon said:**
> 3) FreeCol

```
sudo apt-get install freecol
```

> 8) Bygfoot

```
sudo apt-get install bygfoot
```

---

### Post by Perfect Storm on 2008-05-19
Savage 1:
[http://gaming.gwos.org/doku.php/guides:64bit:savage_1](http://gaming.gwos.org/doku.php/guides:64bit:savage_1)

FreeCol:
[http://gaming.gwos.org/doku.php/guides:64bit:freecol](http://gaming.gwos.org/doku.php/guides:64bit:freecol)

Globulation 2:
[http://gaming.gwos.org/doku.php/guides:64bit:globulation_2](http://gaming.gwos.org/doku.php/guides:64bit:globulation_2)

Yoda Soccer:
[http://gaming.gwos.org/doku.php/guides:64bit:yoda_soccer](http://gaming.gwos.org/doku.php/guides:64bit:yoda_soccer)

---

### Post by Sammi on 2008-05-19
Getdeb.net is a comvenient way of getting Ubuntu deb installers for apps and games that aren't in the official repos or just haven't been updated in a while. Here's the games section with 38 different games: [http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3)

---

