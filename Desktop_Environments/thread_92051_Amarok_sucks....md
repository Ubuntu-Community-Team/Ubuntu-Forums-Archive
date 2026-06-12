---
title: "Amarok sucks..."
date: 2005-11-18
forum: Desktop Environments
---

### Post by sammyguy193 on 2005-11-18
OK. here's the deal... I LOVE LINUX! But seriously, amarok blows when it comes to an mp3 collection above 7000 songs... really... I hate it. Amarok, juk, rhythmbox, you name it- they're slow, ugly, and not usable for a collection of this size. Any suggestions? I've tried almost every music player/jukebox i can get my hands on for linux... Hate to say it, but iTunes simply works, albeit slightly sluggish, its still a heck of alot more responsive than any linux alternatives i've tried.... Any suggestions out there?


Cheers,
Sam

---

### Post by aysiu on 2005-11-18
Sorry to hear the choices aren't working well for you. I, too, found AmaroK a bit sluggish, but JuK has suited my needs just fine (and I have 12,000 songs in my MP3 collection).

Maybe iTunes via Crossover Office may be your solution.

---

### Post by Drain on 2005-11-18
I don't know if you mentioned trying xmms (the winamp clone), which is what I usually use. I'm only dealing with around 3,000 songs over a network, though.

---

### Post by DJ_Max on 2005-11-18
The speed of the application will vary depending on the language and your computer.

Anyhow, Juk should work, seeing as aysui has a huge collection of music. There's also [Banshee](http://banshee-project.org/).

---

### Post by uopjohnson on 2005-11-18
also... have you tried aamrok using a databse engine other than SQLlite which isn't really designed for that kind of load.  Try getting mysql set up.
[http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo](http://amarok.kde.org/amarokwiki/index.php/MySQL_HowTo)

---

### Post by doclivingston on 2005-11-18
Rhythmbox and Banshee both work fine with my ~5500 song library, I can't comment on the others because I don't use them regularaly. What in particular is slow? starting up, certain bits if the user-interface?

---

### Post by 23meg on 2005-11-18
I love Amarok, but am worried that the KDE libs are taking too much RAM / cpu cycles in my Gnome environment. It's very slow to start up as well (+10 seconds on my 1.79GHZ Sonoma machine). But I haven't found a GTK app that even comes close to its functionality. 

How much RAM / CPU cycles will running one single KDE app (Amarok) plus the KDE libs typically consume in Breezy? And do they stay loaded once I shut down Amarok? I do see some entries starting with K in system monitor but am not sure how much they actually are hogging me down since I don't know for certain if they are the KDE libs. I'm such a total stranger to KDE.

---

### Post by cstudent on 2005-11-18
Well this is a little discouraging. I was planning on taking an old P3 1ghz machine I have and making a jukebox out of it. I was going to install Kubuntu and use Amarok, but I have about 15k+ songs. Guess I better do some research before I commit to that.

---

### Post by xequence on 2005-11-18
I found amaroK to be great, though a bit unstable. iTunes on windows is decent, but its hard to tell since its horribly slow.


[QUOTE=aysiu]Sorry to hear the choices aren't working well for you. I, too, found AmaroK a bit sluggish, but JuK has suited my needs just fine (and I have 12,000 songs in my MP3 collection).

Maybe iTunes via Crossover Office may be your solution.[/QUOTE]


Quite the nice collection, also I tried iTunes in crossover once and the sound didnt work.

---

### Post by kairu0 on 2005-11-18
[QUOTE=sammyguy193]Any suggestions out there?


Cheers,
Sam[/QUOTE]

I've never had a collection as large as yours, but QuodLibet doesn't feel sluggish once it is up and running.

---

### Post by GeneralZod on 2005-11-19
[QUOTE=23meg]I love Amarok, but am worried that the KDE libs are taking too much RAM / cpu cycles in my Gnome environment. It's very slow to start up as well (+10 seconds on my 1.79GHZ Sonoma machine). But I haven't found a GTK app that even comes close to its functionality. 

How much RAM / CPU cycles will running one single KDE app (Amarok) plus the KDE libs typically consume in Breezy? And do they stay loaded once I shut down Amarok? I do see some entries starting with K in system monitor but am not sure how much they actually are hogging me down since I don't know for certain if they are the KDE libs. I'm such a total stranger to KDE.[/QUOTE]

RAM could be fairly significant (I don't have figures though; sorry) but the CPU usage should be negligible.  Theoretically, unused libs will be ditched as soon as you close the last app using them.

---

### Post by asimon on 2005-11-19
Amarok rocks!

I use amarok with around 12,000 titles and it works reasonable fast -- this is with the standard sqlite setup. Juk is unberable slow with that many songs, rhythmbox is okay but there I miss all those rocking amarok features.

BTW amarok is currently broken under dapper, it can't write access it's collection.

---

