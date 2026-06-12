---
title: "ATI/AMD Heroes of newerth very bad performance"
date: 2009-12-07
forum: Gaming &amp; Leisure
---

### Post by avengeru on 2009-12-07
Hello all,
first of all, sorry for my bad english.
Now the problem - Im using Linux - Kubuntu (9.10) with latest KDE/Kwin.
Yesterday i installed Heroes of Newerth ( new game from s2games ) linux version. And the problem is that i have on the lowest settings & lowest resolution 18-20fps... its same like on maximum settings 1680x1050 all high, AF16x + all effects enabled. Like most of u know its unplayeble.
My graphic card is ATI HD3870 with the latest catalyst installed (9.11), CPU AMD Athlone X2 5000BE overclocked to 3.1Ghz, 3gb RAM, 6gb swap.
I used to play this game "Windows version" On all max settings with 1680x1050 res on about 60++ fps it was very smooth.
I checked Vertical sync(Disabled everytime), i tried to force process priority(no effect at all), tried to disable Kwin(no effect) so im really out of ideas.

Thanks for your help, and please try to write understandably because im begginer in the world of linux, which is looks like not ment to be played :-(

---

### Post by Ferrat on 2009-12-07
Sadly ATi and Linux doesn't mix very well, but they are working on it, might also be a setting somewhere but not sure, make sure you have the latest ATi drivers and everything else is up to date and make sure you have activated the ATi drivers, other than that you might concider getting a NVIDIA card instead if possible

---

### Post by avengeru on 2009-12-07
Thx for ur reply,
i wont concider getting nvidia. I allways can install second OS WinXP only for games. But this is the only one game which i want to play on linux. Maby u are right about some troubles with video drivers, but i dont know how to figure it out, where is the problem.

---

### Post by sophicsage on 2009-12-07
I haven't had such problems with my ATI card.  I'm using a Sony Viao - NS series.  I've had no problem at all.  During installation the OS notified me that I didn't have the card functioning fully.  I installed the appropriate software through the Synaptic manager and I have full and total use of my system.  It has something to do with Linux being open-source and ATI having protections for their materials and you have to confirm it as an individual user.  For some reason, some companies just loooove MS and they want their hardware to run on a MS machine.  I don't get it.  A user is a user and the card is installed on your machine, so what's the big deal?

I've downloaded Sauerbraten, which is very similar to UT2004.  It runs extremely smoothly.  I plan to get more games, too.  I really think you may be having a set-up issue.  It may also be a game-specific problem.  I've only used Linux (Ubuntu 9.10) for two days and I'm happy with it.  I'm sure there is a solution.  

Oh, keep in mind that many games don't even work right in Windows even when it says that they should work with that OS or version.  I have taken many games back because they didn't work (unless that store would not take opened software).  Windows was no more friendly than Linux, and I'd say it's much less so.  Check Synaptic and the software center for 'ATI'.  That's how I found my own solution.

---

### Post by DeusExM1 on 2009-12-07
If you come up empty and you have tried everything could you please try using Gnome instead of KDE? Someone else posted about a similar problem and they were also a KDE user. 

Its probably not related, but if all is lost and you are about to give up try it.

---

### Post by Vadi on 2009-12-07
while the game is running, can you open the system monitor and see what are the top processes using cpu?

---

### Post by avengeru on 2009-12-08
> **Vadi said:**
> while the game is running, can you open the system monitor and see what are the top processes using cpu?

Yes sure, my cpu first core is used about 60-70% second core 15%. Game uses about 30-40% CPU.

ps. i dont like gnome&compiz, it was very buggy for me. Kubuntu is the first distro of linux i really like. After install i had no problems with X-Fi soundcard&5.1 repro, only slow window maximizing i had to fix with xserver.

---

### Post by Vadi on 2009-12-08
What are the process names?

---

### Post by avengeru on 2009-12-08
> **Vadi said:**
> What are the process names?

Here i made 2 screens for you. But i dont think CPU is the problem... 3.1 Ghz dual-core for this game is enought to run it twice on max details...

---

### Post by bud986 on 2009-12-08
Sounds like the problem im having since the last ubuntu update, I used to play this game also in linux on my laptop with and ati 3470, but since last ubuntu update my performance has been turned into a lag fest :P

---

### Post by Vadi on 2009-12-10
Try muting the sound, restarting the game and see if that works. Otherwise a different video driver version should do it.

Also, there are issues with HoN + KWin performance, S2 said.

---

### Post by avengeru on 2009-12-10
> **Vadi said:**
> Try muting the sound, restarting the game and see if that works. Otherwise a different video driver version should do it.

Also, there are issues with HoN + KWin performance, S2 said.

The main issue is... linux sux hard, now u all fans think "hmm stupid noob". 
But here are main reasons :
Graphic card support & gaming = one big bullsh*t, HON 15fps (aa not working) compare to windows 60-100fps.
Movie playback : mega video tearing... if u like quality.. forget about linux.
Music : Support for X-Fi is pathetic... Forget about all functions.. with the best NEW drivers u can upmix ur stereo sound to 5.1 and listen stereo music from ur subwoofer, coz there is no low pass filter avaible =)
Internet browsing : ATI&compiz... firefox is like a lagged nightmare, with ATI&Kwin its better... But now the best part - FLASH PLAYER, what the f*ck ? Eating up to 50% of my CPU, mega lags... control of videos in 50% not working. Almost imposible to surf without FlashBlock.

Because i want everything legal in my pc, and my current financial situation is not the best i cant afford buying windows&all programs i need... but when it will get better, cya linux.

That was my experience, im sorry if it was too ofensive.
To all people who are thinking about installation of linux ... i can say : Do it only on laptop or sh*tty old pc and prepare to waste ur time on solving problems.

I hope ill change my mind in near future, when new ubuntu will be released.

Thanks to all who tried to help ;-)

---

### Post by Vadi on 2009-12-10
Yeah whatever. ATI support for Linux sucks, everyone knows that, you get nVidia. I'm happily playing HoN on it.

Unless your laptop has a 'Certified for Linux' sticker, which afaik it doesn't, you shouldn't complain of hardware incompatibilities.

Cya.

---

### Post by avengeru on 2009-12-10
> **Vadi said:**
> Yeah whatever. ATI support for Linux sucks, everyone knows that, you get nVidia. I'm happily playing HoN on it.

Unless your laptop has a 'Certified for Linux' sticker, which afaik it doesn't, you shouldn't complain of hardware incompatibilities.

Cya.

Going to try Xubuntu.. last chance for linux =)

---

### Post by DeusExM1 on 2009-12-10
did u try to get rid of KDE and use Gnome?

---

### Post by Vadi on 2009-12-10
> **avengeru said:**
> Going to try Xubuntu.. last chance for linux =)

You know the perf is a regression for ATI from... 9.04? or something like that.

Won't help...

---

### Post by avengeru on 2009-12-11
> **DeusExM1 said:**
> did u try to get rid of KDE and use Gnome?
Sure, i tryied it on gnome and kde.. ( ubuntu, kubuntu now Xubuntu ) :-) all the same. Maby i should give a chance to windows version emulated by WINE ? But i think its not game problem.. its our awesome ATI...

---

### Post by ostaja on 2009-12-11
I'm using ubuntu 9.04 and gnome. HoN:n works very well with nVidia 7600gt. It seems ATI cards have very bad performances in linux, atleast 3xxx series.

---

