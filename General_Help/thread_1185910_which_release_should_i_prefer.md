---
title: "which release should i prefer"
date: 2009-06-12
forum: General Help
---

### Post by erkuserdem on 2009-06-12
Hi i'm a winxp user, and I want to switch to Linux. And I decided to install ubuntu. But i want to ask which release should i install. Here are some information about my hardware:
LG le50 express laptop with ATI chipset
ati on board video card radeon x200
ralink rt2500 wireless card
sigmatel audio device (this is important because in live cd 9.04 my sound has problems)
intel pentium M 1.7
1024 mb ddr2

---

### Post by qwertyuiop96 on 2009-06-12
I think you will be fine with the standard Ubuntu.  I'm not sure if your machine could handle KDE 4, though KDE 3 (Or an older version of Kubuntu)  would be fine.  Xubuntu would run great, though it doesn't look as nice.

Hope that helped

---

### Post by erkuserdem on 2009-06-12
But I want to use Ubunutu, just want my hardware to work correctly

---

### Post by leandromartinez98 on 2009-06-12
> **erkuserdem said:**
> But I want to use Ubunutu, just want my hardware to work correctly

Download the latest version (9.04) and try it with a LiveCD to see if the hardware works fine. It should work. I have it installed on older hardware than yours, and with and ATI graphics card as well, and it works very nice.

Edit: Sorry, now I've seen that you had problems with the audio with the liveCD. Try the 8.04 version then. If you still have problems, that I would go to other distribution, either Debian (for stability) or Fedora 11 (which has the latest kernel and drivers, and which I've tried and seems very nice).

---

### Post by erkuserdem on 2009-06-12
I tried 9.04 live CD, everything is OK but sound, on startup i hear a terrible voice like tatatatata

---

### Post by qwertyuiop96 on 2009-06-12
Oh, release.  If 9.04 isn't working, try 8.04.

EDIT- People seem to have beat me to it. :-)

---

### Post by TheNosh on 2009-06-12
> **erkuserdem said:**
> I tried 9.04 live CD, everything is OK but sound, on startup i hear a terrible voice like tatatatata

... you mean litterally a voice, or something instumental? ubuntu has a startup sound (which can be changed) but i wouldn't call it terrible

---

### Post by erkuserdem on 2009-06-12
I had sound problem with all releases of ubuntu like 8.04 or 8.10 or 9.04,  i will be using ubuntu with this fail but i hope somebody fixes this problem in new release, that's why i wrote my sound card type :)

---

### Post by theozzlives on 2009-06-12
> **erkuserdem said:**
> I tried 9.04 live CD, everything is OK but sound, on startup i hear a terrible voice like tatatatata

That's prolly the drumroll you hear at the login screen.

---

### Post by erkuserdem on 2009-06-12
> **TheNosh said:**
> ... you mean litterally a voice, or something instumental? ubuntu has a startup sound (which can be changed) but i wouldn't call it terrible
 
:D of course I know ubuntu startup sound and i think it is great,  im talking about a sound that is like a brokendown machine :D

---

### Post by leandromartinez98 on 2009-06-12
> **erkuserdem said:**
> I had sound problem with all releases of ubuntu like 8.04 or 8.10 or 9.04,  i will be using ubuntu with this fail but i hope somebody fixes this problem in new release, that's why i wrote my sound card type :)

If there is really a sound card driver problem, try the latest Fedora, the latest kernel may have solved some issue for your card.

---

### Post by erkuserdem on 2009-06-12
> **leandromartinez98 said:**
> If there is really a sound card driver problem, try the latest Fedora, the latest kernel may have solved some issue for your card.
 
no i dont want any other distro, my all hardware drivers work correctly on mandrive but i want to you ubuntu

---

### Post by leandromartinez98 on 2009-06-12
Ok, then, I think you should install 9.04 and from there try to fix your sound problem. Maybe a good idea is to google for your sound card name and "ubuntu" or "linux" to check if the problem was already reported by someone else.

---

### Post by leandromartinez98 on 2009-06-12
Just an addition: given that you are having systematic problems with every Ubuntu release, trying a liveCD of the newest linux distribution (currently probably Fedora 11) would be useful to see if the problem persists with the newest kernel and drivers. All of these can be upgraded in Ubuntu after a standard instalation, so it can be a hint on how to fix your issue.

---

### Post by erkuserdem on 2009-06-12
ohh I think I got it :)  so you say ubuntu and its kerner are different things. why fedora has the latest kernel so ?

---

### Post by leandromartinez98 on 2009-06-12
The kernel is the "hard core" of the OS. All of them use the Linux kernel. Ubuntu 9.04 was released in April, and used the latest kernel that was released until then and could be incorporated in the distribution. Fedora 11 was released a few days ago, and in the mean time (between the Ubuntu 9.04 and Fedora 11 releases), there was one (or two?) kernel updates. Ubuntu 9.04 comes with the 2.6.28 kernel, while Fedora 11 comes with the 2.6.29. The kernel includes most of the drivers, so maybe some issues were solved in this newest version that are relevant to you.

---

### Post by ronz0o on 2009-06-12
Ah, the age old question. "Which version of Linux is best for me?" The simple answer is one that we cannot answer. YOU must try them for yourself, see which one you like best, and which one fits you better. Try them all, you may actually learn something in the end. =)

---

### Post by erkuserdem on 2009-06-13
So am I able to install ubuntu 9.04 and then update the kernel to the latest version?  And also I want to ask who are developing and updating kernel ??
 
Also ronzo0 i dont ask which distro should i prefer, I ask which ubuntu version should I prefer.

---

### Post by gradinaruvasile on 2009-06-13
Only the startup sound has problems? Sometimes on my wives laptop the intro sound skips some "frames" at startup (its P4 1.6Ghz, intel chipset, ati video card - dell c640) but after that it works just fine.
Did u check it by playing music and recording your voice with the microphone (applications->sound and video->sound recorder)?

---

### Post by akakingess on 2009-06-13
If I understand "erkuserdam" he definitely prefers and wants to stick with Ubuntu. As far as the kernel updates go, when the development team has deemed it stable to release for a particular version of Ubuntu they will have it as part of your normal "available" updates. I would just install and try to see if we can't find a way to fix the sound issue. It may be a driver update, or some other update that will be installed after you get up and running and online.

akakingess

By The Way - you may not be able to update to the most current kernel if the dev team has not yet tested it and deemed it stable.

---

### Post by ad_267 on 2009-06-13
> **erkuserdem said:**
> I tried 9.04 live CD, everything is OK but sound, on startup i hear a terrible voice like tatatatata

The startup sound often sounds rubbish like that for me when running the LiveCD, I wish they would disable it when running it from CD. After installing my sound is fine though, I expect it would be the same for you.

---

