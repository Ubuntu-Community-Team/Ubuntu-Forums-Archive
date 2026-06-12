---
title: "Need Help in Xubuntu Enabling Sound on Optiplex GX1 PC"
date: 2009-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Groucho Marxist on 2009-05-17
As a new user of Linux, I am currently trying Xubuntu 9.04 on my humorously-old Dell Optiplex GX1 PIII computer. After some digging on these forums, I have come to the conclusion that I have issues with my Crystal CS4236B integrated sound card. 

I have attempted to follow [these instructions]("http://ubuntuforums.org/showpost.php?p=2039415&postcount=3"), but I have not been able to alleviate my lack of sound in Xubuntu. As I am "taking my first steps into a much larger world," I feel rather lost when it comes to understanding how to solve this problem. Any help would be greatly appreciated.

---

### Post by itsols on 2009-05-17
Hi, just thought you'd like to know. I've installed Ubuntu 7.10 on my GX110 (also PIII 866MHz) box. It's flawless - no issues with the sound card.

But I do have a feeling that your on-board sound system is defective. Perhaps installing an external one may help narrow down the problem.

Good luck with it.
Khalid

---

### Post by Groucho Marxist on 2009-05-17
Update: now, my sound card shows up in PulseAudio controls and I tested my ability to listen to music through Audacity. However, Ron Burgundy and the Channel 4 News Team's "Afternoon Delight" plays through my speakers only through the aforesaid program. 

I am going to re-do the steps listed in the link I posted above to see if I can resolve this issue.

---

### Post by sTpny on 2009-08-20
You are on the right track. In fact, it should be working. 

You have added snd-cs4236 to /etc/modules I assume. First thing I would do is see if thats actually the soundcard you have. run "asoundconf list" to make sure. Now you probably need to disable ESD. That should be in your "sound" properties, under system->preferences. If it still wont work right, then you are probably looking at a permissions problem.  Open up your "Users and Groups" and make sure you have permission to use the sound card. When you open your volume controls, make sure it is using the cs4236 as the sound device, and not the default. Good Luck. 



Tony, 



PS.  Crappy old sound cards are very cheap, but most will be better than what the GX1 comes with.  You should consider upgrading, rather than messing around with that crappy old thing.  

PSS.  Have you managed to get your 3d graphics to work?

---

