---
title: "Huge X.org memory usage?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by linj on 2005-12-14
When I'm using the computer for some period of time, typically with Azureus, Amarok, and GAIM open and using Firefox for surfing, X.org and friends take up huge amounts of memory. 

After about 5 hours of uptime today, I reached a new record of **926MB** ram being eaten away by Xorg and another 311MB of swap space. Thus, in total, (firefox somehow using another 500MB and java, 400MB), I have no ram free and have 550MB swap used and 700MB free. Is this typical? 

I haven't really noticed this until a day ago, when I was talking to my friend about memory usage, and opened up the KDE ProcessTable to check. Previously, this never happened on Gentoo, but now I'm scared. 

Specs:
2x Opteron 244
2x 512MB Corsair ECC = 1GB ram

Any comments are appreciated!

---

### Post by yustabeme on 2005-12-14
[QUOTE=linj]When I'm using the computer for some period of time, typically with Azureus, Amarok, and GAIM open and using Firefox for surfing, X.org and friends take up huge amounts of memory. 

After about 5 hours of uptime today, I reached a new record of **926MB** ram being eaten away by Xorg and another 311MB of swap space. Thus, in total, (firefox somehow using another 500MB and java, 400MB), I have no ram free and have 550MB swap used and 700MB free. Is this typical? 

I haven't really noticed this until a day ago, when I was talking to my friend about memory usage, and opened up the KDE ProcessTable to check. Previously, this never happened on Gentoo, but now I'm scared. 

Specs:
2x Opteron 244
2x 512MB Corsair ECC = 1GB ram

Any comments are appreciated![/QUOTE]

I have I gig ram; here's output of free, displaying memory in mb

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1012        995         16          0        175        356
-/+ buffers/cache:        463        549
Swap:         1027         12       1015

I paid for all of my memory, so I'm glad Linux takes full advantage of it. OTOH, you might have a memory leak, it does happen. But the -/+ buffers/cache | free entry is telling (~ 16 + 175 + 356)

according to top (kde system guard | process table uses top I believe):

Mem:   1036456k total,  1019880k used,    16576k free,   180464k buffers
Swap:  1052216k total,    12540k used,  1039676k free,   363892k cached

which on the surface paints a goomier picture. Take a look at KDE system guard | system load | physical memory. Also, if you're only looking at VmSize (kde), that correlates to this entry in man top:

VIRT  --  Virtual Image (kb)
The total amount of virtual memory used by the task.  It includes all code, data  and  shared  libraries  plus pages that have been swapped out

so, here's a snapshot of my Xorg entry from top (typing "h" while it's runnuing shows how to customize)
  
PID USER      VIRT  RES  SHR %MEM SWAP CODE DATA COMMAND
 9840 root      311m  57m 7360  5.7 253m 1548  44m Xorg

5.7% (%MEM of total physical) doesn't look so bad given the VIRT and SWAP numbers...forgive me if all this is obvious to you.

BTW, someone else mentioned Azureus being a memory hog- that's my experience also, which is why I use another BT frontend.

---

### Post by rattking on 2005-12-14
I have recently noticed that Azureus/java are causing a huge increase in X.org memory useage untill all swap is filled and the system dies hard..
keeping the torrent tabs closed and Azureus in the tray seems to help the runaway memory useage

also don't worry about disk cache.. linux is just trying to keep memory full to avoid hitting the hard disc more then need be

---

### Post by GeneralZod on 2005-12-14
[QUOTE=rattking]I have recently noticed that Azureus/java are causing a huge increase in X.org memory useage untill all swap is filled and the system dies hard..[/QUOTE]

Yep - this has happened to me, several times with the exact same symptoms (i.e. it's not the azureus process that gets bloated, but xorg, and xrestop shows that azureus is using up tons of graphical resources).  It usually happens completely out of the blue - azureus can be left running overnight, but then suddenly while I'm working a few hours in, the system will suddenly start thrashing madly and the mouse pointer becomes increasingly less responsive.  If I'm quick, I can usually shut down azureus just in time, at which point everything is fine; otherwise, it's either a hard reboot or 10 minutes of disk-thrashing until the system registers the CTRL+ALT+BACKSPACE and finally kills X.

---

