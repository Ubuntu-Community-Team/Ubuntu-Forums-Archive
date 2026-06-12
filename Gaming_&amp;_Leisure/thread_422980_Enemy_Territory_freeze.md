---
title: "Enemy Territory freeze"
date: 2007-04-25
forum: Gaming &amp; Leisure
---

### Post by ElVirolo on 2007-04-25
Hi,

Every time I play Enemy Territory, the system eventually freezes and I have to use the Sys Req keys. I didn't have this under Dapper... Has anyone else experienced this problem ?

What information should I give you (BTW I have a ATI Radeon 7500 video card with the free drivers) ?

Alex.

---

### Post by donkyhotay on 2007-04-25
I had a similar issue with a radeon x700 though admittedly I only played the game once then uninstalled it.

---

### Post by lakersforce on 2007-04-25
Happens all the time for me too. All the time!! I have a nvidia card.

And I have posted this error (in much greater detail) several times before. Appereantly no one has any clue at all as to what causes this, so dont excpect your issues to get solved :(

---

### Post by ElVirolo on 2007-04-26
Is it possible to file a bug for this ? I know Enemy Territory can't be supported ...

---

### Post by Inigo Montoya on 2007-04-27
@ ElVirolo:
what are Sys Req keys?

@ lakersforce:
coul you post a link to your former posts regarding this issue?

---

### Post by lakersforce on 2007-04-29
> **Inigo Montoya said:**
> @ ElVirolo:
what are Sys Req keys?

@ lakersforce:
coul you post a link to your former posts regarding this issue?

Well, it basicly exits with a "Signal 11" fault. I have tested my ram and they are not faulty.

---

### Post by aldenhg on 2007-04-30
I'd guess it's your video card's ram. can either of you test with a different card?

---

### Post by lakersforce on 2007-04-30
Yes, same thing. So it is not because faulty video card or faulty ram.

---

### Post by Nesnej Trick on 2007-05-05
I'll take the liberty to resurrect this thread because I've found the solution:

You'll need to add these lines to the "Device" section for your card in your xorg.conf
> Option "Capabilities" "0x00000800"
Option "KernelModuleParm" "locked-userpages=0"

Solution courtesy of [http://www.thinkwiki.org/wiki/Problems_with_fglrx#Freeze_while_using_OpenGL_Apps](http://www.thinkwiki.org/wiki/Problems_with_fglrx#Freeze_while_using_OpenGL_Apps)

---

### Post by tufu5 on 2009-04-15
I had this problem but you can still play on servers that don't use punkbuster.

---

### Post by Jeneral22 on 2009-06-07
I have this problem with ET and a Radeon 3850. I am using the latest ATI drivers and have tried sound driver updates and new sound servers but no luck. I can usually play for 5-20 minutes then the game and computer freezes and the sound just loops over and over then... alt/sysrq REISUB to get the system back running again. 

The PC will run for days with no problems but running ET w/PB just kills the PC. Driving me nuts. I still dual boot WinXP and do not want to install ET on XP just to be able to play... :(

---

### Post by Barky on 2009-06-08
did you try the solution two posts ago?

Have you disabled pulseaudio?

---

### Post by Jeneral22 on 2009-06-10
Barky,

Yes, I tried that last night and it was already saved in the config file. 

Used the killall -9 pulseaudio command then started ET. Appeared to be working and then I froze again. This one was different because I was frozen but not looping the sound. I could here the other players playing and could see them moving around but everything was blurred. Very strange. I am planning on trying again tonight using the Killall to see if I just ran into a map glitch because I was playing a members home made map.

Thanks for the help.

---

