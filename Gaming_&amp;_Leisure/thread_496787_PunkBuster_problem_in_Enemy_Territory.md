---
title: "PunkBuster problem in Enemy Territory"
date: 2007-07-09
forum: Gaming &amp; Leisure
---

### Post by GNUtoo on 2007-07-09
i have the following messages in enemy territory's console at startup(pressing ~ at startup):
PunkBuster Client: PunkBuster Client: (V1.152 | A0) Ebavked
PunkBuster Client: Gane Version [ET 2.60b linux-i386 May 8 2006]

_what's my problem:_
when i connect to a server it is fine until i join the game and play a bit
then i have this error:
Server Disconnected - has been kicked via PunkBuster (for 1 minute) ...
Violation (GAME INTEGRITY) #20004


_how did i install it:_
i followed this howto:[http://ubuntuforums.org/archive/index.php/t-5246.html](http://ubuntuforums.org/archive/index.php/t-5246.html)
i downloaded the enemy territory
i downloaded the zip file for upgrading to the b version
then i followed the PunkBuster update procedure

---

### Post by AthlonMDK on 2007-07-24
This solved the issue for me:

While playing 2 minutes you get pberror #20004 and you get disconnected.
goto $ET map/pb
cp pbweb.x86 /home/%user%/.etwolf/pb
cd /home/%user%/.etwolf/pb
./pbweb.x86
this is updating Punkbuster and after it complete's run et. 

I got it from another howto but could not find it.

Jope it will solve the issue for you!

---

