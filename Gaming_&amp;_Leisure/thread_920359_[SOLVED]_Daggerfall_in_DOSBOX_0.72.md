---
title: "[SOLVED] Daggerfall in DOSBOX 0.72"
date: 2008-09-15
forum: Gaming &amp; Leisure
---

### Post by cisforcojo on 2008-09-15
I'm trying to get Daggerfall running in DOSBOX and it's just resulting in a black screen.

I've done a full install and have edited Z.CFG to point to the c:\dagger\arena2

I've installed the 2.13 patch as well. When I run 'fall.exe z.cfg' the screen just goes black. That's it. I have disabled all sound and still there's no difference. 

Any help would be greatly appreciated!!!

---

### Post by M_the_C on 2008-09-15
[Here is a thread from the Official Elder Scrolls forum where someone had the same issue.]("http://www.bethsoft.com/bgsforums/index.php?showtopic=860924&hl=black")
[Another one suggests removing dagger from Z.cfg, which sounds strange when every other thread suggests adding it, but might be worth a try.]("http://www.bethsoft.com/bgsforums/index.php?s=&showtopic=868935&view=findpost&p=12671661")
Failing that I can only suggest a reinstall.  [Carefully following the guide just to be sure.]("http://www.bethsoft.com/bgsforums/index.php?showtopic=479044&st=0&p=6877868&#entry6877868")

Sorry I can't be of more help.

---

### Post by cisforcojo on 2008-09-15
It's 1:37AM and I've gotta go to work tomorrow so I have no more time to put towards this but I HAD missed a step. Unfortunately, that wasn't the root of my problems. I'll keep on going :) I'm running in KDE4 right now. I'll try it in GNOME tomorrow to see if there's any change.

---

### Post by DarkSim on 2008-09-19
I made a little FAQ a while back on how I got it to work. Not the best. I blame my short attention span. :D

[http://mrdarksim.webs.com/howtotesiionlinux.htm](http://mrdarksim.webs.com/howtotesiionlinux.htm)

You can skip this part. I forgot to take it out.:
<skip>Now go back to DOSBox and type the following:
C:
CD..
RESCAN
DAG213

The patch will start to install itself. Answer yes on all the questions. After the patch installation is done, you can exit DOSBox.</skip>

---

### Post by cisforcojo on 2008-09-20
I followed a howto that was similar to yours but yours worked for me. It was the changing the files from read-only before applying the patch that did it. Thanks!!!

---

### Post by Category on 2008-09-20
I just got this game working yesterday, and have been lost in it's lovely world all day long! If anybody needs a no-cd patch, search for fdagger.exe - that will get it running easier!

And does anyone know if anybody has hacked this to do higher resolutions? I'ld love to see it in 640x480!

---

### Post by cisforcojo on 2008-09-21
No need for a no-cd patch after running the 2.13 patch and then modifying z.cfg.
Watch out for the bugs ;) I remember them really getting in the way back when I was playing it around 10 years ago. I'd check out a program that can try and recover saved games in teh event that your game screws up. I remember a utility like that being pretty useful!

---

### Post by Mordimier on 2008-09-22
Hello everyone

Trying to install Daggerfall. I have the original CD but i think it may be too scratched to install again. Everytime I try to install it freezes during the installation process. So I am trying to download a free version of it. I tried downloading winxpdaggerfallinstaller from fileplanet.com. Then I tried another site (some foreign site) that had a "full cd" download. I figure i may get lucky with that one. I'm not too knowledgeable about it, but i think you start dealing with "ISOs" when not having an actual CD. So i installled the game through the winxpinstaller and tried running it with my original and scratched CD. Not recognizing it, getting an error message "Looks like you inserted the wrong CD. Please insert your daggerfall cd and try again" in DosBox. also I am trying it with dosbox 0.72 as well. So I'm a little lost as far as what I should do next. Can some one lend me a hand and point me in the right direction? I'd rather find a less cost effective way to deal with this as opposed to buying the game off ebay for the exorbitant price of up to 70 bucks. Thanks!!!

Chris

---

### Post by kic on 2008-09-24
This is a little late since the problem has already been solved, but just in case someone else searching for this issue finds this thread (it's ranked well on google), here is my solution.

I was running into this same problem when it finally dawned on me what I was doing wrong: I was mounting the directory incorrectly in DOS Box. Duh!

If you look at z.cfg, the default path is c:\dagger\arena2 for where it's looking for things. If, like me, you are (or were) mounting your Daggerfall directory as "c", that won't work because it will never find that \dagger\arena2 directory.

My solution was simple: mount c as the directory containing the "dagger" directory. Specifically, I'm using /Users/myusername/Applications/DOSBox as "c" and "dagger" is inside that same DOSBox directory.

The game now loads right up, I see the opening video, have a menu, etc. Groovy.

---

### Post by Mordimier on 2008-09-25
Hello everyone

Trying to get daggerfall to run. I have a copy of it but i believe it's too scratched up to use. I think i may have to try and look for another one but i was curious if i go about things without it. I downloaded a "full cd" version of daggerfall but i don't know how to set it up. Do I need an ISO file or something if i have no CD? I tried downloading another way through a Winxpinstaller for daggerfall, all it requires is the CD. I tried to start the game in Dosbox but it tells me it doesn't recognize the CD. So some one lend me a hand please? any other questions regarding the files I downloaded i'd be happy to give more details Thanks!

---

