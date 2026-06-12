---
title: "Some 3D games work and others don't"
date: 2006-01-15
forum: Gaming &amp; Leisure
---

### Post by th3t1nm4n on 2006-01-15
I can run Quake 3 Arena, Wolfenstein:ET, and Cube with no problems, but if I try to run Nexuiz or DigitalPaint2 they run in slow motion. (which I find strange because DigitalPaint2 is based off of Quake 2, and Quake 3 runs fine) e.g. when I shoot there is at least a 4 second delay and the shooting is done in slow motion, movement is way off and in slow motion too, as is going through menu's with my mouse.

I have also found that with [Jake2]("http://bytonic.de/html/jake2_webstart.html"), "webstart jake2 with jogl11" has this lag problem, but "webstart jake2 with lwjgl" doesn't, it runs fine.

I am running Ubuntu 5.1, and have everything up to date.

I get this SAME problem on my desktop computer which has an nVidia GeForce card, but I don't know exactly which GeForce it is running.

0000:00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

Thanks for any help you may find for my situation. :KS

---

### Post by Mr_Grieves on 2006-01-15
You can't compare totally diffrent games and versions like that. Just because Game 1 works on Wine 0.x.x does not mean that Game 2 must work on Wine 0.x.x. It's every game/version for itself I'm afraid.

You have to troubleshoot every game/version for itself. For example: If you are having a problem with DigitalPaint2, search on the web/winehq/maillists on how to get that game to work.

---

### Post by th3t1nm4n on 2006-01-15
I listed theses games simply to state which ones work and which ones don't, because the ones that don't all share the same problem it looks like, and I'm not using wine, they are all linux native games.

Quake 3 Arena and Wolfenstein:ET run on the Quake 3 engine, and DigitalPaint2 and Jake2 run on the Quake 2 engine, so those games are relative to eachother.

[EDIT] The DigitalPaint forums show that some people running the Linux version experience this problem and others don't, I got the same results when looking into Nexuiz, which wasn't much help.

---

### Post by slux on 2006-01-15
Jake2 and Quake 2 are fundamentally different as Jake2 is a reimplementation in Java so they very likely do not have comparable performance. The same goes for Digital Paint 2 if it has enhanced the Q2 engine significantly. (Nexuiz could be said to be based on the Q1 engine but certainly has come far from that)

With that being said, how's your sound when this slow-motion thing is in effect? Have you tried without it? Some alsa drivers and games don't like each other and if you also have "slow-motion" sound that might actually be the cause.

---

### Post by th3t1nm4n on 2006-01-15
The audio crackles and is divided into pieces that play out slowly, I just tried with audio disabled, but it was the same slow response.

---

