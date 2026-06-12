---
title: "Nvidia 87.62 graphics freezes?"
date: 2006-06-02
forum: Gaming &amp; Leisure
---

### Post by Nexu on 2006-06-02
Just updated my Nvidia driver on Ubuntu. Restarted the system.

When i played ET and Warsow i noticed a horrible graphics lag that would freeze my screen for sometimes up to 2 seconds. But generally they last about 0.7 seconds (didn't measured it, but it feels like that).

Anyone else experienced this? :???: 

System Specs:
os[Linux 2.6.15-23-k7 i686] distro[Debian testing/unstable] cpu[1 x AMD Athlon(TM) XP2400+ @ 2.10GHz] mem[Physical : 756MB, 51.8% free] disk[Total : 410.48GB, 15.20% Free] video[nVidia Corporation NV40.2 [GeForce 6800 LE]] sound[EMU10K1 - SB Live [Unknown]1: CMI8738-MC6 - C-Media PCI CMI8738-MC6]

---

### Post by JoWilly on 2006-06-03
Many people are having freezes with the latest drivers... nvidia is aware of the many bug reports.

---

### Post by Nexu on 2006-06-03
Turns out my problem was caused by Beagle-daemon running on the background indexing data. I haven't noticed this problem before because ever since it was installed. Beagle hasn't been running yet due to the fact i haven't logged out and in yet, neither did i ran beagled. ](*,) 
After the updating the system with new Nvidia driver. I went for a reboot and after booting up and logging in, the Beagle-daemon kicked in for the first time thus causing noticable lag while playing games.

Sorry for the confusion. :-k 

PS = Hint for Beagle users and videogamers on Linux. You might wanna turn off Beagle-daemon while playing videogames. It might give you interruptions at very bad moments :mad: . Run from a terminal (**dont** have to be root!):
```
beagle-shutdown
``` To start it up again after you're done playing:
```
beagled
``` To test or Beagle is running:
```
beagle-status
``` Happy gaming everyone :KS

---

