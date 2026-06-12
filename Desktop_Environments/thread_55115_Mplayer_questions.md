---
title: "Mplayer questions"
date: 2005-08-07
forum: Desktop Environments
---

### Post by bob k on 2005-08-07
To make a long story short. I installed Hoary back in the initial stable release while still using warty in a different partation. I got Hoary to a stable working state and and installed all of the updates. I installed Mplayer from source withe the initial install (if I remember right at that time there was no umbutu support for hoary). I got mplayer somewhat working, I wasn't too worried about because I had mplayer working perfectly in warty, well the directory in the warty gets hosed and I am now having to get mplayer working in hoary.

I belive I have a version problem I am running Mplayer
1.0pre6-3.3.5 compliled form the mplayer website and mplayerplug-in 2.70-1unbuntu1 and I belive that is where my problem is. I finally got full screen working in firefox but there are a lot of options that aren't working.

My question is can I reinstall without uninstalling. It looks like the unstall script does nothing but remove the .conf files, I do have a mplayer.list in /var/.../dpkg
directory, but I saw there my be problems with option.

Any ideas or solutions?

TIA
Bob

---

### Post by bob k on 2005-08-08
well I have most of it figured out, removed and reinstalled mplayer, removed and reinstalled the codec libs, downloaded mplayerplug-in3.05 and recompiled and linked to gtk2 so I now have the controls. I have full screen for web streams thru the controls, but still won't open to a full screen, and if I loop the video it will revert to the little box in the upper left coner. I'm hoping this is a config problem.

There has to be a better way to do this!! There is little if any documentation on the plug-in, which forces you to make alot of assumptions on how the program works, and alot of hit and miss configuration changes.

Mplayer is a versital piece of software, and if I was still a software engineer with a video project I would link some of the functionalty in my code base, as it stands now I'm just surfing with mplayer as are 90% of the people that use it. Maybe we could have 2 or 3 packages pointing to the correct codecs and plugins for nube, intermeadiate, and pro.

just a thought

Bob

---

