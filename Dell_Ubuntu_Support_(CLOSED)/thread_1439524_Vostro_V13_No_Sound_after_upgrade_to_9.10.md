---
title: "Vostro V13: No Sound after upgrade to 9.10"
date: 2010-03-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by parrisdc on 2010-03-26
Hi all,

I upgraded my Dell Vostro V13 from 9.04 to 9.10 shortly after getting it, and quickly discovered I have lost my sound.  After searching the 'net for a while, I have not found any related issues, and wonder if anyone might be able to help me walk through solving the problem.

I'm nowhere near a newbie, but it has been a long time since I've needed to solve a glitch like this.  ;)

Many thanks in advance!

---

### Post by Alaska_Jack on 2010-03-26
I was able to fix my identical problem by following the steps here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I can't be of more help, because I'm not exactly sure which of the steps I took worked. I was kind of muddling my way through and all of the sudden I noticed it was working again.

---

### Post by lobotomy42 on 2010-05-20
Did you ever get this fixed, parrisdc? I'm considering upgrading to 9.10 myself.

---

### Post by abalaban on 2010-05-31
This is non-guru help:
I found it helps sometimes to run alsamixer program in terminal and un-mute some channels that may be relevant to you.

mute/unmute - type M
move right/left - right/left arrow
increase/decrease - up/down arrow

Alex

---

### Post by mikethesoccerfreak on 2010-12-26
ok, im having the exact same problem except im a total newbie, please help i have no idea what to do or what you guys are talking about

---

### Post by lidex on 2011-01-05
On an upgrade old configuration files can cause conflicts. Try removing them:
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Logout/in.**

---

