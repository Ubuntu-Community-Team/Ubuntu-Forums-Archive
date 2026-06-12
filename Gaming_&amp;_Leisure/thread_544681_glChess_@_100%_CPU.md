---
title: "glChess @ 100% CPU"
date: 2007-09-06
forum: Gaming &amp; Leisure
---

### Post by marx2k on 2007-09-06
I am running glChess in 2D and any time I run ti in Fiesty, it runs @ 100% CPU (on a 2 CPU system (AMD64), it takes 100% of one of the CPUs).

Is it having the same effect for anyone else here?

Here is 'ps ux | grep chess':
marx2k    8726  0.8  2.1  43476 22400 ?        S    15:55   0:00 python /usr/games/glchess
marx2k    8729 99.2  0.1  10940  1528 pts/0    RNsl+ 15:56   1:42 gnome-gnuchess --xboard

---

### Post by tgalati4 on 2007-09-06
You must be an excellent player!

---

### Post by marx2k on 2007-09-06
:lolflag:
Not until the CPU heats up enough to fuse with the heatsink ;)

---

### Post by geek_Man on 2007-09-06
I have the same problem here... and I'm *bad* at it.

---

### Post by DoktorSeven on 2007-09-06
GNUchess (the chess AI)  takes up the CPU to think.  This is normal.

---

### Post by tgalati4 on 2007-09-06
>sudo apt-get install htop

>htop

Run it along side chess and see how it behaves with the rest of your system.  I know that it is CPU intensive.  If you get proper scheduling, then other tasks will swap in and out of the processor queue.  You can always nice it, that will give you a more responsive desktop, but it will still gobble up 100% of the processor.

Watch it for a while and you will see that it is probably behaving normally.

---

### Post by marx2k on 2007-09-13
I can understand GnuChess taking 100% of the CPU to think, but it must be thinking long and hard because even when it's not doing anything (when it's my turn), it's still eating 100%.

If Kasparov was doing this at tournaments, he would have a cerebral hemmorhage :D

---

### Post by DoktorSeven on 2007-09-13
gnuchess thinks while it's your turn, just like a real chess opponent.  You have to get used to the fact that most, if not all games take up 100% CPU.

---

### Post by Maxei on 2008-08-16
Yeah I know this thread is a few months old but the problem is present. I don't understand. Gnuchess takes all the CPU while it does nothing. Absolutely. THat is wierd. Just fire up xboard and stays idle. but CPU rockets up to 100%. My motherboard (after a while) then starts to sound the alarm for heating (set at 60 Celsius I guess). My PC has an AMD 64 X2 5000+ cpu. Its a heck good cpu man. Before, I had an athlon running at 1 GHZ, and never saw this problem. What the heck could be the problem? Only when gnuchess checks mate the opponent, then cpu use drops to zero%. Reseting brings it back to 100% CPU use. I mean, I dont beleive that gnuchess needs all the cpu just to stay iddle. Is there any setting to decrease cpu use by gnuchess? Looks like programs runnin in linux are becoming fat hogs, like those running in windows. I wonder where is that philosophy that in  linux you could use older hardware? I have the best sytem ever I had and yet seems not better than the oldie. like walking backwards towards microsucks style.

---

### Post by tr1sth3t on 2010-11-22
> **Maxei said:**
> Yeah I know this thread is a few months old but the problem is present. I don't understand. Gnuchess takes all the CPU while it does nothing. Absolutely. THat is wierd. Just fire up xboard and stays idle. but CPU rockets up to 100%. My motherboard (after a while) then starts to sound the alarm for heating (set at 60 Celsius I guess). My PC has an AMD 64 X2 5000+ cpu. Its a heck good cpu man. Before, I had an athlon running at 1 GHZ, and never saw this problem. What the heck could be the problem? Only when gnuchess checks mate the opponent, then cpu use drops to zero%. Reseting brings it back to 100% CPU use. I mean, I dont beleive that gnuchess needs all the cpu just to stay iddle. Is there any setting to decrease cpu use by gnuchess? Looks like programs runnin in linux are becoming fat hogs, like those running in windows. I wonder where is that philosophy that in  linux you could use older hardware? I have the best sytem ever I had and yet seems not better than the oldie. like walking backwards towards microsucks style.

Refer to post #[**8**]("http://ohioloco.ubuntuforums.org/showpost.php?p=3359435&postcount=8").

---

### Post by Sockerdrickan on 2010-11-22
Maybe it's running mesa 3d (software opengl)

---

### Post by efikkan on 2010-11-23
100% CPU load is comletely normal and is due to how the main loop in the game is designed.

---

### Post by &lt;&lt;joe&gt;&gt; on 2011-02-01
I am having a similar experience on my computer phenom x4 one of the cores is maxed. I could understand that maybe the chess engine would be eating all of this up, but I am playing my father on one computer. This leads me to believe that the gui is the thing eating it up.
This can be easly tested use a differnt gui with the same chess engine(my dad). 
Then I will also test it with the gnu engine.
To everyone saying the op just hast to deal with it, it does seam unreasonable for the cpu to be maxed. I mean what would the chess engine do build the entire game out to the end. This would eat so much ram up ... and its not. I smell a infinite loop some where.

---

### Post by lisati on 2011-02-01
May the thread rest in peace.

---

