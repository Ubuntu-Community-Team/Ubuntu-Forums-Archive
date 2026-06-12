---
title: "Warzone 2100 problem - PhysicsFS"
date: 2014-02-06
forum: Gaming &amp; Leisure
---

### Post by Portaro on 2014-02-06
WHen i launch the game a few minutes always crashes.
When i try launch a game via terminal he works and give this message-

> info    |09:02:47: [realmain:1133] Using /home/joao/.warzone2100-3.1/logs/WZlog-0206_210247.txt debug file
error    |09:02:47: [check_Physfs:566] You have PhysicsFS 2.0.2, which is  buggy. You may experience random errors/crashes due to spuriously  missing files.
error   |09:02:47: [check_Physfs:567] Please upgrade/downgrade PhysicsFS to a different version, such as 2.0.3 or 2.0.1.
popup    |09:02:49: [screenInitialise:187] OpenGL GLSL shader version 1.20 is  not supported by your system. Some things may look wrong. Please upgrade  your graphics driver/hardware, if possible.

how to update this PhysicsFS-

I use Ubuntu 12.04.

---

### Post by oldrocker99 on 2014-02-06
What is your video card? Try this:

lspci | grep VGA

and post the results.

---

### Post by Portaro on 2014-02-07
> joao@VIA:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV280 [Radeon 9200 PRO] (rev 01)
joao@VIA:~$ 

Thanks for your help.

---

### Post by Portaro on 2014-02-07
I opt to downgrade to 2.3.8 version and works, but and then have a but behind a but - I remember that I have this problem on 13.04 and 13.10, and this problem can affect other people.
In the case of this great game if is possible probably is good make a local site to maintain deb packages for users, is probably with new releases and many people uses old cards the problem appears more times, and maybe if they have a local to down old deb packages and files of config -music and data the game can be works for more people.

Thanks for your help.

[Solved]

---

