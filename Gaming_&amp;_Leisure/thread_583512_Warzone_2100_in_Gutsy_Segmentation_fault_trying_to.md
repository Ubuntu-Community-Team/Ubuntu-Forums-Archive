---
title: "Warzone 2100 in Gutsy Segmentation fault trying to load saved game"
date: 2007-10-20
forum: Gaming &amp; Leisure
---

### Post by Original Brownster on 2007-10-20
Hi,
It's worked fine until the upgrade to gutsy gibbon. I'm using the fglrx drivers with a radeon 9600pro so not using compiz-fusion at the moment because of issues with 3d gaming and this driver combination.
I have doom3 installed and working fine still but when I run warzone and try and load a saved game it hangs.
If I run it from within a terminal I see that on exiting I get 'no such file or directory' and a segmentation fault.
If I wipe out the .warzone2100 directory and re-run I can start a one player skirmish again but after saving the game I get the same errors. Anyone else got this problem? 
I think I found a [bug report]("https://bugs.launchpad.net/ubuntu/+source/warzone2100/+bug/134533") which might be related.

---

### Post by Maximus86 on 2007-10-22
Hi! 
I'm having the same problem, videocard is a radeon 9200 mobility, I can play all sorts of other games, and played warzone 2100 before on Feisty... My terminal says 'segmentation fault, core dumped'... I also posted on wz2100 forums: 
 [http://forums.wz2100.net/index.php?topic=1051.0]("http://forums.wz2100.net/index.php?topic=1051.0")

Maximus

---

### Post by Original Brownster on 2007-10-22
Hi,
I've subscribed to the bug tracker I mentioned and have since had quite a few people all say the same thing.
Apparently if you have the SVN version it will play without sound, well at least it's not just me / you so I'm sure they will fix it soon. 
I love this game, I spend hours playing it so perhaps it's not a bad thing that I cannot play it for a while anyway :)

---

### Post by tez1982 on 2007-10-22
I'm having the same problem - bumma was hoping for a quick fix!

---

### Post by Maximus86 on 2007-10-23
Crap :( Even without sound it doesn't seem to work, ah well, I hope it wil get fixed soon because I also love this game.... Let's *ALL* hope it will get fixed soon, shall we? [-o<


Maximus

---

### Post by Original Brownster on 2007-11-06
I've checked out the warzone repository and they have 2.0.8.rc1 as a deb file. I installed it but had to remove the warzone2100-data deb.
It works for me however there is another problem, the map overview bottom right never shows the terrain, it's just dots and blobs. Probably something to do with map data files because if you try and install this deb whilst the data deb is installed it dies with errors because it's going to overwrite another file. I did force an install over the data file but it makes no difference either way it seems.

Anyone play this online?

---

### Post by Zyphrexi on 2007-11-27
I'm considering compiling the source. I'd rather do that than use an Etch package.

---

### Post by KaYnemO on 2007-12-18
hmmm -  so no real solution here, eh?

---

### Post by Original Brownster on 2007-12-18
> **KaYnemO said:**
> hmmm -  so no real solution here, eh?

You can use the deb file from the warzone project, version 2.0.8_rc1 works [ download here]("http://wiki.wz2100.net/Releases#Version_2.0.8_RC1")
version 2.0.9 does not work for me though.

The problem I reported earlier about not seeing the contours on the map was me not realising this is a feature you toggle on and off, doh!

---

### Post by Hugolp on 2008-01-03
I just discovered Warzone 2100 3 days ago and its a great game. The problem is that it doesnt load saved games. When trying to load a game it quits, ******* the screen resolution also. I have to change the resolution for the system to load it fine again.

I am running the one from the Gutsy repositories, that is v2.1 . Versions recomended here are older, but I have tried as well. Version 2.0.8 and 2.0.8 RC1 both have no sound and completele stops the computer when selecting a worker unit.

Without being able to save its imposible to go any further in the game. Anyone got a solution?

Hugo

---

### Post by e_racer1999 on 2008-01-19
no solution offered here, but i'm having the same problem.

---

### Post by craffojf on 2008-01-31
I have the same prob. Cant load save file, closes with low resolution ubuntu left. Man! I wish I could play this game again. Worked well on Windows:(

---

### Post by Feudal on 2008-02-27
Yep - same problem here - tried versions 2.08 / 2.09 - these either did exactly the same (i.e. crashed/hung when trying to load saved games) or ran so incredibly slowly (i.e. seemed to be a graphics acceleration issue) that I gave up the will to live... 

I'm running a Radeon 9200 too - seems like this might be the problem - Hmmm - come to think of it I seem to remember having issues with the driver for my card - some compatibility issues with compiz (which is now working beautifully).  

I wonder if its less to do with warzone and more to do with ATI's dodgy drivers? I think I read something somewhere about this being part of the same bug  that causes problems with the suspend function on Gutsy? (My system won't suspend either - not sure if its linked)
 
A fix wud be great! ;-)

---

### Post by TWO on 2008-03-29
Did anyone find a solution to this? 

I'm not running the game on a fancy graphics card, just an Intel 915GM or something like that.

Looking at the [bug report]("https://bugs.launchpad.net/ubuntu/+source/warzone2100/+bug/134533") that was posted earlier in the thread, the last person to post said that the problem had been resolved and that they had requested that it be synced into Hardy Heron.

It would be nice to have a solution for the current one though!

---

### Post by TWO on 2008-05-06
Seems that the problem has been resolved in Hardy Heron!

:)

---

