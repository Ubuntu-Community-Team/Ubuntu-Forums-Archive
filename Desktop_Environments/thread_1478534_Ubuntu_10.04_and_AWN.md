---
title: "Ubuntu 10.04 and AWN"
date: 2010-05-09
forum: Desktop Environments
---

### Post by pepsifx357 on 2010-05-09
I just installed Avant-Window-Navigator, version 0.4.0-0ubuntu, today from synaptic and noticed that it sucked my CPU #2 resources dry...Has anyone else noticed this?  It gets so bad that it makes my computer lag.  I have an AMD Athlon64 X2 4800+ 939 with 2GB ram.  It doesn't seem to affect my first core at all.  But when you have the goodies running on AWN like themes and special effects the computer starts getting choppy.  I mean like Crysis running on a 486DX choppy.

---

### Post by moonbeam on 2010-05-09
Chances are that it's a specific applet.  Try disabling them selectively and see if that's the case.  If it a specific applet then please file a bug at [https://bugs.launchpad.net/awn-extras](https://bugs.launchpad.net/awn-extras) .  If it's not a specific applet then please file a bug at [https://bugs.launchpad.net/awn](https://bugs.launchpad.net/awn) and include the system's video card and video driver info.

---

### Post by pepsifx357 on 2010-05-10
Really, it just seems that AWN is a resource hog right now.  If I add a lot of applets, sure it bogs it down more, but even with no applets on it, just by using the auto hide feature, it uses 90% cpu.  Someone else posted a similar bug report, but they claimed it happened hours after they started the program.  Mine happens the instant it tries to execute ANY effects whatsoever, regardless of how many applets it has.

---

### Post by moonbeam on 2010-05-10
> **pepsifx357 said:**
> Really, it just seems that AWN is a resource hog right now.  If I add a lot of applets, sure it bogs it down more, but even with no applets on it, just by using the auto hide feature, it uses 90% cpu.  Someone else posted a similar bug report, but they claimed it happened hours after they started the program.  Mine happens the instant it tries to execute ANY effects whatsoever, regardless of how many applets it has.

Yeah, well we would probably consider what you describe as a bug :-)  Though if you're using 3d/spotlight then you _might_ get that type of behaviour.  My general feeling is that something is wrong and would suggest filing a bug.  I'm currently rung with 10 applets on a somewhat lower spec system and I'm not seeing this issue.

---

### Post by pepsifx357 on 2010-05-11
> **moonbeam said:**
> Yeah, well we would probably consider what you describe as a bug :-)  Though if you're using 3d/spotlight then you _might_ get that type of behaviour.  My general feeling is that something is wrong and would suggest filing a bug.  I'm currently rung with 10 applets on a somewhat lower spec system and I'm not seeing this issue.

Turns out that Ubuntu 10.04 LTS installed Nvidia driver 173 instead of the recommended driver.  Now everything runs very smooth.

---

### Post by atryus28 on 2010-05-11
If you are seeing high CPU usage for 3D effects then your video card is not working properly.  As you noted you changed your driver for your video card.  Your CPU should not really be affected at all by 3D applications (excluding games that is).

---

