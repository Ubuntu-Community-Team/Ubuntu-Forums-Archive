---
title: "League of Legends on Ubuntu"
date: 2014-08-05
forum: Gaming &amp; Leisure
---

### Post by cgolan on 2014-08-05
Hey all, hoping for some help here !

Right so here is my problem :

I am currently a semi professional League of Legends player (ranked Challenger solo queue and Challenger Team) and i crashed my PC a few days ago...
The thing is i need to be able to play League on a regular basis, as me and my team are aiming for Europe Challenger Series next season. I tried installing League of Legends on my computer currently running Ubuntu 12.04 with Play on Linux (last version updated through apt-get in terminal) and Wine (1.6). After following many (many) guides, i managed to install the game. But now i have a problem when i launch it through the PoL program. The game starts to launch and then just stops, and the League of Legends logo goes from bright colours, to darker ones... I have installed Adobe Air (again through PoL) and even tried leaving it over night, thinking it might need some time. But nothing helped... 
I as wondering if anyone else had ever encountered a similar problem, or if anyone knew how to fix this ? 
Again i need to be online as much as possible for practice with my team, so a fast response would really be appreciated.
I must admit to you i am a total noob when it come to using Linux, having been used to windows...

Thanks in advance for reading and for your answers ! :)

---

### Post by oldrocker99 on 2014-08-05
OK, the free program PlayOnLinux does have an installation script (which is customized for each game) for LoL, but the notes for it do warn that there's a bug with the shops, and it's a big one: a blank screen. Now, [https://appdb.winehq.org/objectManager.php?sClass=version&iId=19141](https://appdb.winehq.org/objectManager.php?sClass=version&iId=19141) shows the way to get it running on your system, which involves a certain amount of terminal commands, which you can cut and paste, a line at a time, into a terminal. They're very complete, and updated to 14.04 (so you'll **need** to substitiute **Precise** for **Trusty**, capitalized or not, as it's shown on that page.

And, before you start, do this:
```
sudo apt-get install build-essential
```
This will give you all the necessary compilers (gcc, g++) on your system, which you'll need before you start the instructions on that page. This method will work, although I haven't tried it, but winehq.org is a trustworthy site.

And good luck! You're jumping off the deep end, but we're here to help.

---

### Post by sffvba[e0rt on 2014-08-05
IMO if you are going to be playing LOL competitively use Windows.  There is no official support for other OS's and it doesn't work flawlessly under Linux.

---

### Post by mastablasta on 2014-08-06
> **not found said:**
> IMO if you are going to be playing LOL competitively use Windows.  There is no official support for other OS's and it doesn't work flawlessly under Linux.
Actually they do have a Mac version now. so that could be an option as well :P


but seriously this advice is actually a very good advice. you can run it on XP. the problem with these online games via wine is that they often get patches. LOL get's a major one once a month at least. so even if it now works well on wine it might not work after update. which is why - run windows apps on windows.


or prepare to loose a few nerves and never have them run properly or do plenty of work arround to even get them to run. 

I just finished Morrowind install and even if that one is platinum.... well --> game crashes when changing keys (basic functionality IMO), conversation menus are always minimised for some reason, some excellent mods do not work at all. and that's a game with platinum rating. while LOL have a notch lower rating at GOLD & with latest development version of wine.

---

### Post by jakub11 on 2014-08-10
IMO you should install Windows ASAP if You still want to play LOL well. Linux has totally different gameflow as for me. I wanted to totally move to Linux, because of great free soft, but I'm a gamer too - Windows to this moment ;)

---

### Post by oldrocker99 on 2014-08-10
I'm a gamer as well, and I deleted my annoying, vulnerable, porous Windows partition so I have more room for my Steam games. I certainly have enough games (200+) in my Steam library (most bought on sale; I'm not rich) to not miss Windows one tiny bit. I certainly don't miss the malware.

---

