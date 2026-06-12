---
title: "How to enable visual effects and/or Unity"
date: 2011-04-29
forum: Desktop Environments
---

### Post by thany on 2011-04-29
I have just installed Ubuntu 11.04 on my laptop. Default installation, nothing special or fancy. It has a QuadroNVS 110M video chip, iirc. On Ubuntu 9, the visual effects were there to be enabled. When I enabled them it would ask if the proprietary drivers may be enabled. If I choose yes, they did and there were the visual effects that we all adore so much.

Now I'm trying Ubuntu 11.04, and the visual effects are nowhere to be found. The funny thing is, right after installation, the very first time the desktop was supposed to be loaded, I got a message telling my that my hardware is not capable of Unity.

So alright, let's just only have the visual effects then. But how/where? It seems as if all references to effects and to unity have been wiped clean, because I can't find it *anywhere*.

Also, in the "additional drivers" I have activated the "[recommended]" nvidia accelerated driver, but after that (and rebooting) it is "activated but not currently in use". I have no idea what that means.

Note that I'm a Windows user really. I have next to no knowledge about linux. So great if I have to do some clicks or some packages to be installed, not so great to muddle in config files. I have also already scouted google, and I did find the obvious links, and no solution.

---

### Post by Blasphemist on 2011-04-29
The nvidia issue is a deep one and I don't have nvidia so I haven't followed everything on that. Search for your version in these forums and follow a thread that looks promising. Sorry I can't help more on that.

You do need to install ccsm, compizconfigsettingsmanager from the software center. This gives you gui access to the visual settings.

---

### Post by pauljwells on 2011-04-29
For Natty, the default Nvidia driver is now the open-source Nouveau. This /can/ give excellent results but is still very new software. I run PPC, not x86 so I can't help you too much, but I can tell you you need to look for threads explaining how to remove Nouveau and install the nvidia proprietary driver. (You would have had this driver in 10.10). There are plenty of them!
For future ubuntus, the proprietary driver will not be good enough, but by then Nouveau should be mature enough...

---

### Post by thany on 2011-04-30
I installed ccsm, and it's got a load of settings. But they don't seem to do anything. It has an option to enable wobbly windows, for example, but it doesn't actually cause windows to become wobbly like they did in U9 on the very same laptop...

I think I'm still missing something.

---

### Post by Krytarik on 2011-04-30
If you just install CCSM, but Compiz isn't running, because of insufficient video support, everything you change in it won't, of course, come into effect.

Try reinstalling the proprietary Nvidia driver, check what version was activated for you, for "current" run:
```
sudo apt-get install --reinstall nvidia-current
```
Otherwise "nvidia-XXX".

---

