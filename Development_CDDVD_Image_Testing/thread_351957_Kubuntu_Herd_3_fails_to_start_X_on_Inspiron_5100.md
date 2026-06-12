---
title: "Kubuntu Herd 3 fails to start X on Inspiron 5100"
date: 2007-02-02
forum: Development CD/DVD Image Testing
---

### Post by NeoChaosX on 2007-02-02
Okay, just downloaded Herd 3, burned it to a CD and booted it on my Inspiron 5100. When I choose "Start or install Kubuntu", the boot is incredibly slow and X does not start, the process go to a terminal and not progressing past a message about fsck. 

Specs of the laptop:
2.6 GHz Pentium 4-M
768 MB RAM
ATI Mobility Radeon 7500
24x CD-RW drive

---

### Post by ButteBlues on 2007-02-02
> **NeoChaosX said:**
> Okay, just downloaded Herd 3, burned it to a CD and booted it on my Inspiron 5100. When I choose "Start or install Kubuntu", the boot is incredibly slow and X does not start, the process go to a terminal and not progressing past a message about fsck. 

Specs of the laptop:
2.6 GHz Pentium 4-M
768 MB RAM
ATI Mobility Radeon 7500
24x CD-RW drive
Same results on almost the same specs.

---

### Post by pochu on 2007-02-03
Could you search for a similar bug in [Lauchpad]("https://launchpad.net/ubuntu/+bugs"), and if it hasn't been reported, do it?

---

### Post by NeoChaosX on 2007-02-03
There doesn't seem to be a related bug on there, so I added a bug report about the behavior: [https://launchpad.net/ubuntu/+bug/83151](https://launchpad.net/ubuntu/+bug/83151)

---

### Post by NeoChaosX on 2007-02-06
Hey ButteBlues, what's the wireless card you use? Try starting the herd 3 CD without it inserted and see if it works.

---

### Post by jonnyburns on 2007-02-06
have u tried the above's idea? idk if that will work but i had similar problems with a compaq laptop with similar specs, and when i took out my pcmcia cards it all started to work... try it and see if it works?

---

### Post by Tictman on 2007-02-06
I have the exact problem with X crashing at boot. From the live Ubuntu cd. I'm running an Athlon 1800xp, MSI 300 mhz mb, connected to the net thru a linksys router, hard wired, not wireless.

---

### Post by NeoChaosX on 2007-02-06
Okay, just tried the February 6th daily build and this problem was fixed. My guess is that the linux-restricted-modules packages for Herd 3 was busted.

---

