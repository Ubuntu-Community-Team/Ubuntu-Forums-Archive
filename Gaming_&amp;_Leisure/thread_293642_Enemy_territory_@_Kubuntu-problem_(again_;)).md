---
title: "Enemy territory @ Kubuntu-problem (again ;))"
date: 2006-11-05
forum: Gaming &amp; Leisure
---

### Post by Xantos on 2006-11-05
Ok folks, 

I installed ET @ Kubuntu 6.10 and I had a few problems(not running in full-screen, no sound,...).

Thnx to this forum I solved allready a lot of problems, now I still got 1 problem: when I start the game, it askes every time to make a new profile.
If I search after etconfig.cfg or something like that I can't find it, same sh*t with searching after profile :???: 
A bit weird I think :p , or am I wrong?

Grtz and thnx in advance


Xantos

---

### Post by babooka on 2006-11-05
May be "ET" directory does not have the correct permissions and the game can't save the profile?

Do map downloads work fine?

---

### Post by Xantos on 2006-11-05
Godd*mn, now you're saying it, those permissions :eek: :D
You'll know more tomorrow, thnx again.

---

### Post by Xantos on 2006-11-07
Just want to say that it works now, thnx:-D

---

### Post by dannyboy79 on 2006-11-07
is this game free, where can i get it from? do you have to run it thru wine?

---

### Post by Xantos on 2006-11-07
Yeah it's free, you don't have to run it thru wine, there's a linux version available at [http://games.activision.com/games/wolfenstein/](http://games.activision.com/games/wolfenstein/)

---

### Post by dannyboy79 on 2006-11-07
> **Xantos said:**
> Yeah it's free, you don't have to run it thru wine, there's a linux version available at [http://games.activision.com/games/wolfenstein/](http://games.activision.com/games/wolfenstein/)

that's only a demo, and if I wanted the game I have to pay for it?
If it's free can you please post where you got it or i'll send you a pm with my ftp server location so you can upload the .deb to me if you could. If it's free that is, I don't want anything pirated and I am being serious. Ubuntu is very serious about Pirated stuff so only if it's suppose to be free.

---

### Post by lotusleaf on 2006-11-07
> **dannyboy79 said:**
> that's only a demo, and if I wanted the game I have to pay for it?
If it's free can you please post where you got it

To quote from: [http://en.wikipedia.org/wiki/Wolfenstein:_Enemy_Territory](http://en.wikipedia.org/wiki/Wolfenstein:_Enemy_Territory)

> "Enemy Territory was originally planned to be released as a commercial expansion pack to the popular FPS Return to Castle Wolfenstein. However, due to problems with the single-player aspect, the multiplayer portion was released on May 29, 2003 as a free standalone game. In early 2004 the source code for the game logic (not the game engine) was released to the benefit of its modding community."

There are downloads available here:
[http://www.3dgamers.com/games/wolfensteinet/downloads/](http://www.3dgamers.com/games/wolfensteinet/downloads/)

The Linux version 2.60 ([ReadMeFile](http://www.3dgamers.com/dlselect/games/wolfensteinet/et-linux-2.60.x86.txt)):
[http://www.3dgamers.com/dlselect/games/wolfensteinet/et-linux-2.60.x86.run.html](http://www.3dgamers.com/dlselect/games/wolfensteinet/et-linux-2.60.x86.run.html)

And hundreds of maps to download for Enemy Territory:
[http://www.new-etmaps.de/](http://www.new-etmaps.de/)

Punkbuster page (you should enable Punkbuster):
[http://www.evenbalance.com/index.php?page=support-et.php](http://www.evenbalance.com/index.php?page=support-et.php)

Punkbuster PBSETUP Utility:
[http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)

P.S.: Xantos, I avoided any/all problems with Enemy Territory by installing it in $HOME as a user rather than it's installed by many on other distributions as root. I don't like the idea of installing it in $HOME but that's what I did in Ubuntu (to avoid the issues with video and/or sound, profile, punkbuster). Whether or not this is something you wish to attempt if you haven't already is up to you, I don't recommend it, but it worked for me.

---

### Post by Xantos on 2006-11-09
I still got one tiny problem:
When I want to join a server, the maps or whatever you need to get on that server, don't want to download.

Grtz

---

### Post by babooka on 2006-11-09
umm ... Permissions? :)
is it installed in your $HOME directory? if so, do
chmod -R u+rw ~/.etwolf

---

### Post by Xantos on 2006-11-09
Tss again those permissions :D

I installed ET in /home/xantos/games/enemy-territory
So I open de terminal and type:
cd /home
Then I type:
chmod -R u+rw ~/.etwolf

I start ET but it's still the same.
I can see the file-name which I need to download and I can see how big it is. Under "estimated time left:" I get estimating.
If I don't need to download anything (standard maps), the game is loading, but suddenly I disconnect and I get: "cannot write to hunkusage.dat" :-k  

Help plz

---

### Post by hopstah on 2006-11-10
instead of typing ```
chmod -R u+rw ~/.etwolf
```you need to change the modifications of the directory where you installed it.  for you it should be ```
chmod -R u+rw /home/xantos/games/enemy-territory
```the other user must have installed his enemy territory game into a ~/.etwolf directory, and that is why he posted that directory.

---

### Post by Xantos on 2006-11-11
Oh, thnx it worked! ;)

---

