---
title: "Wake from lock shows corruption / desktop"
date: 2014-01-27
forum: Desktop Environments
---

### Post by aberry5555 on 2014-01-27
Morning all.

I'm running ubuntu 13.10 on a Dell Latitude E6540 for work and am having a small problem with waking from suspend / unlocking the laptop.

This laptop has a hybrid AMD HD 8XXX series card and an intel HD on-chip gpu, I've set up the laptop with the fglrx drivers provided in the repository (the ones available from AMD directly just boot to a black screen):

fglrx:
  Installed: 2:13.101-0ubuntu3
  Candidate: 2:13.101-0ubuntu3
  Version table:
 *** 2:13.101-0ubuntu3 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/restricted amd64 Packages
        100 /var/lib/dpkg/status


I use the laptop in a dual monitor configuration with a Dell docking station, I have no other issues with undocking etc and the issue is apparent in both docked dual-monitor modes and in standalone single monitor mode.

When I either wake from suspend or go to unlock the computer after using ctrl+alt+l, I am presented either with a mostly black screen and some corruption here and there or (more worryingly) an offset view of both of my screens. Very, very occasionally I am presented with the correct password field and do not see any corruption.

I originally installed this machine with 12.04 LTS and used the FGLRX drivers from AMD's website, but ended up having the same issues. I have done some searching both here on the forums and via google, with a variety of different terms, and it looks to be a long-standing bug. Unfortunately, if that's the case and there's no fix or workaround, I'm going to be forced to choose a different distro as I can't risk displaying what was on my screen to anyone who wakes my computer (company policy and all that). It would be a great shame as I love Ubuntu, have only just got back in to the desktop version (I've been using the server version in the desktop's absence) and would love to continue using it as my day to day OS.

Any help on this would be greatly appreciated.

Thanks,

Alex

---

### Post by aberry5555 on 2014-01-30
Additionally just thought I'd say that I'm running with the intel chipset, rather than the amd drivers, I have the following package installed to ensure this works:

fglrx-pxpress:
  Installed: 0.4
  Candidate: 0.4
  Version table:
 *** 0.4 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
        100 /var/lib/dpkg/status

And can confirm I'm running on the intel chipset:

display: :0  screen: 0
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL version string: 3.0 Mesa 9.2.1

---

### Post by aberry5555 on 2014-01-30
I seem to have found the cause for the problem, when Clementine is open, either in the background or fullscreen, the issue is apparent. Once closed it's fine.

---

