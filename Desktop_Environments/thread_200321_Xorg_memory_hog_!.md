---
title: "Xorg memory hog !"
date: 2006-06-20
forum: Desktop Environments
---

### Post by chetanthaker on 2006-06-20
Hey guys

I got me a nVidia GeForce 4 MX onboard graphics.. and my Xorg usually takes 100+MB of RAM leaving me HARDLY more than 6-9MB of RAM for other apps (got 512MB of RAM on my box)

Is there any work around for this ??

I'm posting my xorg.conf file here

If you guys can help me in ANY way....

CeeTee

---

### Post by ashrack on 2006-06-20
that is normAL! Xorg takes ~100MBs.
And if U have 512MB of ram than there must be at least 200MB free for apps.

---

### Post by chetanthaker on 2006-06-20
[QUOTE=ashrack]that is normAL! Xorg takes ~100MBs.
And if U have 512MB of ram than there must be at least 200MB free for apps.[/QUOTE]


So is that totally alright to run out of memory even with a 512MB RAM ???  :eek:

---

### Post by ashrack on 2006-06-20
It depends what apps U got open. 
But on my machine with 768RAM I almost never fill the RAM!

Check what else is eating away your memory, and if U re looking with GNOME-SYSTEM-MONITOR U should look under RESIDENT MEMORY and not VIRTUAL MEMORY

---

### Post by chetanthaker on 2006-06-20
[QUOTE=ashrack]It depends what apps U got open. 
But on my machine with 768RAM I almost never fill the RAM!

Check what else is eating away your memory, and if U re looking with GNOME-SYSTEM-MONITOR U should look under RESIDENT MEMORY and not VIRTUAL MEMORY[/QUOTE]


I'm running KDE... is there any app where I can find that ?? -- in KDE, all i can see is (when I press Ctrl + esc), only Vmsize (think its VIRTUAL MEMORY SIZE OCCUPIED)..

HELP ???

---

### Post by ashrack on 2006-06-20
I believe that U should run:
ksysguard

correct, VMSIZE stands for VIRTUAL MEMORY

and theres also the 'top' command U can run from terminal but I dont know how to use it

---

### Post by chetanthaker on 2006-06-20
[QUOTE=ashrack]I believe that U should run:
ksysguard

correct, VMSIZE stands for VIRTUAL MEMORY

and theres also the 'top' command U can run from terminal but I dont know how to use it[/QUOTE]


Cool, let me try ksysguard

The 'top' command works fine... but i usually prefer a GUI :)

---

