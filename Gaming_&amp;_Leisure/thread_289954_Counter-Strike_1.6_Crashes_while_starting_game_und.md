---
title: "Counter-Strike 1.6 Crashes while starting game under Wine 0.9.9"
date: 2006-10-31
forum: Gaming &amp; Leisure
---

### Post by Justy on 2006-10-31
**[COLOR="YellowGreen"]SOLVED![/COLOR]**
[B]The only thing to do is update your wine by adding belove to repos:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main[/B]

:neutral: 

Hello to all!

I have been trying to get Counter-Strike 1.6 work under Wine 0.9.9 but I got an error. I have searched google to find a solution but found nothing that solves my problem. Then I tried to solve it myself but that was unsuccessful neither. So I am here!

Okay. I can run CS, but when I try to create a new game with/without bots or try to join an internet server, it just crashes..
Here is a screenshot of the time just before the crash. There is a blue semi-transparent space.
[[IMG]http://justyy.by.ru/ssCSCrashesOnUbuntus.png[/IMG]]("http://justyy.by.ru/ssCSCrashesOnUbuntu.png")

And here is my console output from the start of CS and end of CS : [SIZE="1"][http://paste.ubuntu-nl.org/29593/]("http://paste.ubuntu-nl.org/29593/")
[/SIZE]
It tells me that the File demoheader.dmf was never closed.

Could you please give a hand to me to solve this problem? Thanks for your prompt answer.

My system configuration:
-Linux Ubuntu 6.06 LTS Kernel 2.6.15-27-386
-ATI Radeon x300 128mb graphics card
-I have disabled pixelshader in winecfg at graphics tab
-I can hear sound effects and background music at main menu and other menus at CS
-The OSS driver is enabled in winecfg in sounds tab

---

### Post by haxer on 2006-10-31
Try my guide at google.com search for steam4linux enjoy

---

### Post by Justy on 2006-11-01
> **haxer said:**
> Try my guide at google.com search for steam4linux enjoy
Oops! I unfortunately do not use steam.. I just downloaded the counter-strike 1.6 and runned it. It works perfect with win$hit..


 ](*,)

---

### Post by Mooie on 2006-11-01
you should probably use a newer wine than the default one in the repos, just add this tour sources
```
deb http://wine.budgetdedicated.com/apt dapper main
```
i've heard that it works the same on edgy as on dapper

---

### Post by reiki on 2006-11-01
there's an edgy repo at winehq. It just isn't in the apt docs there yet for some reason.

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

are both valid as well as teh dapper repos

---

### Post by Justy on 2006-11-02
> 
you should probably use a newer wine than the default one in the repos, just add this tour sources
Code:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

i've heard that it works the same on edgy as on dapper
> there's an edgy repo at winehq. It just isn't in the apt docs there yet for some reason.

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main

are both valid as well as teh dapper repo


Thanks both of you Mooie and reiki, that 'worked' after I 'updated my wine'.. Thanks again!

---

### Post by Megatog615 on 2006-11-28
This happens to me with the newest wine 0.9.26!

---

### Post by Justy on 2006-11-29
Try changing your wine version until you find the right one ;)
I use version 0.9.24 now with no problem at all..
Also be sure that you use the latest graphics driver of you gfx card.

Happy ubuntu ing.. :)

---

### Post by encikraju on 2006-12-25
Hi, Sorry if my problem doesnt match the topic here but anyone know how to remove the taskbar(Applications,Places,System-that thing) when playing cs1.6?Because of that i can't see the time,life, bullet left in cs windows. Anyone? Ah..and also how to make wine as default program fow hl.exe?

---

