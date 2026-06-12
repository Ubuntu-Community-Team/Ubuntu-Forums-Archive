---
title: "Graphics stopped working after compiz - nvidia - unity"
date: 2013-11-11
forum: Desktop Environments
---

### Post by jcllings on 2013-11-11
What happened: I had the nVidia drivers working fine with NVIDIA-Linux-x86_64-319.60.run  I started messing with compiz settings to get desktop cube working and suddenly I get only black screens or the dreaded "Low Resolution mode" loop. The wierd thing is that I can ssh -X to the machine and get access to graphics apps without any trouble.  Naturally I've defaulted the compiz settings. I'm not completely ignorant when it comes to Linux so I've done some poking around and tried a few tricks I know but haven't been able to get to a usable screen without shelling in from remote.  Another symptom to be reported is that the embedded intel graphics have the same issue. This is to say that I removed the nVidia card and tried it but got the same thing.  

VGA compatible controller        : NVIDIA Corporation GK107 [GeForce GT 640] (rev a1) (prog-if 00 [VGA controller])
Audio device        : NVIDIA Corporation GK107 HDMI Audio Controller (rev a1)

Help? :-/

---

### Post by jcllings on 2013-11-23
I uninstalled everything, yanked the card and set it on the shelf for a few weeks. In the mean time, I finished set up of synergy + AutoSsh tunnel. Many of the syptoms I had experienced earlier showed up again while I was doing this so that clued me in to the fact that I had been dealing with compound issues rather than just your typical crap when dealing with nVidia. Pulled the card off the shelf last night, plugged it in and viola! Spins like a top. Pretty sure there were some additional issues with the card but I apparently solved them without knowing I was, by doing things and adding packages that seemed like wisdom at the time.  I would post specifics but as you can imagine for a fix that happens over weeks, I can't remember them. :-/

Jim C.

---

