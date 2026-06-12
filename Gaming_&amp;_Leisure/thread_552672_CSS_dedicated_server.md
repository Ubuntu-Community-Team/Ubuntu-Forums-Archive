---
title: "CS:S dedicated server"
date: 2007-09-16
forum: Gaming &amp; Leisure
---

### Post by Unions on 2007-09-16
my CS:S dedicated server is in /home/lucas/srcds_l

When i do *./srcds_run -game cstrike +map cs_office +maxplayers 16*
(which should run a counter strike source server on the map cs_office with a maximimum of 16 players)
I get 
[I]Auto detecting CPU
Using Amd optimised binary.
Auto-restarting server on crash
AppFramework : Unable to load module bin/vphysics_1486.so!
Unable to load interface VPhysics031 from bin/physics_1486.soSun Sep 16 18:48:11 CDT 2007: Server quit[/I]

Yes i am running a amd processor

---

### Post by Unions on 2007-09-16
I also seem to be unable to run srcds_amd in the same directory

---

### Post by Ash96 on 2007-09-17
I am having the same problem. I tried Googling it I only got one thing in English and I couldn't understand the solution if there even was one. I'm using an AMD CPU too. The version of Ubuntu I'm running is Feisty Server Edition with an Xubuntu environment.

---

### Post by Ash96 on 2007-09-18
I found the solution on the [official Steam forums]("http://forums.steampowered.com/forums/showthread.php?t=597774"). You have to use the verify_all flag with the update tool.

---

