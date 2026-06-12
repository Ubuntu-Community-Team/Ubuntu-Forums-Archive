---
title: "WoW and Cedega 5.1 lockup"
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by pwykersotz on 2006-11-07
A new problem just started for me, and I'm at a bit of a loss.  I have been running Kubuntu for several months now, and World of Warcraft has worked for me with Cedega 5.1 from the get go.  Just a week or so ago though, the game began to lock up moments after I log in.  I can alt-tab out and kill it, but that's all.

Originally, I had grabbed a folder from a Windows install of WoW and was running the .exe through Cedega, but when this problem started I installed comletely via Cedega.  This held off the problem for about a week, and now it's locking again.

I don't have locking problems on any other game or app that I run, so this is quite confusing.  Unfortunately, I don't know the location of any pertinant error logs, so that's all I can give without feedback.  Can anyone help?

System Specs:
AMD Athlon 64 X2 4200+ 2.2GHz Socket 939 Dual Core
EPoX EP-9NPA+Ultra Socket 939 NVIDIA nForce4 Ultra ATX AMD Motherboard
Patriot Signature Series RAM 2GB (4 x 512MB) (PC 3200)
eVGA Geforce 7600GT 256MB GDDR3 PCI Express x16 Video Card

---

### Post by reiki on 2006-11-07
You have nVidia so I'll jump in here (I don't know the ins-and-outs of ATI)

#1- Read this:
[http://www.ubuntuforums.org/showthread.php?t=290761](http://www.ubuntuforums.org/showthread.php?t=290761)

#2- (Things discovered since that post) You don't need Cedega to run WoW in Edgy. Add the winehq repositories for Edgy as outlined in that post. Install Wine 0.9.24 using apt or synaptic. Now go to:
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)
and scroll down a bit to where you see "Wine 0.9.24 : Binary patch". You can download just that ONE FILE ( winex11.drv.so ) and replace the existing one. Done!

WoW runs great on Edgy. I have nvidia 7300GT with 512MB, 2 gigs of ram, pentiumD 930 (3GHz). And it's now simple to do thank to Nick Law and AlanJ over at WineHQ for their hard work and much testing and for making that patched binary available.

Advantages of this method:
-you're not paying a monthly fee to play a game for which you pay a monthly fee.
-you're installing from repositories (no compiling) and copying over one patched file.

I was showing my son last night (he also plays WoW but on a Windows machine). Up to 75-80 FPS in Iron Forge at the Great Forge. Full screen glow is ON, textures all on high, death effects OFF. When I go outside where there is more "distance" my FPS actually goes down... to about 45-50. But s--m--o--o--t--h as silk.

On that appdb page if you scroll down, Nick Law tells you how to do a regedit that was originally (I think) to help an ATI issue, but it was discovered that it benefits nVidia users as well. IT DOUBLED MY FRAME RATE (did I say that loud enough?)

Don't struggle. This is easy now. Follow the directions and have fun! :)

---

