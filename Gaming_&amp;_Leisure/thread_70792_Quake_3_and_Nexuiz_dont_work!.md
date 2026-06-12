---
title: "Quake 3 and Nexuiz dont work!"
date: 2005-10-01
forum: Gaming &amp; Leisure
---

### Post by Floker on 2005-10-01
Hi

I installed Quake3 and Nexuiz and they dont work.

The Screen gets black, if i put the mouse in the lower right corner, i can scroll over the screen - the games are only a black box at the upper left corner.

Thats it, nothing changes if i just wait.

The last message of quake3 is "initializing sound"

Greets
Floker

(maybe it has something to do with my other thread here)

---

### Post by Quirky on 2005-10-01
In your other thread you mention a Java program. Java programs that use sound tend to make the Java VM open the sound device and never close it.

Open the menu System Tools -> System Monitor  and see if there is a java program running. If so kill it and try Nexuiz again. Read the HOWTOs on sound if this is the problem.

[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

---

