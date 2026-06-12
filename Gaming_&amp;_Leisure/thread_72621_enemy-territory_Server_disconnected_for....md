---
title: "enemy-territory: Server disconnected for..."
date: 2005-10-06
forum: Gaming &amp; Leisure
---

### Post by kerm on 2005-10-06
Hi,

I have recently installed ET and I can play the game fine initially (first map) but when the server loads a new map and gets ready to put me into the game, it shuts down and gives me a "Server disconnected for unknown reason".

I'm reasonably sure it's a Punkbuster problem because I can play fine on a non-Punkbuster server. What is confusing is that I have two "pb" directories: "~/.etwolf/pb" and "/usr/local/games/enemy-territory/pb". I'm not sure why. 

Even though I installed ET into /usr/local/games instead of my home directory, it seems in general a lot of files get copied to ~/.etwolf anyways (probably a user profile deal). I ran "pbweb.x86" in both pb directories because I am not really sure which folder needs updating (if any). Also, I noticed that the pbweb.log file is generated and kept in my ~/.etwolf folder. 

I would appreciate any help or suggestions. Thank you.

---

### Post by kerm on 2005-10-10
A guy from Even Balance (the makers of PunkBuster) told me to defrag my hard drive. I know fragmentation isn't as much of a problem on Linux (as opposed to Windows) and I'm not sure how to even do it. 

The logic is that since my computer is so slow that PunkBuster is timing out between map changes.

He said:

> If you take over 2 minutes to load the next map, PB will timeout in that time. Can you do a drive defrag, anything to speed up the system will help.

It probably does take me at least 2 minutes to load the next map so I can see this being a potential problem.

Is there a utility which allows me to defrag my hardrive painlessly? I haven't been able to find any information using slocate,man or info. I've seen a few programs that can be downloaded on Google but I'm not sure if I can trust any of them.

---

### Post by Efwis on 2005-10-10
[QUOTE=kerm]A guy from Even Balance (the makers of PunkBuster) told me to defrag my hard drive. I know fragmentation isn't as much of a problem on Linux (as opposed to Windows) and I'm not sure how to even do it. 

Is there a utility which allows me to defrag my hardrive painlessly? I haven't been able to find any information using slocate,man or info. I've seen a few programs that can be downloaded on Google but I'm not sure if I can trust any of them.[/QUOTE]
because of the way Linux is set up there is no need for deframenting the HDD. I've never seen any of these tools your talking about, but my understanding is that Linux doesn't need defragging, which is one of the reasons its better then Windows IMO. Not to bash Windows or MS, it's good software if you don't mind paying for everything, and the crashes it can have, which is usually caused by the fragmentation of files.

---

### Post by seethru on 2005-10-10
[QUOTE=Efwis]because of the way Linux is set up there is no need for deframenting the HDD. I've never seen any of these tools your talking about, but my understanding is that Linux doesn't need defragging, which is one of the reasons its better then Windows IMO. Not to bash Windows or MS, it's good software if you don't mind paying for everything, and the crashes it can have, which is usually caused by the fragmentation of files.[/QUOTE]
yes, if you've ever looked closely at the space you have free, you'll notice you "missing" some. Linux takes 5% from each partition for specifically that, to stop fragmentation.

---

### Post by kerm on 2005-10-10
Thank you for your replies! I'm just going to write them (Even Balance) back and tell them no dice on the defrag deal. 

I hate that my computer is just barely fast enough to play Enemy Territory ok but too slow for PunkBuster of all things. I think that 2 minute timeout rule stinks and tacks on to the system requirements of the game...it just shouldn't. I can keep reconnecting after the a map change but then I'll lose all my XP. :mad:

---

### Post by Hobgoblin on 2005-10-11
Memory has more impact on load times for ET than drive or processor speed.

We usually say 256MB is the bare minimum for Windows XP if you close every unneeded application.

Changing the com_hunkmegs setting in the game can help, see [this guide](http://www.planetwolfenstein.com/features/articles/pw_faq_rtcw.shtml#fastmapload) (it's for RtCW but applies to ET as well).

Not sure exactly how that applies to Linux but I hope it helps.

---

