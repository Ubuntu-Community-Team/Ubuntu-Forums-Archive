---
title: "playing racer in ubuntu"
date: 2005-11-23
forum: Gaming &amp; Leisure
---

### Post by nuttyrave on 2005-11-23
Hello,
I am enquiring if anybody has managed to get the excellent "[racer]("http://www.racer.nl")" game to work with ubuntu? I have just installed it using Loki's installer:
[IMG]http://www.geocities.com/nuttyrave/img/racer.png[/IMG]

 and this is what I get:
```
$ racer 
./bin/racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

1_Has anybody (with ubuntu :KS ) gotten it to work?
2_Do you think coming releases of the game will move away from compatibilty libraries?

Cordially,
Donan Raven

---

### Post by AlexMartinius on 2005-11-23
libstdc++6 is available through apt (sudo apt-get install libstdc++6). And perhaps libc6 is the name of the other one in apt. I'm not sure, not that familiar with libraries, you could give it a try.

---

### Post by nuttyrave on 2005-11-23
WOW - this is a fast reply - the missing lib is acquired through the
compat-libstdc++
package...but where do I get it? No results in synaptic for example. And I cannot find the correct version .rpm  - which maybe I could in turn "alien".

D.

---

### Post by AlexMartinius on 2005-11-23
[QUOTE=nuttyrave]WOW - this is a fast reply - the missing lib is acquired through the
compat-libstdc++
package...but where do I get it? No results in synaptic for example. And I cannot find the correct version .rpm  - which maybe I could in turn "alien".

D.[/QUOTE]
I misread, thought it missed 2 libraries and one of 'em was libstdc++6. I did a quick search on google and found this: [http://ubuntuforums.org/showthread.php?t=1879](http://ubuntuforums.org/showthread.php?t=1879)

Searching for libstdc++2.10 with apt does give some results, one of them is libstdc++2.10-glibc2.2 (and a debug and developer version). Perhaps the glibc2.2 package would do the trick. Might be worth a try, I read it would be the package you need on: [http://www.atitd.net/forum/archive/index.php/t-8002.html](http://www.atitd.net/forum/archive/index.php/t-8002.html)

---

### Post by nuttyrave on 2005-11-23
Eureka!

---

### Post by charlieg on 2005-11-24
Hopefully, with good community support, games like [VDrift](http://www.vdrift.net) and [TORCS](http://torcs.sourceforge.net) will get up to speed ('scuse the pun) with Racer.

VDrift is already a lot of fun, by all accounts.

---

### Post by nuttyrave on 2005-11-24
Maybe they are also more controllable games for the occasional player. Racer is quite hard to maneuver with a keyboard, and is only meant for use with a fully-analog steering wheel.

---

### Post by Biased turkey on 2005-11-24
[QUOTE=nuttyrave]Eureka![/QUOTE]
What do you mean "Eureka" ?
Does it mean that you found the missing libstdc++2.10-glibc2.2 library, or that you have atualy Racer running at full speed ?
Please give more details. Will you post a "Racer HOWTO" ?

---

### Post by Biased turkey on 2005-11-24
[QUOTE=charlieg]Hopefully, with good community support, games like [VDrift](http://www.vdrift.net) and [TORCS](http://torcs.sourceforge.net) will get up to speed ('scuse the pun) with Racer.

VDrift is already a lot of fun, by all accounts.[/QUOTE]


I love racing games, 95% of my purchased Playstation and PC games are in the  racing category , Playstation2: Granturismo, Enthusia  on PC Richard Burns Rally, Grand Prx legends and F1 Challenge).
I knew about Torcs  and Racer, but not about VDrift. It looks excellent.
How many of those 3 games are running perfectly with Ubuntu ?

---

