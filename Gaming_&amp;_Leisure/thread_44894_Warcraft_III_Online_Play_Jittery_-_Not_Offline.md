---
title: "Warcraft III Online Play Jittery - Not Offline"
date: 2005-06-28
forum: Gaming &amp; Leisure
---

### Post by GML3G0 on 2005-06-28
I have installed Warcraft III: TFT under Cedega and offline everything runs smooth, even when I have 10+ other CPUs playing. Playing online is a different story. It tends to skip around. Like the game will play fine, then pause for a second and continue. Four seconds later, it will pause for a second again, and so on.

Is this possibly a FireStarter conflict, blocking port 6112? I don't even know if when I installed FireStarter if it put a startup script. How can I check?

---

### Post by Fexx on 2005-06-28
If you think its a firewall problem, you could do sudo iptables --flush. That will wipe the firewall policy list.

But; Firestarter by default doesnt block anything.

Im pretty sure 6112-6119 = ports for custom game, like you hosting it.

---

### Post by gil-galad on 2005-06-28
I doubt it has anything to do with the firewall.  Sounds like simple lag to me.

---

### Post by GML3G0 on 2005-06-29
Not lag. I don't get this under Windows. 3.0 Mbps low ping connection.

---

### Post by GML3G0 on 2005-07-01
Bump.

---

### Post by zer on 2005-07-16
I have the same problem here.
In the console, every time it hangs i get: "WARNING: wait4 timed out"

I would be appreciated for any ideas or tips that could help. :-)

The System is a 3600+, 512 MB and an ATI Radeon 9600. In Windows, everything works fine.

---

### Post by Jet2k5 on 2005-07-16
I have a friend who just discribed the same problem to me.  He says on Linux it's very very jerky, but on windows it's fine.  You guys should check out the [transgaming forums](http://www.transgaming.org/forum/) and see if there might be a fix for this.

---

### Post by Gnobody on 2005-07-17
[QUOTE=Jet2k5]I have a friend who just discribed the same problem to me.  He says on Linux it's very very jerky, but on windows it's fine.  You guys should check out the [transgaming forums](http://www.transgaming.org/forum/) and see if there might be a fix for this.[/QUOTE]
 DMA not enable on your cd drive? hdparm it and find out!  Also, try running in WarCraft in opengl mode by adding -opengl after the War3.exe when launching it.  This will improve performance.

---

### Post by zer on 2005-07-20
With a new version of cedega (4.4), everything works fine.
Thanks for the help :-)

---

