---
title: "World of Warcraft freezes on loading..."
date: 2005-10-15
forum: Gaming &amp; Leisure
---

### Post by St3althcAt on 2005-10-15
Hello, I have recently installed Ubuntu 5.10, I have the latest ATi drivers from the Ubuntu repositories and I've installed Cedega 4.4.1 from the .deb packages. I used this version of Cedega on Ubuntu 5.04 and managed to sucessfully play World of Warcraft. Now I start the game, put my username and password, choose character and hit the "Enter World" button. When the blue loading bar, reaches the end, instead of entering the game world, it keeps in the same screen, disk activity stops, mouse moves, music continues and the only way to get out is using CTRL+ALT+BACKSPACE to shutdown x. Does anyone know what is the problem? Anyone know the solution?

Thank you for the atention.

Info:

Ubuntu 5.10 i386;
ATi Drivers 8.16.20 from repositories;
Cedega 4.4.1;
World of Warcraft with patch 1.8.0 installed.

---

### Post by KingBahamut on 2005-10-15
Sounds like an acceleration problem.  Are you getting decent acceleration out of glxgears or any other related glx/opengl application?

---

### Post by St3althcAt on 2005-10-15
Well, that has been a problem I've noticed since I installed Breezy (yesterday).
fgl_glxgears works normal, less frames than on Hoary but works, about 397 frames per second, but glxgears is terribly slow. It doesn't even appear the frame rates on the console. Maybe that is the problem.

---

### Post by KingBahamut on 2005-10-15
bad ATI driver install most likely. 

Did you use the ATI installer or grab them from the Repositories?

---

### Post by St3althcAt on 2005-10-15
Repository install. Should I try the ones from ATi website or do you have other recomendation? Already reinstalled the drivers an it's all the same.

---

### Post by St3althcAt on 2005-10-15
Since this looks like a 3D problem, maybe I'm moving this topic to the desktop support.

Link: [http://www.ubuntuforums.org/showthread.php?p=414686#post414686](http://www.ubuntuforums.org/showthread.php?p=414686#post414686)

---

### Post by St3althcAt on 2005-10-15
Glxgears problem solved, but WoW problem persists. Any ideas?

---

### Post by seethru on 2005-10-15
what winver are you emulating?

---

### Post by Anchovie on 2005-10-15
Hey, I am having the exact same problem, emulating WIndows XP. However when I start a new character the game loads, but when I'm trying to log into one of existing character sits in Orgrimmar, I get the same stuck-in-loading-screen problem.

---

### Post by St3althcAt on 2005-10-16
I'm installing the game from Linux, instead of copying it from the Windows partition (waiting for a friend to send me a patch though). If it works, I'll report here, if it doesn't, I'll report here too. I'm also going to try and execute it with Windows Version set to Windows 98, maybe it helps.

---

### Post by wakingrufus on 2007-08-08
I am having this same problem.  it happens about 90% of the time i try to log in to orgrimmar and hall of legends. all my other characters can log in fine

---

