---
title: "Quick question about dule boot?"
date: 2006-08-03
forum: Desktop Environments
---

### Post by bobleny on 2006-08-03
I will have Ubuntu on one HDD and XP Home on the other. Would it be posible to run my windows apllications with out leaveing the comfort of my linux without wine or any other simulare programe?

For example, I open the other HDD via Linux, and open the exe file then the game loads from the other drive. Could this work with out wine (or simulare software)?

---

### Post by aptget on 2006-08-03
> **bobleny said:**
> I will have Ubuntu on one HDD and XP Home on the other. Would it be posible to run my windows apllications with out leaveing the comfort of my linux without wine or any other simulare programe?

For example, I open the other HDD via Linux, and open the exe file then the game loads from the other drive. Could this work with out wine (or simulare software)?

Exe files aren't able to be loaded without Wine, but the idea of opening them from a Windows drive in Ubuntu could work. I don't think .exe support will ever be included as it would amount to questions of why a certain .exe didn't open and such.

---

### Post by bobleny on 2006-08-03
I think that its best if Linux didn't open exe files as it would be a security problem and make it more susceptible to viruses. All I really want to do is run a Microsoft game from windows in Linux with out wine. I don't know if it can though. That's why I'm asking... :D

---

### Post by cutterjohn on 2006-08-04
Here's your answer then:
No, you cannot run windows applications under linux without wine.

Other Options:
If there's a linux ported version of the executable then you would be able to run it under linux.  e.g. various versions of Id games(they usually provide linux versions of the executable, or at least they used to...), IIRC bioware has(had?) linux versions for some of their games...

OW if it's an older game the game's source may have been released and someone else ported it to linux, or updated the game, e.g. Doom, Quake, Quake 2, Marathon, etc.

Also some even older games like the infocom text adventures, Sierra graphics adventure games, Lucas studios games, etc. have linux interpreters. (Versions of these and many more(e.g. various console emulators) ARE available in the ubuntu repos, or at least universe & multiverse...)

even more options:
dosbox for DOS games (you'll likely need a fairly fast machine to run game targetted at 250MHz or faster DOS machines)

VMware (or some other virtualizer) to run an instance of windows under linux in which you can run your apps/games just like you had booted into windows in the first place...

i.e. go at least do a little googling once in a while.

---

### Post by forrestcupp on 2006-08-11
> **cutterjohn said:**
> 

i.e. go at least do a little googling once in a while.

Maybe you should too, and you'll find out that vmware doesn't really handle games all that well.

---

### Post by Ramses de Norre on 2006-08-11
It does not matter whether the exe is located on a drive with windows installed or not, you can only run one operating system a time (it might be sort of possible to run more than one using parallels but that does not matter here) and thus if you run linux you will run the exe with linux, independent were it is located and thus you'll need something like wine..

---

