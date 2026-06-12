---
title: "open arena problem"
date: 2008-01-02
forum: Gaming &amp; Leisure
---

### Post by Falc7 on 2008-01-02
Hi
I have installed open arena using the add/remove programs. However after around 15mins the game minimises from whole screen to only part of the screen, and i can't maximise it or do anything else. It is basically completely unresponsive. However the game window is still running, and i still get shot at!
Anyway i tried control, alt and delete but the comp did nothing? What can i do?

---

### Post by BreathEasy on 2008-01-02
It might be due to Compiz Fusion, since I've had a few problems myself when playing Urban Terror with it running. Try disabling it before playing Open Arena. An easy way to do so:

Press Alt+F2
Type in: **metacity --replace**

Run that, and then try running OpenArena. If you don't have any issues, then your problem is solved. Compiz will return the next time you log in, or you can restart it manually by doing the Alt+F2 thing again and typing in **compiz --replace**.

---

### Post by brunolabs on 2008-01-17
I also have a OA problem. I can't connect to any server and the following message shows up "Invalid Game Folder". I installed it normally through the Add/Remove Applications.

What can I do?

---

### Post by markyb86 on 2008-01-17
> Hi
I have installed open arena using the add/remove programs. However after around 15mins the game minimises from whole screen to only part of the screen, and i can't maximise it or do anything else. It is basically completely unresponsive. However the game window is still running, and i still get shot at!
Anyway i tried control, alt and delete but the comp did nothing? What can i do?

Disable your screensaver before you play any fullscreen games, or movies

> I also have a OA problem. I can't connect to any server and the following message shows up "Invalid Game Folder". I installed it normally through the Add/Remove Applications.

What can I do?

the OA in the repos is old. download the newest version from [http://www.getdeb.net/category.php?id=3](http://www.getdeb.net/category.php?id=3) and you will be squared away. you need openarena and openarena-data, and you can install openarena-server  only if you want.

---

### Post by DrMega on 2008-01-17
> **Falc7 said:**
> Hi
I have installed open arena using the add/remove programs. However after around 15mins the game minimises from whole screen to only part of the screen, and i can't maximise it or do anything else. It is basically completely unresponsive. However the game window is still running, and i still get shot at!
Anyway i tried control, alt and delete but the comp did nothing? What can i do?

I've had this problem. I'm fairly sure it is a Compiz thing. What I've done is installed Xubuntu Desktop, and I just switch session to Xfce when I plan to play any games.

---

### Post by networkthinking on 2008-01-18
BreathEasy  - that worked for me!

---

### Post by agtownz on 2008-01-18
This might also be caused by the Weather Widget, unless it's been fixed now.  I had no idea why my apps like Nexuiz and Cube were going into windowed mode to a quiarter of the screen after 10 mins, only to find that after disabling auto update on Weather Widget did the trick.  If you're running it, it's worth a try.

---

